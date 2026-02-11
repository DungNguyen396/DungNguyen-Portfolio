## Project 1: Behavioral Analysis and Customer Churn Prediction
**Project Background:** This project was initiated following a request from the internal Data Analysis team to develop a robust predictive model for customer churn. The primary objective was to move beyond retrospective reporting and establish an early-warning system for the strategic departments. By identifying high-risk behavioral patterns before a customer actually leaves, the organization can proactively deploy retention campaigns. This analysis serves as the foundation for data-driven interventions aimed at stabilizing the customer base and protecting long-term revenue.

### ❓ Business Questions
This project shifts from descriptive statistics to proactive churn management:

**1. Commercial Impact of Churn:**<br>

Beyond the rate itself, what is the actual severity of churn in terms of revenue loss and market share erosion?

**2. Behavioral Breakpoints:**<br>

What specific sequences of actions rather than isolated incidents trigger a transition from a "Loyal" to an "At-Risk" state?

**3. Early Warning Systems:** <br>

How can we identify the "point of no return" to intervene effectively before the final transaction occurs?

**4. Strategic Retention:** <br>

How can churn prevention be personalized at scale to ensure intervention costs do not exceed the customer's lifetime value?<br><br>
   

### 🔑 Key Findings & Outcomes
**1. High-Level Churn Impact Visualization**

   Provided a comprehensive view of churn severity, mapping its direct correlation to portfolio value decay.

**2. Sequential Churn Drivers**

   Proved that churn is driven by behavioral sequences rather than single actions, typically involving a primary negative behavior              reinforced by secondary triggers.

**3. Threshold Identification**

   Identified critical behavioral thresholds where churn probability increases sharply, allowing for data-driven monitoring.

**4. Predictive & Explanatory Modeling**

   Developed a primary prediction model to estimate churn likelihood and a secondary model to interpret individual churn drivers for            personalized action.

**5. Behavior-Based Framework**

   Established a monitoring framework using defined behavioral thresholds to support ongoing, proactive retention efforts.<br><br>

### 📁 Analysis Documents

1. [EDA, Behavioral Analysis, and Data Preparation](https://nbviewer.org/github/DungNguyen396/DungNguyen-portfolio/blob/main/project1-churn/eda.ipynb)
2. [BigQuery Model Building & Behavioral Segmentation](./query.md)
4. [Insight Interpretation and Strategic Action Plan](https://nbviewer.org/github/DungNguyen396/DungNguyen-portfolio/blob/main/project1-churn/explain.ipynb)
