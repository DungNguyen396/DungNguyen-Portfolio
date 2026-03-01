<div align="center">
  <h1 style="color: #455a64; border-bottom: none; margin-bottom: 10px; font-size: 30px;">CHURN PROBABILITY MODELING FOR CUSTOMER SEGMENTATION</h1>
  <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Category-Risk%20Analytics-455a64?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Tools-Python%20%26%20BigQuery-607d8b?style=for-the-badge" />
</div>

<br>

<div style="background-color: #f5f7f8; padding: 30px; border-radius: 15px; width: 100%;">
  <div style="background-color: #ffffff; padding: 30px; border-radius: 12px; border-left: 10px solid #455a64; box-shadow: 0 4px 15px rgba(0,0,0,0.05)";>
    <h2 style="color: #455a64; margin-top: 0; border-bottom: none;">📌 Project Background</h2>
    <p style="color: #2c3e50; line-height: 1.8; font-size: 16px; text-align: justify; margin-bottom: 0;">
      This project was initiated following a request from the internal Data Analysis team to develop a robust predictive model for customer churn. The primary objective was to move beyond retrospective reporting and establish an early-warning system for the strategic departments. By identifying high-risk behavioral patterns before a customer actually leaves, the organization can proactively deploy retention campaigns. This analysis serves as the foundation for data-driven interventions aimed at stabilizing the customer base and protecting long-term revenue.
    </p>
  </div>
</div>

<br>

<h2 style="color: #455a64; padding-left: 10px; border-bottom: none;">Exposing the Underlying Drivers ❓</h2>
<p style="padding-left: 10px; color: #7f8c8d; font-style: italic; margin-bottom: 20px;">Shifting from descriptive statistics to proactive churn management:</p>

<div style="width: 100%; display: flex; flex-direction: column; gap: 20px;">
  <div style="display: flex; align-items: center; background: #ffffff; padding: 20px; border-radius: 12px; border: 1px solid #dee2e6; box-shadow: 0 8px 15px rgba(69, 90, 100, 0.08); position: relative; overflow: hidden;">
    <div style="font-size: 30px; margin-right: 20px;"></div>
    <div style="flex: 1; z-index: 1;">
      <h4 style="color: #455a64; margin: 0; font-size: 16px; text-transform: uppercase;">Commercial Impact of Churn</h4>
      <p style="color: #444; margin: 5px 0 0 0; font-size: 15px;">Beyond the rate itself, what is the actual severity of churn in terms of revenue loss and market share erosion?</p>
    </div>
    <div style="color: #eceff1; font-size: 55px; font-weight: 900; position: absolute; right: 10px; bottom: -12px; z-index: 0;">01</div>
  </div>
  <div style="display: flex; align-items: center; background: #ffffff; padding: 20px; border-radius: 12px; border: 1px solid #dee2e6; box-shadow: 0 8px 15px rgba(69, 90, 100, 0.1); position: relative; overflow: hidden;">
    <div style="font-size: 30px; margin-right: 20px;"></div>
    <div style="flex: 1; z-index: 1;">
      <h4 style="color: #455a64; margin: 0; font-size: 16px; text-transform: uppercase;">Behavioral Breakpoints</h4>
      <p style="color: #444; margin: 5px 0 0 0; font-size: 15px;">What specific sequences of actions trigger a transition from a "Loyal" to an "At-Risk" state?</p>
    </div>
    <div style="color: #cfd8dc; font-size: 55px; font-weight: 900; position: absolute; right: 10px; bottom: -12px; z-index: 0;">02</div>
  </div>
  <div style="display: flex; align-items: center; background: #ffffff; padding: 20px; border-radius: 12px; border: 1px solid #dee2e6; box-shadow: 0 8px 15px rgba(69, 90, 100, 0.12); position: relative; overflow: hidden;">
    <div style="font-size: 30px; margin-right: 20px;"></div>
    <div style="flex: 1; z-index: 1;">
      <h4 style="color: #455a64; margin: 0; font-size: 16px; text-transform: uppercase;">Early Warning Systems</h4>
      <p style="color: #444; margin: 5px 0 0 0; font-size: 15px;">How can we identify the "point of no return" to intervene effectively before the final transaction occurs?</p>
    </div>
    <div style="color: #b0bec5; font-size: 55px; font-weight: 900; position: absolute; right: 10px; bottom: -12px; z-index: 0;">03</div>
  </div>
  <div style="display: flex; align-items: center; background: #ffffff; padding: 20px; border-radius: 12px; border: 1px solid #dee2e6; box-shadow: 0 10px 18px rgba(69, 90, 100, 0.15); position: relative; overflow: hidden;">
    <div style="font-size: 30px; margin-right: 20px;"></div>
    <div style="flex: 1; z-index: 1;">
      <h4 style="color: #455a64; margin: 0; font-size: 16px; text-transform: uppercase;">Strategic Retention</h4>
      <p style="color: #444; margin: 5px 0 0 0; font-size: 15px;">How can churn prevention be personalized at scale to ensure costs align with lifetime value?</p>
    </div>
    <div style="color: #90a4ae; font-size: 55px; font-weight: 900; position: absolute; right: 10px; bottom: -12px; z-index: 0;">04</div>
  </div>
