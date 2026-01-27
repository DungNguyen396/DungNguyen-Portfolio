## Project 1: Behavioral Analysis and Customer Churn Prediction
### ❓ Business Questions 

This project aims to address the following key business questions related to customer churn:

1. **How significant is customer churn?**  
   Is churn a critical issue, and how severe is it across the customer base?

2. **Which customer behaviors are associated with churn?**  
   What patterns or actions tend to appear before a customer leaves?

3. **Can customer churn be predicted early?**  
   Is it possible to identify customers at risk of churn in advance to support early retention efforts?

4. **Can churn prevention be personalized at the individual level?**  
   Can insights be tailored to each customer to enable targeted and proactive interventions?<br><br>
   
### 🔑 Key Findings & Outcomes

1. **Overall churn rate and high-level patterns**  
   A descriptive statistical analysis was conducted to provide an overall view of the churn rate and its distribution across the customer base.

2. **Churn is driven by behavioral sequences, not single actions**  
   The analysis shows that churn rarely results from a single behavior. Instead, it is driven by a sequence of actions, typically involving one primary behavior supported by several contributing behaviors.

3. **Identification of behavioral breakpoints**  
   Critical behavioral breakpoints were identified, where the probability of churn increases sharply once certain thresholds are crossed.

4. **Predictive and explanatory modeling**  
   - A primary churn prediction model was developed to estimate the likelihood of churn.  
   - A secondary explanatory model was built to interpret and explain the main drivers of churn for each individual customer.

5. **Behavior-based customer segmentation**  
   Customers were segmented based on behavioral patterns, enabling clearer differentiation between churn-prone and loyal customer groups.

6. **Behavioral threshold monitoring framework**  
   A set of behavioral thresholds was defined to support ongoing monitoring and early warning signals for churn risk.<br><br>

### 📁 Analysis Documents

1. [EDA, behavioral analysis, and data preparation for model building](https://nbviewer.org/github/DungNguyen396/DungNguyen-portfolio/blob/main/project1-churn/eda.ipynb)
2. [Build models from Big Query, and segment customers based on behavior](./query.md)
4. [Explain the results from the Big Query and suggest actions](https://nbviewer.org/github/DungNguyen396/DungNguyen-portfolio/blob/main/project1-churn/explain.ipynb)
