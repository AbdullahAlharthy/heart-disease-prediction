# Customer Churn Prediction — Telecom

Graduation project | University of Jeddah | Data Science Department

## Overview
Predictive system to identify telecom customers at risk of churning, 
built using the CRISP-DM methodology on the IBM Telco dataset (7,043 records).

The core challenge: severe class imbalance (26.5% churn rate).  
The solution: combine **TabDDPM** synthetic data generation with 
**SMOTETomek** boundary refinement + **LightGBM** + threshold tuning.

## Results

| Metric                  | Score |
|-------------------------|-------|
| F1-Score                | 0.67  |
| Recall                  | 0.78  |
| Precision               | 0.58  |
| Improvement vs baseline | +7% F1 |

> Recall was prioritized: missing a churner costs 5× more than a false positive.

## Pipeline

```
Raw Data → Label Encoding → TabDDPM (4.8:1 synthetic ratio)
→ SMOTETomek → LightGBM → Threshold Tuning → Final Model
```

## Business Segmentation

Customers were segmented into 4 groups based on the model's 
churn probability score × customer value:

| Segment       | Churn Risk | Value |
|---------------|------------|-------|
| 🔵 Champions  | Low        | High  |
| 🔴 At Risk    | High       | High  |
| ⚫ Lost Cause | High       | Low   |
| 🔷 Potential  | Low        | Low   |

Churn probability scores from the LightGBM model were used 
to assign each customer to a segment — translating model 
output into actionable business groups.

## Tech Stack

| Category       | Tools                                      |
|----------------|--------------------------------------------|
| Core Model     | LightGBM                                   |
| Synthetic Data | TabDDPM                                    |
| Imbalance      | SMOTETomek, SMOTEENN, ADASYN, BorderlineSMOTE |
| AutoML         | H2O AutoML, PyCaret                        |
| HPO            | Optuna, GridSearchCV, RandomizedSearch     |
| Explainability | SHAP                                       |
| Data           | Pandas, Scikit-learn                       |

## Experiments
- **10 ML models** compared (LightGBM, CatBoost, XGBoost, MLP, TabNet, SVM, NB, LR...)
- **6 balancing strategies** evaluated
- **4 encoding schemes** tested
- **50+ documented runs**

## Key Findings
- TabDDPM synthetic data raised F1 by **~7%** (0.63 → 0.67) on unseen test set
- Contract type, tenure, and monthly charges are the strongest churn drivers (SHAP)
- Threshold tuning on validation set maximized recall without retraining

## Team
University of Jeddah — Senior Project 2025  
Supervised by Dr. Ahmad Alamri
