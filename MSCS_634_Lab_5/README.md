# MSCS 634 Lab 5: Hierarchical and DBSCAN Clustering

## Purpose
This lab applies Hierarchical Clustering and DBSCAN Clustering to the Wine dataset from `sklearn.datasets`. The goal is to compare how each clustering method groups standardized wine-chemistry records and to evaluate cluster quality using Silhouette Score, Homogeneity Score, and Completeness Score.

## Files
- `MSCS_634_Lab_5.ipynb`: Jupyter Notebook containing data preparation, hierarchical clustering, DBSCAN clustering, metrics, visualizations, dendrogram analysis, and interpretation.
- `requirements.txt`: Python dependencies used for the notebook.
- `screenshots/`: PNG images of notebook plots and tables.

## Screenshot Guide
### Plots
- `screenshots/01-actual-wine-classes-pca.png`: PCA scatter plot colored by actual Wine class labels.
- `screenshots/02-hierarchical-clusters-by-n-clusters.png`: Hierarchical clustering visualizations for different `n_clusters` values.
- `screenshots/03-hierarchical-dendrogram.png`: Truncated Ward-linkage dendrogram.
- `screenshots/04-dbscan-parameter-cluster-examples.png`: DBSCAN cluster examples with noise points highlighted.
- `screenshots/05-clustering-metric-comparison.png`: Metric comparison between the selected hierarchical and DBSCAN results.

### Tables
- `screenshots/tables/01-wine-dataset-preview.png`: First five rows of the Wine dataset.
- `screenshots/tables/02-feature-summary-statistics.png`: Feature summary statistics from `.describe()`.
- `screenshots/tables/03-class-distribution.png`: Count of records in each Wine class.
- `screenshots/tables/04-standardized-feature-summary.png`: Summary of standardized features.
- `screenshots/tables/05-hierarchical-clustering-metrics.png`: Metrics for different hierarchical `n_clusters` values.
- `screenshots/tables/06-dbscan-parameter-metrics.png`: Metrics for tested DBSCAN `eps` and `min_samples` values.
- `screenshots/tables/07-final-clustering-comparison.png`: Final comparison between hierarchical clustering and DBSCAN.

## Requirement Coverage
- Created a Jupyter Notebook with name, course title, and lab assignment title.
- Loaded the Wine dataset from `sklearn.datasets`.
- Examined the dataset with `.head()`, `.info()`, and `.describe()`.
- Standardized the dataset features before clustering.
- Applied Agglomerative Hierarchical Clustering.
- Tested multiple values of `n_clusters`.
- Visualized hierarchical clusters using PCA scatter plots.
- Generated and interpreted a dendrogram.
- Applied DBSCAN clustering.
- Tested multiple `eps` and `min_samples` parameter combinations.
- Visualized DBSCAN clusters and highlighted noise points.
- Computed Silhouette Score, Homogeneity Score, and Completeness Score.
- Compared Hierarchical and DBSCAN clustering results.
- Discussed parameter effects, strengths, and weaknesses.

## Methods
- The Wine dataset was loaded using `load_wine`.
- The 13 numeric features were standardized with `StandardScaler`.
- PCA was used only for two-dimensional visualization; clustering and metrics used the full standardized feature set.
- Agglomerative Hierarchical Clustering used Ward linkage and tested `n_clusters` values from 2 through 6.
- DBSCAN was tested with several `eps` and `min_samples` combinations to show how density parameters affect cluster formation and noise detection.

## Key Insights
- Hierarchical clustering performed best for this dataset when `n_clusters=3`.
- The best hierarchical model had Silhouette Score `0.277`, Homogeneity Score `0.790`, and Completeness Score `0.783`.
- The dendrogram supported a small number of major cluster groups by showing larger linkage-distance gaps near the top of the hierarchy.
- DBSCAN was highly sensitive to `eps` and `min_samples`. Small `eps` values classified many observations as noise, while larger `eps` values often merged clusters together.
- The selected DBSCAN setting, `eps=2.5` and `min_samples=10`, produced Silhouette Score `0.204`, Homogeneity Score `0.504`, and Completeness Score `0.560`.
- Hierarchical clustering aligned better with the known three-class Wine structure, while DBSCAN was more useful for demonstrating noise detection and density sensitivity.
- The lower DBSCAN homogeneity and completeness scores show that its density-based clusters did not map cleanly onto the three known Wine classes.

## Challenges and Decisions
- Standardization was necessary because Wine features use different numeric ranges.
- A PCA projection was used for scatter plots because the Wine dataset has 13 features.
- DBSCAN did not naturally recover three strong clusters for this dataset. This was treated as an important finding rather than a failure, because it shows that algorithm assumptions matter.
- A truncated dendrogram was used to keep the hierarchical visualization readable.
- The notebook explains each metric in context: Silhouette Score evaluates cluster separation/cohesion, while Homogeneity and Completeness compare cluster assignments with the known class labels.
- This lab includes a requirement checklist, direct interpretation after major outputs, and saved screenshots for plots and tables.

## Run the Notebook
```bash
cd MSCS_634_Lab_5
pip install -r requirements.txt
jupyter notebook MSCS_634_Lab_5.ipynb
```

If the notebook shows a missing package error, install the requirements in the Python environment used by Jupyter.