</div>

<br>

<div style="background-color: #f5f7f8; padding: 30px; border-radius: 15px; width: 100%;">
  <h2 style="color: #455a64; margin-top: 0; border-bottom: none;">🔑 Key Findings & Outcomes</h2>
  <div style="background-color: #ffffff; padding: 18px; border-radius: 10px; border-left: 10px solid #cfd8dc; margin-bottom: 20px; box-shadow: 0 8px 20px rgba(207, 216, 220, 0.5);">
    <b style="color: #455a64; font-size: 16px;">1. High-Level Churn Impact Visualization</b>
    <p style="margin-top: 5px; color: #2c3e50;">Provided a comprehensive view of churn severity, mapping its direct correlation to portfolio value decay.</p>
  </div>
  <div style="background-color: #ffffff; padding: 18px; border-radius: 10px; border-left: 10px solid #90a4ae; margin-bottom: 20px; box-shadow: 0 8px 20px rgba(144, 164, 174, 0.5);">
    <b style="color: #455a64; font-size: 16px;">2. Sequential Churn Drivers</b>
    <p style="margin-top: 5px; color: #2c3e50;">Proved that churn is driven by behavioral sequences typically involving a primary negative behavior reinforced by secondary triggers.</p>
  </div>
  <div style="background-color: #ffffff; padding: 18px; border-radius: 10px; border-left: 10px solid #607d8b; margin-bottom: 20px; box-shadow: 0 8px 20px rgba(96, 125, 139, 0.5);">
    <b style="color: #455a64; font-size: 16px;">3. Threshold Identification</b>
    <p style="margin-top: 5px; color: #2c3e50;">Identified critical behavioral thresholds where churn probability increases sharply, allowing for data-driven monitoring.</p>
  </div>
  <div style="background-color: #ffffff; padding: 18px; border-radius: 10px; border-left: 10px solid #546e7a; margin-bottom: 20px; box-shadow: 0 8px 20px rgba(84, 110, 122, 0.5);">
    <b style="color: #455a64; font-size: 16px;">4. Predictive & Explanatory Modeling</b>
    <p style="margin-top: 5px; color: #2c3e50;">Developed a primary prediction model for likelihood estimation and a secondary model to interpret individual drivers for action.</p>
  </div>
  <div style="background-color: #ffffff; padding: 18px; border-radius: 10px; border-left: 10px solid #455a64; box-shadow: 0 8px 25px rgba(69, 90, 100, 0.3);">
    <b style="color: #455a64; font-size: 16px;">5. Behavior-Based Framework</b>
    <p style="margin-top: 5px; color: #2c3e50;">Established a monitoring framework using defined behavioral thresholds to support ongoing, proactive retention efforts.</p>
  </div>
</div>

<br>

<h2 style="color: #455a64; padding-left: 10px; border-bottom: none;">📁 Analysis Documents</h2>
<p style="padding-left: 10px; color: #7f8c8d; font-style: italic; margin-bottom: 15px;">Technical implementation and code:</p>

<div style="display: flex; gap: 15px; justify-content: space-between;">
  <a href="https://nbviewer.org/github/DungNguyen396/DungNguyen-portfolio/blob/main/project1-churn/eda.ipynb" style="flex: 1; text-decoration: none;">
    <div style="background-color: #455a64; border-radius: 10px; padding: 18px 10px; text-align: center; height: 100%; box-shadow: 0 6px 15px rgba(69, 90, 100, 0.3);">
      <b style="color: #ffffff; font-size: 11px; text-transform: uppercase; display: block; letter-spacing: 1px;">EDA & PREP</b>
    </div>
  </a>
  <a href="./query.md" style="flex: 1; text-decoration: none;">
    <div style="background-color: #607d8b; border-radius: 10px; padding: 18px 10px; text-align: center; height: 100%; box-shadow: 0 6px 15px rgba(96, 125, 139, 0.3);">
      <b style="color: #ffffff; font-size: 11px; text-transform: uppercase; display: block; letter-spacing: 1px;">BIGQUERY ML</b>
    </div>
  </a>
  <a href="https://nbviewer.org/github/DungNguyen396/DungNguyen-portfolio/blob/main/project1-churn/explain.ipynb" style="flex: 1; text-decoration: none;">
    <div style="background-color: #90a4ae; border-radius: 10px; padding: 18px 10px; text-align: center; height: 100%; box-shadow: 0 6px 15px rgba(144, 164, 174, 0.3);">
      <b style="color: #ffffff; font-size: 11px; text-transform: uppercase; display: block; letter-spacing: 1px;">STRATEGY</b>
    </div>
  </a>
</div>

<br><br>

<div align="center" style="padding-bottom: 50px;">
  <hr style="opacity: 0.1;">
  <a href="https://dungnguyen396.github.io/DungNguyen-Portfolio/" style="background-color: #455a64; color: white; padding: 14px 30px; text-decoration: none; border-radius: 10px; font-weight: bold; box-shadow: 0 4px 15px rgba(69, 90, 100, 0.2);">← BACK TO MAIN PORTFOLIO</a>
</div>
