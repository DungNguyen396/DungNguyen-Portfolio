<div align="center">
  <h1 style="color: #1a3a5f; border-bottom: none; margin-bottom: 10px; font-size: 30px;">PROJECT 1: BEHAVIORAL ANALYSIS & CUSTOMER CHURN PREDICTION</h1>
  <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Category-Risk%20Analytics-1a3a5f?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Tools-Python%20%26%20BigQuery-4682B4?style=for-the-badge" />
</div>

<br>

<div style="background-color: #e9ecef; padding: 30px; border-radius: 15px; width: 100%;">
  <div style="background-color: #ffffff; padding: 30px; border-radius: 12px; border-left: 10px solid #1a3a5f; box-shadow: 0 4px 15px rgba(0,0,0,0.05);">
    <h2 style="color: #1a3a5f; margin-top: 0; border-bottom: none;">📌 Project Background</h2>
    <p style="color: #2c3e50; line-height: 1.8; font-size: 16px; text-align: justify; margin-bottom: 0;">
      This project was initiated following a request from the internal Data Analysis team to develop a robust predictive model for customer churn. The primary objective was to move beyond retrospective reporting and establish an early-warning system for the strategic departments. By identifying high-risk behavioral patterns before a customer actually leaves, the organization can proactively deploy retention campaigns. This analysis serves as the foundation for data-driven interventions aimed at stabilizing the customer base and protecting long-term revenue.
    </p>
  </div>
</div>

<br>

<h2 style="color: #1a3a5f; padding-left: 10px; border-bottom: none;">❓ Business Questions</h2>
<p style="padding-left: 10px; color: #7f8c8d; font-style: italic; margin-bottom: 20px;">Shifting from descriptive statistics to proactive churn management:</p>

<div style="width: 100%; display: flex; flex-direction: column; gap: 15px;">
  <div style="display: flex; align-items: center; background: #ffffff; padding: 18px; border-radius: 12px; border: 1px solid #dee2e6; box-shadow: 0 6px 15px rgba(244, 246, 247, 0.9); position: relative; overflow: hidden;">
    <div style="font-size: 28px; margin-right: 18px;">📊</div>
    <div style="flex: 1; z-index: 1;">
      <h4 style="color: #1a3a5f; margin: 0; font-size: 15px; text-transform: uppercase;">Commercial Impact</h4>
      <p style="color: #444; margin: 3px 0 0 0; font-size: 14px;">What is the actual severity of churn in terms of revenue loss and market share erosion?</p>
    </div>
    <div style="color: #f4f6f7; font-size: 50px; font-weight: 900; position: absolute; right: 8px; bottom: -10px; z-index: 0;">01</div>
  </div>
  <div style="display: flex; align-items: center; background: #ffffff; padding: 18px; border-radius: 12px; border: 1px solid #dee2e6; box-shadow: 0 6px 15px rgba(213, 216, 220, 0.7); position: relative; overflow: hidden;">
    <div style="font-size: 28px; margin-right: 18px;">🧠</div>
    <div style="flex: 1; z-index: 1;">
      <h4 style="color: #1a3a5f; margin: 0; font-size: 15px; text-transform: uppercase;">Behavioral Breakpoints</h4>
      <p style="color: #444; margin: 3px 0 0 0; font-size: 14px;">What specific sequences of actions trigger a transition to an "At-Risk" state?</p>
    </div>
    <div style="color: #d5d8dc; font-size: 50px; font-weight: 900; position: absolute; right: 8px; bottom: -10px; z-index: 0;">02</div>
  </div>
  <div style="display: flex; align-items: center; background: #ffffff; padding: 18px; border-radius: 12px; border: 1px solid #dee2e6; box-shadow: 0 6px 15px rgba(171, 178, 185, 0.5); position: relative; overflow: hidden;">
    <div style="font-size: 28px; margin-right: 18px;">🛰️</div>
    <div style="flex: 1; z-index: 1;">
      <h4 style="color: #1a3a5f; margin: 0; font-size: 15px; text-transform: uppercase;">Early Warning Systems</h4>
      <p style="color: #444; margin: 3px 0 0 0; font-size: 14px;">How can we identify the "point of no return" before the final transaction?</p>
    </div>
    <div style="color: #abb2b9; font-size: 50px; font-weight: 900; position: absolute; right: 8px; bottom: -10px; z-index: 0;">03</div>
  </div>
  <div style="display: flex; align-items: center; background: #ffffff; padding: 18px; border-radius: 12px; border: 1px solid #dee2e6; box-shadow: 0 8px 18px rgba(86, 101, 115, 0.3); position: relative; overflow: hidden;">
    <div style="font-size: 28px; margin-right: 18px;">🚀</div>
    <div style="flex: 1; z-index: 1;">
      <h4 style="color: #1a3a5f; margin: 0; font-size: 15px; text-transform: uppercase;">Strategic Retention</h4>
      <p style="color: #444; margin: 3px 0 0 0; font-size: 14px;">How can prevention be personalized at scale to ensure costs align with LTV?</p>
    </div>
    <div style="color: #566573; font-size: 50px; font-weight: 900; position: absolute; right: 8px; bottom: -10px; z-index: 0;">04</div>
  </div>
</div>

<br>

