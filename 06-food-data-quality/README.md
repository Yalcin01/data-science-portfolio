# 06 — Data quality on a large open dataset (Open Food Facts)

**Question:** a public-health agency wants to build an application on the Open Food Facts database. Is the data clean and complete enough to be used?

**Data:** [Open Food Facts](https://world.openfoodfacts.org/data) — ~820k products, crowd-sourced; 52 columns kept for the study.

## Approach
1. **Column selection:** keeping the variables relevant to nutrition and the Nutri-Score, dropping columns with too many missing values.
2. **Deduplication:** grouping records on product code, then **fuzzy matching** (`fuzzywuzzy`) to detect near-duplicate product names and brands.
3. **Outliers:** detection and treatment of aberrant nutrient values.
4. **Imputation:** missing Nutri-Scores estimated with **KNN** and checked against a linear model (OLS, R² ≈ 0.60).
5. **Exploratory analysis:** univariate and multivariate analysis, correlations and PCA.

## Why it matters
Most of the value of a data project depends on the reliability of the source. This project applies the same reflexes I used as a data steward: profiling, duplicates, business rules for validity, and documented imputation choices.

**Stack:** pandas, NumPy, statsmodels, scikit-learn, fuzzywuzzy, seaborn
