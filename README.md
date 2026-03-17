# Credit-Risk-Modeling– Probability of Default Prediction
A credit scoring project developed under the supervision of a PwC consultant,
as part of my Data Science Engineering studies at ESSAI Tunis.The goal is to predict the probability of default (PD) for bank clients using logistic regression,
following the internal rating model methodology used in the banking industry.

## What this project does

Starting from a real bank client dataset (~5000 observations), I built a full credit scoring pipeline :

- Data quality check : missing values, duplicates, business coherence filters
- Feature engineering and median imputation
- Handling class imbalance with SMOTE
- Feature selection using Information Value (IV >= 0.02)
- Logistic Regression model (70/30 stratified split)
- Model evaluation with AUC and GINI coefficient
- Credit score output on a 300–850 scale with 3 risk classes

 ## Repository structure
credit-risk-modeling/
├── credit_risk_modeling.ipynb   # full pipeline
├── Rapport_Data_Quality_Check.pdf  # step 1 report
├── resultats_scoring.xlsx       # model output : PD, score, risk class
└── README.md

## Methodology

### Data Quality Check
The dataset contains socio-demographic, financial and credit behavior variables.
I identified variable types, analyzed missing values (excluded variables above 80% missingness),
detected 27 duplicate observations, and applied business filters on age, financial ratios and revenues.

### Feature Selection
I used Information Value to rank variables and kept those with IV >= 0.02.
Final variables retained :

| Variable | Description |
|---|---|
| Engagement | Total bank engagement |
| Revenus_mensuels | Monthly income |
| Garantie | Collateral value |
| Maturite | Loan maturity |
| Age_relation | Client relationship seniority |
| Interdiction_cheque | Check ban flag |
| Etat_civil_Celibataire | Marital status |
| Nationalite_Morocco | Nationality |

### Model
Logistic Regression with lbfgs solver, trained on SMOTE-resampled data.
Evaluated using AUC and GINI on the test set.

### Scoring
Probabilities converted to a credit score :
Score = 850 - (PD × 550)


| Risk Class | PD |
|---|---|
| Low Risk | < 0.20 |
| Medium Risk | 0.20 – 0.40 |
| High Risk | >= 0.40 |



## Stack

Python · Pandas · Scikit-learn · imbalanced-learn · scorecardpy · Matplotlib · Seaborn


## Authors

Zeineb Jeljli & Azza Wahabi — Data Science Engineering, ESSAI Tunis
Supervised by Mme Chammam (PwC) — 2025/2026

> The original dataset is confidential and not included in this repository.
