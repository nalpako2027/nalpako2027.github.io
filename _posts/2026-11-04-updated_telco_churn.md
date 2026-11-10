---
title: "Updated: Customer Churn Prediction and Retention Strategy Analysis with Business Impact Simulation"
layout: single
show_excerpts: false
categories:
  - Repository
tags:
  - Data Science
  - Machine learning
  - XGBoost
  - Logistic regression
  - KNN
  - Intervention Simulation
link: "https://github.com/nalpako2027/telco_customer_churn_prediction_simulation.git"
header:
  teaser: "assets/images/roc_curve_comparison.png"
---


💸 A $15/month "win-back" discount can lose money. A $2/month perk can return 4x. Same customers, same model.
I just updated my Telco churn project, and the biggest lesson wasn't about the model. It was about the offer. 👇
📊 The setup
26.5% of customers in the IBM Telco dataset churned, roughly $139K in lost monthly revenue. So I asked: what customer should be contacted, and how much can we afford to spend?
🔍 What I did
• Used XGBoost (gain importance) to narrow 23 encoded features (after one-hot encoding) down to 13
• Compared Logistic Regression vs. KNN on unseen customers
• Logistic Regression won: it caught 77.2% of actual churners (ROC-AUC 0.85) with well-calibrated probabilities
• Grouped customers into 4 risk tiers; the top two (22% of customers) hold 56.6% of the revenue at risk
⚠️ The highest-risk profile: month-to-month contract + fiber optic + electronic check
💰 The business impact (assuming a 20% save rate)
• $2/month offer → 431.5% ROI
• $7/month offer → 51.9% ROI
• $15/month offer → −29.1% ROI
• Break-even: about $10.63/month
🎯 Takeaway: a good model tells you WHO to target. The economics of the offer decide WHETHER it's worth it.

Limitation: the 20% save rate is an assumption, so these are upper-bound scenarios. The data show association, not causation. Next step: an A/B test with a no-offer control group.
📂 Full code, notebooks and executive summary: https://lnkd.in/dNg9tE95
I'd love feedback from anyone working in retention or marketing analytics. How do you estimate save rates before running a campaign? 🤔
