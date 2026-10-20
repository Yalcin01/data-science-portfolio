# 02 — Big data image pipeline on AWS with PySpark

**Question:** an agri-tech start-up wants to recognise fruits from photos. The image volume will grow quickly, so the first processing pipeline has to scale in the cloud.

**Data:** [Fruits-360](https://www.kaggle.com/datasets/moltean/fruits) — images of fruits and vegetables across many categories.

## Approach
1. **Cloud set-up:** images stored in an **AWS S3** bucket, processing run on an **EC2** instance with a Spark session.
2. **Feature extraction:** images read directly from S3 and passed through **VGG16** (transfer learning, ImageNet weights, no top layer) to get feature vectors.
3. **Distributed processing:** features loaded into a **PySpark** DataFrame, standardised and reduced with Spark ML **PCA** (≈ 90 % of the variance kept).
4. **Output:** the reduced dataset written back to S3 as CSV, then a first **K-Means** clustering (Spark ML) evaluated with the silhouette score.

## Why it matters
This is the data-engineering side of AI: storage, distributed compute and a pipeline that can scale, not only a model on a laptop.

**Stack:** PySpark (SQL, ML), AWS S3 & EC2, boto3, TensorFlow/Keras (VGG16), Pillow
