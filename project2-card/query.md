``` sql
/* --================================================================================--
                                    COLLECTING DATA
--================================================================================--  */

CREATE OR REPLACE TABLE `dungportfolio.card.card_transaction` AS
WITH 
category_group AS (
  SELECT
    mcc_code
    ,description
    ,CASE
      WHEN mcc_code IN (5812, 5814, 5813, 5921, 7995, 7996, 7832, 7922, 7801, 7802) 
      THEN 'Food & Entertainment'

      WHEN mcc_code IN (5411, 5311, 5310, 5300, 5651, 5621, 5661, 5977, 5941, 5655, 5942, 5192, 5947, 5970, 5815, 5816, 5932, 5499) 
      THEN 'Shopping & Retail'

      WHEN mcc_code IN (4900, 4814, 4899, 4784, 9402, 6300, 8111, 8931, 7276, 4829, 7210, 7230, 7349, 7393, 1711, 7531, 7538, 7542, 7549) 
      THEN 'Bill & Services'

      WHEN mcc_code IN (4511, 4121, 4111, 4131, 3771, 3722, 4112, 7011, 4411, 4722, 4214, 3775) 
      THEN 'Travel & Transportation'

      WHEN mcc_code IN (3000, 3001, 3005, 3006, 3009, 3359, 3389, 3387, 3393, 3390, 3007, 3008, 3075, 3058, 3596, 3509) 
      THEN 'Materials & Manufacturing'

      WHEN mcc_code IN (8062, 5912, 8011, 8021, 8041, 8043, 8049, 8099) 
      THEN 'Healthcare & Medical'

      WHEN mcc_code IN (5732, 5045, 3780, 3684, 5712, 5719, 5722, 3174, 3640, 5733, 5261, 3504) 
      THEN 'Technology & Household'

      ELSE 'Miscellaneous'

    END AS category_group
  FROM `dungportfolio.card.mcc_code`
),

transaction_data AS (
  SELECT
    t.id AS trans_id
    ,DATE(t.date) AS trans_date
    ,t.client_id
    ,t.card_id

    ,SAFE_CAST(
        REGEXP_REPLACE(
                CAST(t.amount AS STRING), r'[^0-9.]', '') 
            AS FLOAT64) 
    AS amount

    ,mcc.description
    ,mcc.category_group
  FROM `dungportfolio.card.transaction` t
  LEFT JOIN category_group mcc ON t.mcc = mcc.mcc_code
),

card_data AS (
  SELECT 
    id AS card_id
    ,client_id
    ,card_brand
    ,card_type
    ,credit_limit AS card_limit
  FROM `dungportfolio.card.card_data` 
  WHERE card_type NOT LIKE '%(%' 
),

user_data AS (
  SELECT
    id AS client_id

    ,COALESCE(per_capita_income
                , SAFE_DIVIDE(yearly_income, 12)
            ) AS personal_income

    ,total_debt
    ,num_credit_cards AS num_total_card
  FROM `dungportfolio.card.user`

/* 
Use quartiles to observe income thresholds

WITH income_ranked AS (
    SELECT 
        client_id, 
        personal_income,
        NTILE(4) OVER (ORDER BY personal_income) AS income_quartile
    FROM (SELECT DISTINCT client_id, personal_income FROM `dungportfolio.card.card_transaction`)
)
SELECT 
    income_quartile,
    MIN(personal_income) AS min_in_group,
    MAX(personal_income) AS max_in_group,
    COUNT(*) AS total_clients
FROM income_ranked
GROUP BY 1
ORDER BY 1;
*/
)

SELECT
  t.trans_id
  ,t.client_id
  ,t.card_id
  ,u.personal_income
  ,CASE 
        WHEN u.personal_income < 17000 THEN 'Low (<17k)'
        WHEN u.personal_income <= 26000 THEN 'Medium (17k-26k)'
        ELSE 'High (>26k)'
    END AS income_segment
  ,SAFE_DIVIDE(u.total_debt, u.personal_income) AS dti_ratio
  ,t.trans_date
  ,t.amount
  ,c.card_type
  ,c.card_limit
  ,u.num_total_card
  ,u.total_debt
  ,t.description
  ,t.category_group
FROM transaction_data t
INNER JOIN card_data c ON t.card_id = c.card_id
INNER JOIN user_data u ON t.client_id = u.client_id
WHERE personal_income > 0
      AND t.amount > 0;



/* --================================================================================--
                                DATA ANALYSIS
--================================================================================--  */

--1/ OVER VIEW ------------------------
SELECT 
  EXTRACT(YEAR FROM trans_date) AS trans_year
  ,card_type
  ,COUNT(DISTINCT client_id) AS total_clients
  ,COUNT(DISTINCT card_id) AS total_active_cards
  ,COUNT(trans_id) AS total_transactions
  ,ROUND(SUM(amount), 2) AS total_volume
  ,ROUND(SUM(amount) / 
            NULLIF(COUNT(trans_id), 0)
            , 2) 
            AS ticket_size
  ,ROUND(SUM(amount) / 
        NULLIF(COUNT(DISTINCT client_id), 0)
        , 2) 
        AS avg_spending_per_client
FROM `dungportfolio.card.card_transaction`
GROUP BY 1, 2
ORDER BY 1, 2;

--2/ CATEGORY CONTRIBUTION ------------------------
WITH filtered_data AS (
  SELECT *
  FROM `dungportfolio.card.card_transaction`
)
SELECT 
  category_group,
  COUNT(trans_id) AS total_trans,
  ROUND(SUM(amount), 2) AS total_amount,
  ROUND(SUM(amount) * 100 / 
        SUM(SUM(amount)) OVER(), 2) 
        AS pct_contribution
FROM filtered_data
GROUP BY 1
ORDER BY total_amount DESC;

--3/ MONEY FLOW ------------------------
SELECT 
  category_group,

  ROUND(SUM(CASE 
                WHEN EXTRACT(YEAR FROM trans_date) = 2018 
                THEN amount ELSE 0 END), 2) 
                AS amount_2018,

  ROUND(SUM(CASE 
                WHEN EXTRACT(YEAR FROM trans_date) = 2019 
                THEN amount ELSE 0 END), 2) 
                AS amount_2019,

  ROUND(
    (SUM(CASE 
             WHEN EXTRACT(YEAR FROM trans_date) = 2019 
             THEN amount ELSE 0 END) / 10) / 
    NULLIF(SUM(CASE 
                    WHEN EXTRACT(YEAR FROM trans_date) = 2018 
                    THEN amount ELSE 0 END) / 12, 0) - 1 
       ,4) * 100 
       AS monthly_avg_growth_pct
FROM `dungportfolio.card.card_transaction`
GROUP BY 1
ORDER BY amount_2018 DESC;

--4/ TOP CATEGORY ------------------------
WITH top_categories AS (
  SELECT category_group
  FROM `dungportfolio.card.card_transaction`
  GROUP BY 1
  ORDER BY SUM(amount) DESC
  LIMIT 3
),

segmented_data AS (
  SELECT 
    category_group
    ,income_segment
    .ROUND(SUM(amount), 2) AS total_amount
    ,COUNT(DISTINCT client_id) AS total_users
    ,ROUND(SUM(amount) / 
            NULLIF(COUNT(DISTINCT client_id), 0), 2) 
            AS spending_per_user

    ,ROUND(SUM(CASE 
                  WHEN card_type = 'Credit' 
                  THEN amount ELSE 0 END) * 100.0 / 
           NULLIF(SUM(amount), 0)
        , 2) 
        AS credit_spending_pct

    ,ROUND(SUM(CASE
                  WHEN card_type = 'Debit' 
                  THEN amount ELSE 0 END) * 100.0 /
            NULLIF(SUM(amount), 0)
        , 2) 
        AS debit_spending_pct
  FROM `dungportfolio.card.card_transaction`
  WHERE category_group IN (SELECT category_group FROM top_categories)
  GROUP BY 1, 2
)

SELECT * FROM segmented_data
ORDER BY category_group
        ,total_amount DESC;

--5/ DTI CONTRIBUTION ------------------------
WITH client_health AS (
  SELECT 
    client_id
    ,income_segment
    ,MAX(dti_ratio) AS dti_ratio
    ,MAX(total_debt) AS total_debt
  FROM `dungportfolio.card.card_transaction`
  GROUP BY 1, 2
)

SELECT 
  income_segment
  ,ROUND(AVG(dti_ratio), 2) AS avg_monthly_dti

  ,ROUND(COUNTIF(dti_ratio > 5.0) * 100.0 / 
        NULLIF(COUNT(client_id), 0)
    , 2) 
    AS high_leverage_client_pct

  ,ROUND(AVG(total_debt), 0) AS avg_total_debt
  ,COUNT(client_id) AS total_clients
FROM client_health
GROUP BY 1
ORDER BY 1;

--6/ DTI > 5 SCANING ------------------------
WITH high_leverage_users AS (
  SELECT 
    DISTINCT client_id
    ,income_segment
    ,dti_ratio
    ,total_debt
  FROM `dungportfolio.card.card_transaction`
  WHERE dti_ratio > 5.0
)

SELECT 
  t.income_segment
  ,t.category_group
  ,t.card_type
  ,ROUND(SUM(t.amount), 0) AS total_spending
  ,ROUND(AVG(t.amount), 2) AS avg_ticket_size
  ,COUNT(DISTINCT t.client_id) AS risk_user_count
FROM `dungportfolio.card.card_transaction` t
INNER JOIN high_leverage_users h ON t.client_id = h.client_id
GROUP BY 1, 2, 3
ORDER BY total_spending DESC;

--7/ CORHOT COMPARISION ------------------------
WITH segment_metrics AS (
  SELECT 
    income_segment
    ,SUM(CASE 
            WHEN EXTRACT(YEAR FROM trans_date) = 2019 
            THEN amount ELSE 0 END) 
            AS volume_2019

    ,SAFE_DIVIDE(
                SUM(CASE 
                        WHEN EXTRACT(YEAR FROM trans_date) = 2019 
                        THEN amount ELSE 0 END) - 
                SUM(CASE 
                        WHEN EXTRACT(YEAR FROM trans_date) = 2018 
                        THEN amount ELSE 0 END)
                ,NULLIF(SUM(CASE 
                                WHEN EXTRACT(YEAR FROM trans_date) = 2018 
                                THEN amount ELSE 0 END), 0)
                ) * 100 
                AS growth_pct

    ,AVG(dti_ratio) AS avg_dti

    ,SAFE_DIVIDE(
                SUM(CASE 
                        WHEN card_type = 'Credit' 
                        THEN amount ELSE 0 END)
                ,NULLIF(SUM(amount), 0)
                ) AS credit_ratio
  FROM `dungportfolio.card.card_transaction`
  WHERE EXTRACT(MONTH FROM trans_date) <= 10 
            OR EXTRACT(YEAR FROM trans_date) = 2018
  GROUP BY 1
)

SELECT 
  income_segment
  ,ROUND(volume_2019, 0) AS revenue
  ,ROUND(growth_pct, 2) AS growth_yoy
  ,ROUND(avg_dti, 2) AS debt_level
  ,ROUND(credit_ratio * 100, 2) AS leverage_pct
FROM segment_metrics
ORDER BY revenue DESC;
```
