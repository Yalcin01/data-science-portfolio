# 01 — Credit scoring with a business-driven metric

**Question:** a consumer-credit company wants to decide whether to grant a loan to clients with little or no credit history, and to explain each decision to its advisors and clients.

**Data:** [Home Credit Default Risk](https://www.kaggle.com/c/home-credit-default-risk) — 307,511 applications, 241 features after encoding, only ~8 % defaults (strongly imbalanced).

## Approach
1. **Exploration & cleaning:** target distribution, anomaly detection (e.g. an impossible "days employed" value affecting 55k rows), train/test column alignment, missing values.
2. **Baseline models:** Dummy, Logistic Regression, Random Forest, XGBoost, LightGBM.
3. **Class imbalance:** SMOTE, ADASYN and random undersampling inside `imblearn` pipelines, tuned with cross-validated grid search (AUC ≈ 0.74).
4. **Business metric:** granting a loan to a client who defaults costs far more than refusing a good client. I built a custom **F-beta score (β = 10)** to weight that cost, and optimised the models on it rather than on accuracy.
5. **Explainability:** global feature importance and **SHAP** force plots for individual clients, so an advisor can see *why* a given client was scored as risky.
6. **Deployment (at the time):** serialised LightGBM model, JSON export and data samples for an API and a Streamlit dashboard hosted on AWS (no longer online).

## Why it matters
Turning a model into a decision rule means choosing the metric that reflects business cost, and being able to justify each individual decision. That is the same logic I applied as Product Owner on an anti-fraud control at a public payment agency.

**Stack:** pandas, scikit-learn, imbalanced-learn, XGBoost, LightGBM, SHAP, joblib

> Note: the test-set AUC of the baseline models was originally computed on hard labels; those cells have been corrected to use predicted probabilities (see the note in the notebook).
