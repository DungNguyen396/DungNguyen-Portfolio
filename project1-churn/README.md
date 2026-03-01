<div align="center">
  <h1 style="color: #1a3a5f; border-bottom: none; margin-bottom: 10px; font-size: 32px;">BEHAVIORAL ANALYSIS & CHURN PREDICTION</h1>
  <div style="margin-bottom: 20px;">
    <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" />
    <img src="https://img.shields.io/badge/Focus-Retention%20Strategy-1a3a5f?style=for-the-badge" />
    <img src="https://img.shields.io/badge/Tech-Python%20%7C%20BigQuery-4682B4?style=for-the-badge" />
  </div>
</div>

<div style="background-color: #e9ecef; padding: 30px; border-radius: 15px;">
  <div style="background-color: #ffffff; padding: 30px; border-radius: 12px; border-left: 10px solid #1a3a5f; box-shadow: 0 4px 15px rgba(0,0,0,0.05);">
    <h2 style="color: #1a3a5f; margin-top: 0; border-bottom: none; font-size: 24px;">📌 Project Background</h2>
    <p style="color: #2c3e50; line-height: 1.8; font-size: 16px; text-align: justify; margin-bottom: 0;">
      This project was initiated following a request from the internal Data Analysis team to develop a robust predictive model for customer churn. The primary objective was to move beyond retrospective reporting and establish an early-warning system for the strategic departments. By identifying high-risk behavioral patterns before a customer actually leaves, the organization can proactively deploy retention campaigns. This analysis serves as the foundation for data-driven interventions aimed at stabilizing the customer base and protecting long-term revenue.
    </p>
  </div>
</div>

<br>

<div style="padding: 10px;">
  <h2 style="color: #1a3a5f; border-bottom: 2px solid #1a3a5f; display: inline-block;">❓ Business Questions</h2>
  <p style="color: #7f8c8d; font-style: italic; margin-top: 5px;">Shifting from descriptive statistics to proactive churn management:</p>
  
  <table border="0" width="100%" style="border-collapse: separate; border-spacing: 15px;">
    <tr>
      <td width="50%" style="background-color: #f8f9fa; border: 1px solid #dee2e6; border-radius: 15px; padding: 25px; vertical-align: top;">
        <span style="background-color: #1a3a5f; color: white; padding: 5px 12px; border-radius: 20px; font-size: 12px; font-weight: bold;">COMMERCIAL</span>
        <h4 style="color: #1a3a5f; margin: 15px 0 10px 0;">Impact of Churn</h4>
        <p style="color: #444; font-size: 14px; line-height: 1.6; margin: 0;">Beyond the rate itself, what is the actual severity of churn in terms of revenue loss and market share erosion?</p>
      </td>
      <td width="50%" style="background-color: #f8f9fa; border: 1px solid #dee2e6; border-radius: 15px; padding: 25px; vertical-align: top;">
        <span style="background-color: #4682B4; color: white; padding: 5px 12px; border-radius: 20px; font-size: 12px; font-weight: bold;">BEHAVIORAL</span>
        <h4 style="color: #1a3a5f; margin: 15px 0 10px 0;">Breakpoints</h4>
        <p style="color: #444; font-size: 14px; line-height: 1.6; margin: 0;">What specific sequences of actions trigger a transition from a "Loyal" to an "At-Risk" state?</p>
      </td>
    </tr>
    <tr>
      <td width="50%" style="background-color: #f8f9fa; border: 1px solid #dee2e6; border-radius: 15px; padding: 25px; vertical-align: top;">
        <span style="background-color: #708090; color: white; padding: 5px 12px; border-radius: 20px; font-size: 12px; font-weight: bold;">DETECTION</span>
        <h4 style="color: #1a3a5f; margin: 15px 0 10px 0;">Early Warning</h4>
        <p style="color: #444; font-size: 14px; line-height: 1.6; margin: 0;">How can we identify the "point of no return" to intervene effectively before the final transaction?</p>
      </td>
      <td width="50%" style="background-color: #f8f9fa; border: 1px solid #dee2e6; border-radius: 15px; padding: 25px; vertical-align: top;">
        <span style="background-color: #2c3e50; color: white; padding: 5px 12px; border-radius: 20px; font-size: 12px; font-weight: bold;">SCALABILITY</span>
        <h4 style="color: #1a3a5f; margin: 15px 0 10px 0;">Strategic Retention</h4>
        <p style="color: #444; font-size: 14px; line-height: 1.6; margin: 0;">How can prevention be personalized at scale without exceeding the customer's lifetime value?</p>
      </td>
    </tr>
  </table>
