# Data Science Portfolio — Yalcin Keles

Industrial engineer (Grenoble INP, Supply Chain Management) turned data Product Owner. These projects were built during the **Data Scientist programme of OpenClassrooms & CentraleSupélec** (2022, RNCP level 7). Each one starts from a business question and ends with a model, a metric or a decision aid, not just a score.

| # | Project | Business question | Key techniques | Highlights |
|---|---------|-------------------|----------------|------------|
| 01 | [Credit scoring](01-credit-scoring) | Should this loan be granted, and why? | LightGBM, XGBoost, SMOTE/ADASYN, custom business metric, SHAP | 307k applications · cost-sensitive F-beta metric · explainable per-client decisions |
| 02 | [Big data on AWS](02-big-data-spark-aws) | How to scale image processing for a large catalogue? | PySpark, AWS EC2 + S3, VGG16 transfer learning, distributed PCA | End-to-end cloud pipeline · 90 % variance kept with PCA |
| 03 | [Energy & CO₂ prediction](03-energy-co2-prediction) | Can we predict building emissions without costly annual readings? | XGBoost, Gradient Boosting, Hyperopt, Optuna, SHAP, LIME | R² ≈ 0.81 (CO₂) and 0.82 (energy) vs. 0 for the baseline |
| 04 | [Product classification (NLP + vision)](04-product-classification-nlp-vision) | Can product categories be assigned automatically from text and images? | TF-IDF, SVD, UMAP, t-SNE, SIFT, VGG16, ResNet50 | ARI from 0.04 (SIFT) to 0.46 (text) · ~85 % accuracy on validation with supervised ResNet50 |
| 05 | [Customer segmentation](05-customer-segmentation) | Which customer segments should marketing target? | RFM, K-Means, DBSCAN, PCA, t-SNE, ARI stability | 6 segments (silhouette 0.45) · stability over time with ARI |
| 06 | [Food data quality](06-food-data-quality) | Is a large open dataset reliable enough to use? | Data cleaning, fuzzy matching, KNN imputation, OLS | ~820k products · fuzzy deduplication · KNN imputation |

## How these projects connect to my work

- **Data governance & quality** (projects 03, 06): the same discipline I applied as a data steward on reference data at Renault Trucks.
- **Risk detection & explainability** (project 01): the logic behind the anti-fraud control I designed as Product Owner at the French payment agency ASP (+50 % flagged cases vs. the initial model in the POC, fraud detected at application stage instead of payment).
- **Data engineering & cloud** (project 02): building pipelines that scale, not only models.
- **Translating models into decisions** (all): business metrics, SHAP explanations and segment profiles that a non-technical stakeholder can act on.

## Notes

- Notebook explanations and code comments have been translated into English. The code itself is unchanged, so some variable names and chart labels remain in French. Error outputs and oversized interactive charts were removed for readability on GitHub.
- Datasets are public and not included; each project README links to its source.
- Some notebooks import small helper modules (`functions*.py`) that are not part of this repository.

**Contact:** [LinkedIn](https://www.linkedin.com/in/yalcin-keles/)
