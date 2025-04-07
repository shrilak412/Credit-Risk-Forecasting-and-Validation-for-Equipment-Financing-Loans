📘 Project: Credit Risk Modeling & Portfolio Stress Testing
🔍 Overview
This project simulates and analyzes a $5M small business loan portfolio using machine learning to predict:

📉 Probability of Default (PD) using a Decision Tree Classifier with class balancing (SMOTE)

💸 Loss Given Default (LGD) using a Random Forest Regressor

It includes full EDA, feature engineering, model evaluation, portfolio-level monitoring, and economic stress scenario analysis.

🧩 Dataset
Source: LendingClub Small Business Loan data

Period: 2016Q4 to 2018Q4 (for portfolio monitoring)

Size: ~15,000 loans post-cleaning

Labels:

default (binary)

lgd = (Loan Amount − Recovered Principal) / Loan Amount

🧪 Models Developed
Model	Target	Key Features Used	Metric Highlights
Decision Tree Classifier (with SMOTE)	PD	loan_amnt, dti, annual_inc, fico_range_low, term, grade, int_rate	ROC-AUC: 0.63, Recall: 52%, Precision: 40%
Random Forest Regressor	LGD	Same as above	MAE: 0.16, R²: 0.09, RMSE: 0.20
Models trained using GridSearchCV on scaled data

Balanced class distribution for PD via SMOTE

Robust evaluation using KS-Stat, ROC-AUC, and SHAP

📊 Portfolio Monitoring
Simulates $5M portfolio allocation across 9 quarters

Computes Expected Loss per quarter:

Expected Loss
=
𝑃
𝐷
×
𝐿
𝐺
𝐷
×
𝐸
𝑥
𝑝
𝑜
𝑠
𝑢
𝑟
𝑒
Expected Loss=PD×LGD×Exposure
Visualizes loss trajectory using Matplotlib

🌪️ Stress Testing
Simulates economic downturns by modifying key borrower features:

Scenario	int_rate ↑	fico_range_low ↓	annual_inc ↓	dti ↑
Baseline	–	–	–	–
Mild Stress	+1.0%	−20 pts	−5%	+2
Severe Stress	+3.0%	−40 pts	−20%	+5
Recalculates expected loss under stressed conditions

Outputs scenario-wise risk comparison

📈 Visual Insights
Default rate by loan grade

Default rate over time (2007–2018)

Correlation heatmap of features

SHAP interpretability plots (LGD model)

Actual vs. Predicted LGD scatter

💼 Business Impact
Helps lenders evaluate portfolio health

Supports capital allocation decisions

Enables preparation for economic shocks

Encourages risk-based pricing strategies