</div>

<br>

<div style="background-color: #e9ecef; padding: 35px; border-radius: 20px;">
  <h2 style="color: #1a3a5f; border-bottom: none; margin-top: 0; margin-bottom: 25px;">🔑 Key Findings & Outcomes</h2>
  
  <table border="0" width="100%" style="border-collapse: separate; border-spacing: 0 15px;">
    <tr>
      <td style="background-color: #ffffff; border-radius: 12px; padding: 20px; border-left: 5px solid #1a3a5f; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
        <b style="color: #1a3a5f; font-size: 17px;">01. Churn Impact Visualization</b>
        <p style="margin: 8px 0 0 0; color: #444; font-size: 15px;">Provided a comprehensive view of churn severity, mapping its direct correlation to portfolio value decay.</p>
      </td>
    </tr>
    <tr>
      <td style="background-color: #ffffff; border-radius: 12px; padding: 20px; border-left: 5px solid #4682B4; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
        <b style="color: #4682B4; font-size: 17px;">02. Sequential Churn Drivers</b>
        <p style="margin: 8px 0 0 0; color: #444; font-size: 15px;">Proved churn is driven by behavioral sequences; typically a primary negative behavior reinforced by secondary triggers.</p>
      </td>
    </tr>
    <tr>
      <td style="background-color: #ffffff; border-radius: 12px; padding: 20px; border-left: 5px solid #708090; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
        <b style="color: #708090; font-size: 17px;">03. Threshold Identification</b>
        <p style="margin: 8px 0 0 0; color: #444; font-size: 15px;">Identified critical thresholds where churn probability increases sharply, enabling data-driven monitoring.</p>
      </td>
    </tr>
    <tr>
      <td style="background-color: #ffffff; border-radius: 12px; padding: 20px; border-left: 5px solid #1a3a5f; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
        <b style="color: #1a3a5f; font-size: 17px;">04. Prediction & Explanation Models</b>
        <p style="margin: 8px 0 0 0; color: #444; font-size: 15px;">Developed dual models: one for likelihood estimation and another for interpreting individual drivers for action.</p>
      </td>
    </tr>
    <tr>
      <td style="background-color: #ffffff; border-radius: 12px; padding: 20px; border-left: 5px solid #2c3e50; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
        <b style="color: #2c3e50; font-size: 17px;">05. Behavior-Based Framework</b>
        <p style="margin: 8px 0 0 0; color: #444; font-size: 15px;">Established a monitoring framework using behavioral thresholds to support ongoing, proactive retention efforts.</p>
      </td>
    </tr>
  </table>
</div>

<br>

<div align="center" style="padding: 30px; border: 2px dashed #dee2e6; border-radius: 15px;">
  <h2 style="color: #1a3a5f; border-bottom: none; margin-top: 0;">📁 Technical Documentation</h2>
  <p style="color: #7f8c8d; margin-bottom: 25px;">Deep dive into the technical implementation and code:</p>
  
  <a href="https://nbviewer.org/github/DungNguyen396/DungNguyen-portfolio/blob/main/project1-churn/eda.ipynb" style="display: inline-block; background-color: #ffffff; color: #1a3a5f; border: 2px solid #1a3a5f; padding: 12px 20px; text-decoration: none; border-radius: 10px; font-weight: bold; margin: 5px;">🔍 EDA & Preparation</a>
  
  <a href="./query.md" style="display: inline-block; background-color: #ffffff; color: #4682B4; border: 2px solid #4682B4; padding: 12px 20px; text-decoration: none; border-radius: 10px; font-weight: bold; margin: 5px;">⚡ BigQuery ML</a>
  
  <a href="https://nbviewer.org/github/DungNguyen396/DungNguyen-portfolio/blob/main/project1-churn/explain.ipynb" style="display: inline-block; background-color: #ffffff; color: #708090; border: 2px solid #708090; padding: 12px 20px; text-decoration: none; border-radius: 10px; font-weight: bold; margin: 5px;">📊 Strategic Plan</a>
</div>

<br>

<div align="center" style="padding-top: 20px; padding-bottom: 50px;">
  <a href="https://dungnguyen396.github.io/DungNguyen-Portfolio/" style="color: #1a3a5f; text-decoration: none; font-weight: bold; font-size: 16px; border-bottom: 2px solid #1a3a5f;">← BACK TO MAIN PORTFOLIO</a>
</div>
