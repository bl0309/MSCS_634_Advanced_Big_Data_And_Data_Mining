# MSCS 634 Lab 3: Clustering Analysis Using K-Means and K-Medoids

## Purpose
This lab applies K-Means and K-Medoids clustering to the Wine dataset from `sklearn`. The goal is to compare how the two clustering algorithms group standardized wine-chemistry records and evaluate the clusters using Silhouette Score and Adjusted Rand Index (ARI).

## Files
- `MSCS_634_Lab_3.ipynb`: Jupyter Notebook containing dataset exploration, standardization, clustering models, metrics, PCA visualizations, and interpretation.
- `requirements.txt`: Python dependencies used for the notebook.
- `screenshots/`: PNG images of the notebook visualizations.

## Screenshot Guide
### Plots
- `screenshots/01-actual-wine-classes-pca.png`: PCA scatter plot colored by actual Wine class labels.
- `screenshots/02-kmeans-vs-kmedoids-cluster-comparison.png`: Side-by-side PCA scatter plots for K-Means and K-Medoids clusters with centroids/medoids marked.
- `screenshots/03-clustering-metric-comparison.png`: Bar chart comparing Silhouette Score and Adjusted Rand Index for both algorithms.

### Tables
- `screenshots/tables/01-wine-dataset-preview.png`: First five rows of the Wine dataset with target and class labels.
- `screenshots/tables/02-feature-summary-statistics.png`: Mean, standard deviation, minimum, and maximum for original features.
- `screenshots/tables/03-class-distribution.png`: Count of records in each Wine class.
- `screenshots/tables/04-standardized-feature-summary.png`: Summary of z-score standardized features.
- `screenshots/tables/05-kmeans-metrics.png`: K-Means Silhouette Score and ARI.
- `screenshots/tables/06-kmedoids-metrics.png`: K-Medoids Silhouette Score and ARI.
- `screenshots/tables/07-algorithm-metric-comparison-table.png`: Side-by-side metric comparison for K-Means and K-Medoids.
- `screenshots/tables/08-kmeans-clusters-vs-actual-classes.png`: K-Means cluster assignments compared with actual classes.
- `screenshots/tables/09-kmedoids-clusters-vs-actual-classes.png`: K-Medoids cluster assignments compared with actual classes.

## Requirement Coverage
- Created a Jupyter Notebook with name, course title, and lab assignment title.
- Loaded the Wine dataset from `sklearn`.
- Performed data exploration for feature details and class distribution.
- Standardized the dataset using z-score normalization.
- Implemented K-Means with `k=3`.
- Calculated K-Means Silhouette Score and Adjusted Rand Index.
- Implemented K-Medoids with `k=3`.
- Calculated K-Medoids Silhouette Score and Adjusted Rand Index.
- Created side-by-side scatter plots for K-Means and K-Medoids clusters.
- Marked K-Means centroids and K-Medoids medoids on the plots.
- Compared the algorithms and explained when each may be preferable.

## Methods
- The Wine dataset was loaded from `sklearn.datasets.load_wine`.
- The 13 numeric features were standardized using z-score normalization with `StandardScaler`.
- K-Means was implemented with `k=3`, matching the three known wine classes.
- K-Medoids was implemented with `k=3` using a compact PAM-style routine based on pairwise Euclidean distances.
- PCA was used only for two-dimensional visualization. Metrics were calculated on the full standardized feature set.
- Additional visual analysis was included with an actual-class PCA reference plot and a metric comparison bar chart.

## Key Insights
- K-Means produced the stronger clustering results, with a Silhouette Score of `0.285` and an ARI of `0.897`.
- K-Medoids produced a Silhouette Score of `0.268` and an ARI of `0.741`.
- K-Means achieved the higher Silhouette Score, meaning its clusters were slightly more cohesive and better separated.
- K-Means also achieved the higher ARI, meaning its cluster assignments aligned more closely with the actual wine class labels.
- K-Medoids used actual observations as medoids, which can be helpful for robustness and interpretability, but it produced more overlap between two wine groups in this experiment.
- The PCA visualization showed that K-Means formed more compact groups around centroids, while K-Medoids had less separation between clusters.

## Challenges and Decisions
- Standardization was necessary because the Wine features use very different numeric ranges. Without scaling, features with larger values, such as `proline`, would dominate distance calculations.
- Core `scikit-learn` does not include a K-Medoids estimator, so a simple PAM-style implementation was added directly in the notebook instead of requiring an extra package.
- PCA was used for visualization because the original dataset has 13 features and cannot be directly plotted in two dimensions.

## Run the Notebook
```bash
cd MSCS_634_Lab_3
pip install -r requirements.txt
jupyter notebook MSCS_634_Lab_3.ipynb
```

If the notebook shows a missing package error, install the requirements in the Python environment used by Jupyter.
