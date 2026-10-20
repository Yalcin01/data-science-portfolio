# 04 — Automatic product classification from text and images

**Question:** an e-commerce marketplace wants to automate the categorisation of products uploaded by sellers. Is it feasible from the product description and photo?

**Data:** 1,050 products from the Flipkart marketplace, 7 categories, with descriptions and images.

## Approach
**Text (NLP)**
- Cleaning with regex, tokenisation, stopwords, lemmatisation (NLTK)
- Bag-of-words / **TF-IDF**, dimensionality reduction with **Truncated SVD**, then **PCA, UMAP and t-SNE**
- K-Means clustering compared with the real categories using the **Adjusted Rand Index (ARI)**

**Images (computer vision)**
- Classical approach: **SIFT** descriptors + bag of visual words (MiniBatchKMeans)
- **Transfer learning** with **VGG16** and **ResNet50** as feature extractors, then t-SNE / UMAP + K-Means
- **Supervised** fine-tuning of ResNet50 with data augmentation, early stopping, and analysis of misclassified images

## Results
| Method | ARI vs. real categories |
|--------|------------------------|
| SIFT (images) | 0.04 |
| ResNet50 / VGG16 features (images) | ≈ 0.32–0.34 |
| TF-IDF + t-SNE (text) | ≈ 0.46 |
| Supervised ResNet50 (validation) | ≈ 85 % accuracy (89/105) |

## Why it matters
The project shows the path from "is it feasible?" (unsupervised exploration) to a working supervised model, and why modern pre-trained models outperform hand-crafted features.

**Stack:** NLTK, scikit-learn, UMAP, OpenCV (SIFT), TensorFlow/Keras (VGG16, ResNet50)
