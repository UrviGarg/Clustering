# Clustering
# Comparative Performance Study of Clustering Algorithms on the Iris Dataset

## Overview

This project investigates the performance of three popular clustering algorithms - K-Means, Hierarchical Clustering (Agglomerative), and Mean Shift - on the classic Iris dataset. The study compares their effectiveness under different pre-processing techniques: No Data Processing, Normalization (StandardScaler), Power Transform, Principal Component Analysis (PCA), Transform followed by Normalization (T+N), and Transform followed by PCA (T+PCA). The performance of the algorithms is evaluated using three common internal clustering evaluation metrics: Silhouette score, Calinski-Harabasz index, and Davies-Bouldin index.

The goal is to understand how different pre-processing steps influence the performance of these clustering algorithms and to identify which combinations work best for the Iris dataset based on the chosen evaluation metrics.

## Dataset

The Iris dataset is used for this study. It contains measurements of sepal length, sepal width, petal length, and petal width for 150 samples of three species of Iris (Iris setosa, Iris versicolor, and Iris virginica). While the species labels are available in the dataset, this study focuses on unsupervised clustering and does not use these labels directly for the clustering process itself, but they can be used for qualitative analysis or validation if needed.

The `iris.data` file from the UCI Machine Learning Repository was used. It contains comma-separated values representing the features and the class label.

## Methodology

The following steps were performed:

1.  **Data Loading:** The Iris dataset was loaded using pandas. The feature columns (sepal length, sepal width, petal length, petal width) were separated from the target (species).
2.  **Pre-processing:** Six different pre-processing techniques were applied to the feature data:
    * **No Data Processing:** The original data was used directly.
    * **Normalization (StandardScaler):** Features were scaled to have zero mean and unit variance.
    * **Transform (PowerTransformer):** A power transform was applied to make the data more Gaussian-like.
    * **PCA (Principal Component Analysis):** Dimensionality reduction was performed to retain 95% of the variance.
    * **Transform + Normalization (T+N):** Power transform followed by StandardScaler.
    * **Transform + PCA (T+PCA):** Power transform followed by PCA (retaining 95% variance).
3.  **Clustering:** Three clustering algorithms were applied to each pre-processed version of the data:
    * **K-Means:** Run with a fixed number of clusters (3, 4, and 5).
    * **Hierarchical Clustering (Agglomerative):** Run with a fixed number of clusters (3, 4, and 5).
    * **Mean Shift:** The number of clusters was automatically estimated by the algorithm.
4.  **Evaluation:** The performance of each clustering result was evaluated using:
    * **Silhouette Score:** Measures how well each data point fits into its assigned cluster. Higher values indicate better clustering.
    * **Calinski-Harabasz Index:** Measures the ratio of between-cluster variance to within-cluster variance. Higher values indicate better-defined clusters.
    * **Davies-Bouldin Index:** Measures the average similarity ratio of each cluster with its most similar cluster. Lower values indicate better clustering.
5.  **Results Analysis and Visualization:** The evaluation metrics were collected and organized in a pandas DataFrame. Bar plots and line plots were generated to compare the performance of different algorithms under various pre-processing techniques and with different numbers of clusters (where applicable).

## Results Summary

To provide a clearer comparison, the results are presented in separate tables for each clustering algorithm:

### K-Means Clustering Results

| Preprocessor        | n\_clusters | Silhouette | Calinski-Harabasz | Davies-Bouldin |
| :------------------ | :---------- | :--------- | :---------------- | :------------- |
| No Data Processing  | 3           | 0.553      | 560.40            | 0.662          |
| No Data Processing  | 4           | 0.498      | 529.40            | 0.781          |
| No Data Processing  | 5           | 0.489      | 494.09            | 0.806          |
| Normalization       | 3           | 0.459      | 239.34            | 0.835          |
| Normalization       | 4           | 0.385      | 206.09            | 0.873          |
| Normalization       | 5           | 0.347      | 201.99            | 0.941          |
| Transform           | 3           | 0.456      | 244.42            | 0.843          |
| Transform           | 4           | 0.419      | 212.41            | 0.929          |
| Transform           | 5           | 0.352      | 208.95            | 0.950          |
| PCA                 | 3           | 0.598      | 692.40            | 0.565          |
| PCA                 | 4           | 0.558      | 717.79            | 0.613          |
| PCA                 | 5           | 0.553      | 682.40            | 0.639          |
| T+N                 | 3           | 0.456      | 244.42            | 0.843          |
| T+N                 | 4           | 0.419      | 212.41            | 0.929          |
| T+N                 | 5           | 0.352      | 208.95            | 0.950          |
| T+PCA               | 3           | 0.504      | 295.07            | 0.731          |
| T+PCA               | 4           | 0.482      | 268.98            | 0.747          |
| T+PCA               | 5           | 0.422      | 282.66            | 0.777          |

