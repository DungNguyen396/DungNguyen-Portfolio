```sql
--=============== SECTION 1: PREPARE SPLIT DATA ===============--

-- 1/ BOOSTED TREE DATA (RAW, NO SCALE)
CREATE OR REPLACE TABLE `dungportfolio.RawData.customer_churn_split` AS
SELECT 
    *	
    ,IF(RAND() < 0.8, 'TRAIN', 'TEST') AS data_split
FROM `dungportfolio.RawData.ecommerce_cust_data`;


-- 2/ LOGISTIC DATA (SCALED)
CREATE OR REPLACE TABLE `dungportfolio.RawData.customer_churn_split_logistic` AS
SELECT
  *,
  IF(RAND() < 0.8, 'TRAIN', 'TEST') AS data_split
FROM `dungportfolio.RawData.scale_data`;


--------------------------------------------------------------------------------------------------------
--=============== SECTION 2: BOOSTED TREE MODEL (MAIN)) ===============--

-- 1/ Create model
CREATE OR REPLACE MODEL `dungportfolio.RawData.churn_boosted_tree`
OPTIONS (
  model_type = 'boosted_tree_classifier',
  input_label_cols = ['Churned'],
  max_iterations = 50,
  max_tree_depth = 5,
  subsample = 0.8,
  enable_global_explain = TRUE
) AS
    SELECT 
        * except(customer_id, data_split)
    FROM `dungportfolio.RawData.customer_churn_split`
    WHERE data_split = 'TRAIN';


-- 2/ Evaluate model
SELECT *
FROM ML.EVALUATE(
    MODEL `dungportfolio.RawData.churn_boosted_tree`,
    (
        SELECT 
            * 
        FROM `dungportfolio.RawData.customer_churn_split`
        WHERE data_split = 'TEST'
    )
);

-- 3/ Global explain
SELECT *
FROM ML.GLOBAL_EXPLAIN(
    MODEL `dungportfolio.RawData.churn_boosted_tree`,
    STRUCT(30 AS top_k_features)
);

-- 4/ Rebuild model (except weak attribution features)
CREATE OR REPLACE MODEL `dungportfolio.RawData.churn_boosted_tree_v2`
OPTIONS (
  model_type = 'boosted_tree_classifier',
  input_label_cols = ['Churned'],
  max_iterations = 50,
  max_tree_depth = 5,
  subsample = 0.8,
  enable_global_explain = TRUE
) AS
    SELECT 
        * except(
                  customer_id
                  ,data_split
                  ,credit_balance
                  ,signup_quarter
                  ,city
                  ,country
                  ,gender 
                  ,membership_years
                  ,payment_method_diversity
                  )
    FROM `dungportfolio.RawData.customer_churn_split`
    WHERE data_split = 'TRAIN';

SELECT *
FROM ML.EVALUATE(
    MODEL `dungportfolio.RawData.churn_boosted_tree`,
    (
        SELECT 
            * 
        FROM `dungportfolio.RawData.customer_churn_split`
        WHERE data_split = 'TEST'
    )
);

-- 5/ Predict churn probability (threshold = 0.3)
CREATE OR REPLACE TABLE `dungportfolio.RawData.churn_predict_tree` AS
SELECT
    customer_id
    ,ROUND(probs.prob,2) AS churn_probability
FROM ML.PREDICT(
        MODEL `dungportfolio.RawData.churn_boosted_tree_v2`,
        (SELECT * FROM `dungportfolio.RawData.ecommerce_cust_data`)
     ) AS t,
UNNEST(t.predicted_Churned_probs) AS probs
WHERE probs.label = 1 
      AND probs.prob >= 0.3;


--------------------------------------------------------------------------------------------------------
--=============== SECTION 3: LOGISTIC MODEL (BASELINE - EXPLAIN)) ===============--

---- 1/ Create logistic model
CREATE OR REPLACE MODEL `dungportfolio.RawData.churn_logistic_model`
OPTIONS (
  model_type = 'logistic_reg',
  input_label_cols = ['churned'],
  auto_class_weights = TRUE,
  standardize_features = FALSE
) AS
SELECT
   * except(customer_id, data_split)
FROM `dungportfolio.RawData.customer_churn_split_logistic`
WHERE data_split = 'TRAIN';

---- 2/ Evaluate logistic
SELECT
  *
FROM
  ML.EVALUATE(
    MODEL `dungportfolio.RawData.churn_logistic_model`,
    (
      SELECT
         * except(customer_id, data_split)
      FROM `dungportfolio.RawData.customer_churn_split_logistic`
      WHERE data_split = 'TEST'
    )
  );

---- 3/ Logistic explain 
SELECT
  processed_input
  ,weight
  ,EXP(weight) AS odds_ratio
FROM
  ML.WEIGHTS(MODEL `dungportfolio.RawData.churn_logistic_model`)
ORDER BY ABS(weight) DESC;


--------------------------------------------------------------------------------------------------------
--=============== SECTION 4: LOGISTIC MODEL (BASELINE - EXPLAIN)) ===============--

CREATE OR REPLACE TABLE `dungportfolio.RawData.customer_churn_rootcause` AS
WITH churn_tree AS (
SELECT
    customer_id
    ,ROUND(probs.prob,2) AS churn_probability
FROM ML.PREDICT(
        MODEL `dungportfolio.RawData.churn_boosted_tree_v2`,
        (SELECT * FROM `dungportfolio.RawData.ecommerce_cust_data`)
     ) t,
     UNNEST(t.predicted_Churned_probs) AS probs
WHERE probs.label = 1
  AND probs.prob >= 0.21
),

logistic_explain AS (
SELECT
    e.customer_id
    ,f.feature
    ,f.attribution
FROM ML.EXPLAIN_PREDICT(
    MODEL `dungportfolio.RawData.churn_logistic_model`,
    (
      SELECT
        * EXCEPT(data_split)
      FROM `dungportfolio.RawData.customer_churn_split_logistic`
    )
) e
CROSS JOIN UNNEST(e.top_feature_attributions) AS f
),

ranked_drivers AS (
SELECT
    customer_id
    ,feature
    ,attribution
    ,ROW_NUMBER() OVER (
        PARTITION BY customer_id
        ORDER BY attribution DESC
     ) AS rn
FROM logistic_explain
WHERE attribution > 0
),

behavior_segment AS (
SELECT
    t.customer_id
    ,churn_probability
    ,STRING_AGG(d.feature, ' + ') AS churn_drivers
FROM churn_tree t
LEFT JOIN ranked_drivers d
    ON t.customer_id = d.customer_id
   AND d.rn <= 3
GROUP BY
    t.customer_id
    ,t.churn_probability
ORDER BY churn_probability DESC
)

SELECT 
    *
    ,CASE
        WHEN churn_drivers IS NULL
            THEN 'silent_risk customer'

        WHEN churn_drivers LIKE 'Customer_Service_Calls%'
            THEN 'high_complain customer'

        WHEN churn_drivers LIKE '%Cart_Abandonment_Rate + Customer_Service_Calls%'
            THEN 'high_cart_abandonment_rate & medium_complain customer'

        WHEN churn_drivers LIKE 'Total_Purchases + Customer_Service_Calls%'
            THEN 'low_purchases & medium_complain customer'

        WHEN churn_drivers LIKE '%+ Customer_Service_Calls +%'
            THEN 'low_engagement & medium_complain customer'

        ELSE 'low_engagement customer'
    END AS churn_cause

FROM behavior_segment;


--Check the distribution among churn_cause
SELECT
    r.churn_cause
    ,COUNT(DISTINCT r.customer_id) AS customer_count
    ,ROUND(
        COUNT(DISTINCT r.customer_id)
        / SUM(COUNT(DISTINCT r.customer_id)) OVER() * 100
    ,2) AS pct_customers

    ,ROUND(SUM(d.average_order_value * d.total_purchases),2) AS total_revenue

    ,ROUND(
        SUM(d.average_order_value * d.total_purchases)
        / SUM(SUM(d.average_order_value * d.total_purchases)) OVER() * 100
    ,2) AS pct_revenue

FROM `dungportfolio.RawData.customer_churn_rootcause` r
JOIN `dungportfolio.RawData.ecommerce_cust_data` d
  ON r.customer_id = d.customer_id

GROUP BY r.churn_cause
ORDER BY total_revenue DESC;


--Breakout-reference 
CREATE OR REPLACE TABLE `dungportfolio.RawData.breakout_reference` AS
SELECT
    'Customer_Service_Calls' AS feature_name,
    '≤ 5 calls' AS safe_zone,
    '> 5 calls' AS risk_zone,
    'Customers calling support more than 5 times show sharp churn increase' AS business_meaning

UNION ALL
SELECT
    'Login_Frequency',
    '≥ 6 logins',
    '< 6 logins',
    'Low login frequency signals disengagement'

UNION ALL
SELECT
    'Cart_Abandonment_Rate',
    '≤ 68%',
    '> 68%',
    'High cart abandonment indicates purchase friction'

UNION ALL
SELECT
    'Session_Duration_Avg',
    '≥ 20 minutes',
    '< 20 minutes',
    'Short sessions reflect weak product engagement'

UNION ALL
SELECT
    'Pages_Per_Session',
    '≥ 6 pages',
    '< 6 pages',
    'Low page views suggest shallow browsing behavior';


```
