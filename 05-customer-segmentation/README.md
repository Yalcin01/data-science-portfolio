# 05 — Customer segmentation for an e-commerce platform

**Question:** Olist, a Brazilian marketplace, wants actionable customer segments for its marketing team, and to know how often the segmentation should be updated.

**Data:** [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — ~100k orders across 9 relational tables (customers, orders, payments, reviews, products, sellers, geolocation).

## Approach
1. **`01_exploratory_analysis`** — joining the 9 tables, exploring review scores, payment methods, purchase volumes over time and satisfaction by product category; building **RFM** features (Recency, Frequency, Monetary) enriched with satisfaction and delivery delay.
2. **`02_clustering`** — **K-Means** and **DBSCAN** on two feature scenarios, elbow and silhouette analysis, visualisation with **PCA** and **t-SNE**, segment profiling with boxplots.
3. **Maintenance:** the data is split into time periods and segments are compared with the **Adjusted Rand Index**, to see how quickly they drift and how often the model should be retrained.

## Results
- 6 segments with K-Means (silhouette ≈ 0.45), profiled on recency, frequency, spend, satisfaction and delivery delay.
- A time-based stability check to frame the maintenance of the segmentation.

**Stack:** pandas, scikit-learn, Yellowbrick, seaborn
