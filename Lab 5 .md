# Lab 5 - Clustering with DBSCAN and Hierarchical Clustering

## Student Information
**Name:** Vishnu Mallam  
**Course Title:** Advanced Big Data and Data Mining  
**Lab Assignment Title:** Lab 5 - Clustering with DBSCAN and Hierarchical Clustering  
**Instructor:** [Insert Instructor Name]  
**Date:** [Insert Date of Submission]

---

## Purpose

The objective of this lab is to develop a practical understanding of unsupervised machine learning techniques by implementing and evaluating two clustering algorithms: **Hierarchical Clustering** and **DBSCAN** (Density-Based Spatial Clustering of Applications with Noise). The lab uses the Wine dataset to demonstrate how these techniques can uncover natural groupings in data, and how parameter choices impact clustering performance and interpretation.

Through visualizations, metrics, and hands-on experimentation, this lab aims to reinforce concepts such as distance metrics, linkage methods, noise detection, and cluster evaluation. This experience prepares students to apply clustering methods to real-world scenarios such as customer segmentation, anomaly detection, and bioinformatics.

---

## Dataset Description

- **Dataset Used:** Wine dataset from `sklearn.datasets`
- **Source:** UCI Machine Learning Repository (via scikit-learn)
- **Instances:** 178 wine samples
- **Features:** 13 continuous variables (e.g., alcohol content, flavonoids, phenols, etc.)
- **Target:** 3 distinct wine cultivars (used only for evaluation, not for training)

The dataset contains chemical analysis of wines grown in the same region in Italy but derived from three different cultivars. Although clustering is unsupervised, the target class is used to compute evaluation metrics like homogeneity and completeness.

---

## Methodology

The lab followed a structured four-step approach:

### Step 1: Data Preparation and Exploration
- Loaded the dataset using `load_wine()` from `sklearn`.
- Displayed initial rows, column information, and summary statistics using `pandas`.
- Verified absence of missing values.
- Standardized all features using `StandardScaler` to normalize the scale of attributes.

### Step 2: Hierarchical Clustering
- Used `AgglomerativeClustering` from `sklearn.cluster` for clustering.
- Applied different values of `n_clusters` (2, 3, and 4) to assess behavior and interpretability.
- Visualized results using scatter plots with Seaborn.
- Generated a dendrogram using `scipy.cluster.hierarchy` to determine the optimal number of clusters.
- Used the Ward linkage method for clustering.

### Step 3: DBSCAN Clustering
- Implemented `DBSCAN` with parameter values `eps=1.5` and `min_samples=5`.
- Visualized cluster formation and noise detection.
- Evaluated clustering performance using the following metrics:
  - Silhouette Score
  - Homogeneity Score
  - Completeness Score

### Step 4: Analysis and Interpretation
- Compared clustering structures and outputs from both methods.
- Discussed the impact of parameters on clustering outcomes.
- Identified noise points, cluster shape handling, and algorithm robustness.

---

## Key Findings

### Hierarchical Clustering:
- Produced consistent clustering outcomes when the number of clusters was chosen appropriately (e.g., 3).
- Provided a comprehensive hierarchical structure via dendrogram.
- Easy to interpret and effective for well-separated, globular clusters.
- Less robust to noise and outliers due to reliance on distance metrics.

### DBSCAN:
- Successfully detected noise points and arbitrarily shaped clusters.
- Did not require pre-specifying the number of clusters.
- Sensitivity to `eps` and `min_samples` required manual tuning and experimentation.
- More robust to outliers and effective for discovering dense clusters.

---

## Evaluation Metrics

To quantitatively assess clustering results:

- **Silhouette Score:** Measures how similar an object is to its own cluster versus other clusters. Higher values indicate better-defined clusters.
- **Homogeneity Score:** Indicates whether each cluster contains only members of a single class.
- **Completeness Score:** Indicates whether all members of a given class are assigned to the same cluster.

These metrics were especially useful in comparing DBSCAN and Hierarchical Clustering against the known wine class labels, although the algorithms were trained without access to this target information.

---

## Challenges and Decisions

- **DBSCAN Parameter Tuning:** Selecting appropriate `eps` and `min_samples` was challenging and required iterative testing to avoid over-clustering or classifying too many points as noise.
- **Cluster Visualization:** Since the dataset is multi-dimensional, visualizations were limited to the first two principal components (or scaled feature dimensions) for simplicity.
- **Dendrogram Interpretation:** Identifying a cut-off threshold for the number of clusters in the dendrogram involved a balance between over-segmentation and under-segmentation.

These decisions directly impacted the clarity and effectiveness of the clustering results and highlighted the importance of preprocessing and parameter selection.

---

## Files Included

- `Lab5_Clustering_Wine.ipynb`: Jupyter notebook containing complete Python code, visualizations, and metric evaluations for both Hierarchical Clustering and DBSCAN.
- `README.md`: This documentation file summarizing the objectives, methods, findings, and conclusions from the lab.

---

## Conclusion

This lab provided hands-on experience with two fundamental clustering techniques and highlighted their comparative strengths and weaknesses. 

- **Hierarchical Clustering** was found to be intuitive and informative, especially when an approximate number of clusters is known or can be inferred visually through a dendrogram.
- **DBSCAN** was advantageous for identifying clusters with arbitrary shapes and for filtering out noise, making it useful in more complex or noisy datasets.

Both methods emphasized the need for proper preprocessing, domain knowledge for parameter selection, and the use of evaluation metrics for meaningful analysis. This lab has strengthened the understanding of unsupervised learning and its applications in data mining and analytics.

---