<div style="background-color: #e9ecef; padding: 30px; border-radius: 15px; width: 100%;">
  <h2 style="color: #1a3a5f; margin-top: 0; border-bottom: none;">🔑 Key Findings & Outcomes</h2>
  <div style="background-color: #ffffff; padding: 18px; border-radius: 10px; border-left: 10px solid #d4e6f1; margin-bottom: 18px; box-shadow: 0 8px 20px rgba(212, 230, 241, 0.8);">
    <b style="color: #1a3a5f; font-size: 15px;">1. High-Level Churn Impact Visualization</b>
    <p style="margin-top: 5px; color: #2c3e50; font-size: 14px;">Comprehensive view of churn severity, mapping its direct correlation to portfolio value decay.</p>
  </div>
  <div style="background-color: #ffffff; padding: 18px; border-radius: 10px; border-left: 10px solid #a9cce3; margin-bottom: 18px; box-shadow: 0 8px 20px rgba(169, 204, 227, 0.8);">
    <b style="color: #1a3a5f; font-size: 15px;">2. Sequential Churn Drivers</b>
    <p style="margin-top: 5px; color: #2c3e50; font-size: 14px;">Churn is driven by behavioral sequences typically involving a primary negative behavior reinforced by secondary triggers.</p>
  </div>
  <div style="background-color: #ffffff; padding: 18px; border-radius: 10px; border-left: 10px solid #7fb3d5; margin-bottom: 18px; box-shadow: 0 8px 20px rgba(127, 179, 213, 0.8);">
    <b style="color: #1a3a5f; font-size: 15px;">3. Threshold Identification</b>
    <p style="margin-top: 5px; color: #2c3e50; font-size: 14px;">Identified critical behavioral thresholds where churn probability increases sharply.</p>
  </div>
  <div style="background-color: #ffffff; padding: 18px; border-radius: 10px; border-left: 10px solid #5499c7; margin-bottom: 18px; box-shadow: 0 8px 20px rgba(84, 153, 199, 0.8);">
    <b style="color: #1a3a5f; font-size: 15px;">4. Predictive & Explanatory Modeling</b>
    <p style="margin-top: 5px; color: #2c3e50; font-size: 14px;">Developed models for both likelihood estimation and individual driver interpretation for action.</p>
  </div>
  <div style="background-color: #ffffff; padding: 18px; border-radius: 10px; border-left: 10px solid #2980b9; box-shadow: 0 8px 25px rgba(41, 128, 185, 0.5);">
    <b style="color: #1a3a5f; font-size: 15px;">5. Behavior-Based Framework</b>
    <p style="margin-top: 5px; color: #2c3e50; font-size: 14px;">Established a monitoring framework using defined thresholds to support proactive retention efforts.</p>
  </div>
</div>

<br>

<h2 style="color: #1a3a5f; padding-left: 10px; border-bottom: none;">📁 Analysis Documents</h2>
<p style="padding-left: 10px; color: #7f8c8d; font-style: italic; margin-bottom: 15px;">Technical implementation and code:</p>

<div style="display: flex; flex-wrap: wrap; gap: 12px; padding: 10px;">
  <a href="https://nbviewer.org/github/DungNguyen396/DungNguyen-portfolio/blob/main/project1-churn/eda.ipynb" style="text-decoration: none; flex: 1; min-width: 250px;">
    <div style="background-color: #f0f4f8; padding: 15px 20px; border-radius: 10px; border: 1px solid #d1d9e6; display: flex; align-items: center; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
      <span style="font-size: 20px; margin-right: 12px;">🔍</span>
      <b style="color: #1a3a5f; font-size: 13px; text-transform: uppercase; letter-spacing: 0.5px;">EDA & Preparation</b>
    </div>
  </a>
  <a href="./query.md" style="text-decoration: none; flex: 1; min-width: 250px;">
    <div style="background-color: #eef7fd; padding: 15px 20px; border-radius: 10px; border: 1px solid #cfe6f5; display: flex; align-items: center; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
      <span style="font-size: 20px; margin-right: 12px;">⚡</span>
      <b style="color: #4682B4; font-size: 13px; text-transform: uppercase; letter-spacing: 0.5px;">BigQuery ML Modeling</b>
    </div>
  </a>
  <a href="https://nbviewer.org/github/DungNguyen396/DungNguyen-portfolio/blob/main/project1-churn/explain.ipynb" style="text-decoration: none; flex: 1; min-width: 250px;">
    <div style="background-color: #f8f9fa; padding: 15px 20px; border-radius: 10px; border: 1px solid #e9ecef; display: flex; align-items: center; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
      <span style="font-size: 20px; margin-right: 12px;">📊</span>
      <b style="color: #708090; font-size: 13px; text-transform: uppercase; letter-spacing: 0.5px;">Strategic Action Plan</b>
    </div>
  </a>
</div>

<br><br>

<div align="center" style="padding-bottom: 50px;">
  <hr style="border: 0; border-top: 1px solid #dee2e6; margin-bottom: 30px;">
  <a href="https://dungnguyen396.github.io/DungNguyen-Portfolio/" style="background-color: #1a3a5f; color: white; padding: 12px 30px; text-decoration: none; border-radius: 8px; font-weight: bold; font-size: 14px;">← BACK TO MAIN PORTFOLIO</a>
</div>
