# Heart Disease Prediction — Data Mining

Academic project | University of Jeddah | Data Science Department | 2025

## Overview

Analyzed 2,182 patient records from 5 combined public datasets to predict heart disease risk.
The project follows a complete data mining pipeline: EDA, Decision Tree classification across
12 configurations, and K-Means clustering for patient segmentation.

## Dataset

| Property | Value |
|----------|-------|
| Raw records | 2,182 |
| After cleaning | 1,889 |
| Features | 14 clinical features |
| Target | Binary (0 = low risk, 1 = high risk) |
| Source | 5 combined public heart disease datasets |

**Features:** age, sex, chest pain type (cp), resting blood pressure (trestbps),
cholesterol (chol), fasting blood sugar (fbs), resting ECG (restecg),
max heart rate (thalachh), exercise-induced angina (exang), ST depression (oldpeak),
slope, number of vessels (ca), thalassemia (thal)

## Results

### Decision Tree — Best Model

| Metric | Score |
|--------|-------|
| Accuracy | 85% |
| Overall Score | 0.87 |
| Lift (3rd decile) | 1.20 |
| Best config | Information Gain + 3.5% min leaf |

### Decision Tree — All Configurations Compared

| Config | Accuracy | Overall Score |
|--------|----------|---------------|
| Info Gain · 3.5% leaf ★ | 0.85 | **0.87** |
| Gini · 3.5% leaf | 0.84 | 0.86 |
| Info Ratio · 3.5% leaf | 0.83 | 0.85 |
| Info Gain · 6.0% leaf | 0.82 | 0.84 |
| Gini · 6.0% leaf | 0.81 | 0.83 |
| Info Ratio · 6.0% leaf | 0.80 | 0.82 |

### K-Means Clustering — Patient Segmentation

K=3 selected via Elbow Method — 3 clinically distinct patient groups identified.

| Cluster | Profile | Key Features |
|---------|---------|--------------|
| Cluster 0 | Moderate risk · Middle-aged | Average BP and cholesterol |
| Cluster 1 | Higher risk · Older patients | Higher blood pressure · Higher cholesterol |
| Cluster 2 | High chest pain risk | Atypical angina · Flatter ST slope |

**Key discriminating features across clusters:**
- `thal` — Thalassemia type (iron levels → younger patients in Cluster 0)
- `cp` — Chest pain type (atypical angina → higher risk in Cluster 2)
- `slope` — ST slope (flatter slope → higher heart failure risk)
- `age` — Higher age → higher risk

## Pipeline

```
Raw Data (2,182) → Cleaning & Outlier Removal → 1,889 records
→ EDA (distributions, boxplots, correlation)
→ Decision Tree (12 configs: Info Gain / Gini / Info Ratio × leaf sizes)
→ K-Means Clustering (K=2,3,4,5 → selected K=3)
→ Decision Tree per Cluster (explainability)
```

## Tech Stack

| Category | Tools |
|----------|-------|
| Platform | RapidMiner Studio |
| Classification | Decision Tree (Information Gain, Gini, Information Ratio) |
| Clustering | K-Means (K=2–5, Elbow Method) |
| Analysis | Python · Pandas · Scikit-learn · Matplotlib · Seaborn |

## Key Findings

- Information Gain with 3.5% minimum leaf size consistently outperformed all other configurations
- K=3 clustering revealed clinically meaningful patient subgroups validated by domain features
- Thalassemia type and chest pain type are the strongest predictors of heart disease risk
- Decision trees per cluster provided interpretable insights for each patient subgroup

## Team

University of Jeddah — Data Mining Course Project 2025
Supervised by Dr. Abdullah Alghoson