### Hierarchical Clustering Results

| Preprocessor        | n\_clusters | Silhouette | Calinski-Harabasz | Davies-Bouldin |
| :------------------ | :---------- | :--------- | :---------------- | :------------- |
| No Data Processing  | 3           | 0.554      | 556.84            | 0.657          |
| No Data Processing  | 4           | 0.489      | 513.77            | 0.796          |
| No Data Processing  | 5           | 0.484      | 487.07            | 0.821          |
| Normalization       | 3           | 0.446      | 220.26            | 0.806          |
| Normalization       | 4           | 0.399      | 198.73            | 0.981          |
| Normalization       | 5           | 0.355      | 194.96            | 0.947          |
| Transform           | 3           | 0.478      | 223.37            | 0.745          |
| Transform           | 4           | 0.426      | 211.66            | 0.904          |
| Transform           | 5           | 0.361      | 202.01            | 0.911          |
| PCA                 | 3           | 0.598      | 687.37            | 0.561          |
| PCA                 | 4           | 0.541      | 672.57            | 0.655          |
| PCA                 | 5           | 0.549      | 664.10            | 0.653          |
| T+N                 | 3           | 0.478      | 223.37            | 0.745          |
| T+N                 | 4           | 0.426      | 211.66            | 0.904          |
| T+N                 | 5           | 0.361      | 202.01            | 0.911          |
| T+PCA               | 3           | 0.522      | 254.67            | 0.638          |
| T+PCA               | 4           | 0.483      | 264.07            | 0.715          |
| T+PCA               | 5           | 0.428      | 266.57            | 0.732          |

### Mean Shift Clustering Results

| Preprocessor        | n\_clusters | Silhouette | Calinski-Harabasz | Davies-Bouldin |
| :------------------ | :---------- | :--------- | :---------------- | :------------- |
| No Data Processing  | 2           | 0.685      | 508.88            | 0.389          |
| Normalization       | 2           | 0.580      | 248.90            | 0.598          |
| Transform           | 2           | 0.586      | 257.34            | 0.590          |
| PCA                 | 2           | 0.710      | 564.90            | 0.356          |
| T+N                 | 2           | 0.586      | 257.34            | 0.590          |
| T+PCA               | 2           | 0.618      | 288.74            | 0.539          |

**Key Observations:**

* **K-Means:**
    * PCA pre-processing consistently yielded the best Calinski-Harabasz indices, indicating well-separated clusters.
    * Silhouette scores were generally highest with PCA and No Data Processing.
    * Normalization and Transform often resulted in lower performance compared to no pre-processing.
    * Performance varied with the number of clusters, with 3 clusters often showing better Silhouette scores.
* **Hierarchical Clustering:**
    * Similar to K-Means, PCA pre-processing resulted in high Calinski-Harabasz indices.
    * No Data Processing also performed well, especially with 3 clusters.
    * Normalization and Transform tended to decrease performance.
    * The best Silhouette scores were observed with PCA and No Data Processing, with 3 clusters.
* **Mean Shift:**
    * Mean Shift consistently estimated 2 clusters for all pre-processing techniques.
    * PCA pre-processing resulted in the highest Silhouette score and lowest Davies-Bouldin index, suggesting good separation.
    * All pre-processing methods produced relatively low Davies-Bouldin indices compared to K-Means and Hierarchical, indicating that Mean Shift tended to create clusters with better separation.

## Code and Implementation

The code for this study is implemented in a Google Colaboratory notebook (`clustering.ipynb`). The notebook includes:

* Loading and exploration of the Iris dataset.
* Implementation of the pre-processing techniques using scikit-learn.
* Implementation of the clustering algorithms using scikit-learn.
* Calculation of the evaluation metrics using scikit-learn.
* Visualization of the results using matplotlib and seaborn (bar plots and line plots).
* A summary of the findings.

## Usage

To run this analysis:

1.  Open the `clustering.ipynb` file in Google Colaboratory.
2.  Ensure that the `iris.data` file is uploaded to the Colab environment (if it's not already included in the notebook).
3.  Run the cells in the notebook sequentially. The results, tables, and visualizations will be displayed within the notebook.

## Further Work

Possible extensions of this study include:

* Exploring other clustering algorithms (e.g., DBSCAN).
* Experimenting with different parameters for the algorithms and pre-processing techniques (e.g., different `n_components` for PCA).
* Applying different dimensionality reduction techniques (e.g., t-SNE, UMAP).
* Performing external validation by comparing the cluster assignments to the true Iris species labels.
* Analyzing the visual representation of the clusters formed by the different methods in the reduced dimensional space.

## Author

[Urvi Garg]


## Date

April 15, 2025
