# 🌍 Financial Inclusion in Africa — Zindi Competition

[![Zindi Competition](https://img.shields.io/badge/Competition-Zindi-blue?style=for-the-badge)](https://zindi.africa)
[![Python](https://img.shields.io/badge/Python-3.8+-yellow?style=for-the-badge&logo=python)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/Model-XGBoost-EB2027?style=for-the-badge)](https://xgboost.readthedocs.io/)

> **"Every submission taught us something. Every failed experiment made the final model stronger."**

This repository documents the complete **27-submission journey** to predict bank account ownership in East Africa. From a simple baseline to a high-performance stacked ensemble, this notebook captures the iterative process of feature engineering, model selection, and hyperparameter optimization.

---

## 📖 Project Overview

**The Challenge:**
Predict which individuals in East Africa (Kenya, Rwanda, Tanzania, and Uganda) are most likely to have or use a bank account. Financial inclusion is a key driver of economic development, and predicting usage helps organizations target their services effectively.

*   **Target Variable:** `bank_account` (1 = Has account, 0 = No account)
*   **Evaluation Metric:** Accuracy Score
*   **Dataset:** 23,524 training samples | 10,086 test samples | 13 initial features

---

## 📊 Submission History & Evolution

Our journey involved testing multiple hypotheses, from simple encoding fixes to complex stacking architectures.

| Phase | Submissions | Key Improvements | Best Score |
| :--- | :--- | :--- | :--- |
| **I: Baseline** | #01 - #07 | Fixed encoding bugs, implemented CV, benchmarked LGBM/XGB/RF. | 0.8980 |
| **II: Engineering** | #08 - #15 | Age/HH bins, interaction features, country-level group statistics. | 0.9012 |
| **III: Tuning** | #16 - #19 | Optuna automated hyperparameter search & Stratified K-Fold CV. | 0.9020 |
| **IV: Ensembling** | #20 - #27 | **Stacked Ensemble** (LGBM + XGB + CatBoost) with RF Meta-learner. | **0.9041** |

---

## 🔧 Feature Engineering Pipeline

The most significant performance gains came from carefully crafted features:

1.  **Demographic Bins**: Grouped age and household size into statistically significant ranges.
2.  **Interaction Features**: Combined location (Urban/Rural) with cellphone access.
3.  **Job Grouping**: Simplified `job_type` into high-level categories (Formal, Informal, Dependent).
4.  **Group Statistics**: Calculated country-level bank account rates to capture regional economic variance.
5.  **Target Encoding**: Used smoothed target encoding for high-cardinality categorical features.

---

## 🚀 Model Architecture

Our final winning submission (#27) utilized a **Voting & Stacking Architecture**:

*   **Level 0 (Base Models):**
    *   **LightGBM**: Exceptional at handling categorical features.
    *   **XGBoost**: Robust gradient boosting with fine-tuned regularization.
    *   **CatBoost**: Native handling of categorical variables for superior generalization.
*   **Level 1 (Meta-learner):**
    *   **Random Forest / Logistic Regression**: Blends the predictions to minimize variance and maximize accuracy.

---

## 🛠️ Tech Stack & Libraries

*   **Models**: LightGBM, XGBoost, CatBoost, Scikit-Learn
*   **Tuning**: Optuna (Bayesian Optimization)
*   **Preprocessing**: Imbalanced-Learn (SMOTE/Undersampling), Category Encoders
*   **Visualization**: Seaborn, Matplotlib, Plotly
*   **Environment**: Google Colab / Jupyter Notebook

---

## 📈 Results

*   **Initial Baseline**: ~0.8963
*   **Final Best Score**: **0.9041**
*   **Total Iterations**: 27 Submissions

---

*This project was developed as part of the Zindi Financial Inclusion Challenge.*
