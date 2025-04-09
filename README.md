# 🚀 Credit Risk Forecasting & Validation for Equipment Finance Loans

![Credit Risk Banner](https://img.shields.io/badge/Project-Credit%20Risk%20Forecasting-blueviolet)  
![Python](https://img.shields.io/badge/Python-3.11-blue) ![Pandas](https://img.shields.io/badge/Pandas-2.2.2-green) ![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.5.1-orange)

## 🌟 Project Snapshot
Ever wondered how financial institutions forecast whether a loan might default? This project dives into that question, combining machine learning with financial analytics to predict credit risk for a $5M equipment finance loan portfolio. It simulates an end-to-end credit risk system using **Python**, **Pandas**, and **Scikit-learn** to estimate:

- **Probability of Default (PD)**
- **Loss Given Default (LGD)**

From preprocessing to deployment planning, this project reflects my deep dive into financial risk modeling, regulatory insights, and the real-world impact of smart analytics.

---

## 📊 Goals and Objectives
- Forecast **PD** and **LGD** to estimate expected losses
- Stress-test the loan portfolio under economic downturns
- Validate models using backtesting, out-of-sample testing, and sensitivity analysis
- Propose a scalable deployment solution using Microsoft Azure

---

## 🌐 Model Selection Process
### ✅ **PD Model (Random Forest Classifier)**
- Evaluated: Logistic Regression, XGBoost, Random Forest
- **Why Random Forest?** Best balance of recall and ROC-AUC with interpretability
- **ROC-AUC**: 0.6688 (train), 0.6500 (test)  
- **Hyperparameters**: `n_estimators=200`, `max_depth=10`, `min_samples_split=5`, `min_samples_leaf=2`, `class_weight="balanced"`

### ✅ **LGD Model (Random Forest Regressor)**
- Evaluated: Linear Regression, XGBoost, Random Forest
- **Why Random Forest?** Lowest MAE, handled skewed distribution better
- **MAE**: 0.0215 (train), though **R^2** was negative due to low variance in LGD
- **LGD challenges**: Unrealistic recovery assumptions skewed predictions

---

## 📖 Methodology
1. **Data Preprocessing**
   - Started with 15,577 loans, filtered down to 6,537
   - Engineered LGD, handled missing values, encoded categorical data
2. **Model Training**
   - Trained on 3,922 loans with GridSearchCV for optimization
3. **Stress Testing**
   - Adjusted key features like `int_rate`, `fico_range_low`, and `annual_inc` across baseline and stressed scenarios
4. **Model Validation**
   - Split into train, validate, test (60-20-20)
   - Evaluated with ROC-AUC, MAE, R^2, and backtesting

---

## 🔍 Key Findings
### 🔢 PD Model
- Moderate ROC-AUC, but recall suggests potential overfitting
- Missed half of actual defaults; threshold tuning recommended

### 🔢 LGD Model
- Very low predicted LGD values due to skewed distribution
- Realistic recovery cost data needed for better accuracy

### 📊 Stress Testing Insights
- Expected loss increased by 4.24% under mild stress
- Severe stress scenario underperformed mild stress (due to LGD inconsistency)

### 🔄 Backtesting
- Overestimated expected loss by ~23%
- PD model slightly overpredicts; LGD model underpredicts loss severity

### 📊 Sensitivity Analysis
- Small changes in `int_rate`, `fico_range_low` influence PD

### 🔺 Model Stability
- Stable ROC-AUC across multiple subsets (Std Dev: 0.0037)

---

## 🛠️ Tools & Tech Stack
- **Languages**: Python 3.11
- **Libraries**: Pandas, NumPy, Scikit-learn, Matplotlib
- **Environment**: Jupyter Notebook
- **Deployment Plan**: Microsoft Azure (Blob Storage, ML, Data Factory)

---

## 🌐 Visuals & Feature Importance
- Feature importances (PD): `int_rate` (37.8%), `fico_range_low` (18.8%), `term` (16.9%)
- Feature importances (LGD): `fico_range_low`, `dti`, `int_rate`

---

## 🔍 Recommendations
1. Use realistic LGD assumptions & recovery datasets
2. Optimize PD threshold for higher recall
3. Refine LGD model to reflect economic stress accurately
4. Consider XGBoost if data quality improves

---

## ⚡ How to Run It
### Prerequisites
- Python 3.11+
- Install required libraries:
```bash
pip install pandas numpy scikit-learn matplotlib jupyter
```

---

This project was not just about predictive modeling—it was about learning the language of credit, risk, and responsible finance. Let's connect if you're working on similar domains or have feedback!

