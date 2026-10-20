# 03 — Predicting building energy use and CO₂ emissions

**Question:** the City of Seattle aims for carbon neutrality by 2050. Annual energy readings are expensive, so can we predict a non-residential building's **CO₂ emissions** and **energy use** from its structural data alone? And is the ENERGY STAR Score worth collecting?

**Data:** [Seattle Building Energy Benchmarking 2015–2016](https://data.seattle.gov/dataset/2016-Building-Energy-Benchmarking/2bpz-gwpy).

## Approach
1. **Data preparation:** merging two years, selecting non-residential buildings, removing outliers and leakage variables (anything that is itself a reading), encoding usage types, log-transforming skewed targets, PCA to study correlations.
2. **Modelling, compared on R² and RMSE:** Dummy, Linear Regression, Kernel Ridge, Random Forest, Gradient Boosting, SVR, KNN, XGBoost.
3. **Optimisation:** hyperparameter search with **Hyperopt** and **Optuna**, cross-validation.
4. **Interpretation:** permutation importance, **SHAP** and **LIME** to understand which building characteristics drive emissions.
5. **ENERGY STAR Score:** impact of adding it as a feature.

## Results
| Target | Best model | R² (test) |
|--------|-----------|-----------|
| CO₂ emissions (log) | XGBoost (tuned) | ≈ 0.81 |
| Site energy use (log) | Gradient Boosting (tuned) | ≈ 0.82 |
| Baseline | Dummy regressor | ≈ 0 |

## Why it matters
Choosing the right variables (and excluding the ones that would leak the answer) is a data-governance question as much as a modelling one. Sustainability reporting is also a growing need for industrial companies.

**Stack:** pandas, statsmodels, scikit-learn, XGBoost, Hyperopt, Optuna, SHAP, LIME
