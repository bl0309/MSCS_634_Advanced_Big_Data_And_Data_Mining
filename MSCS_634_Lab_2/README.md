# MSCS 634 Lab 2: KNN and Radius Neighbors Classification

## Purpose
This lab evaluates K-Nearest Neighbors (KNN) and Radius Neighbors (RNN) classifiers on the Wine dataset from `sklearn`. The goal is to compare how different neighbor-count and radius parameters affect classification accuracy.

## Files
- `MSCS_634_Lab_2.ipynb`: Jupyter Notebook containing dataset exploration, model training, accuracy tables, plots, and observations.
- `requirements.txt`: Python dependencies used for the notebook.
- `screenshots/`: Output screenshots organized by lab step.

## Screenshot Guide

### Load and Prepare Dataset
- `screenshots/load_prepare_dataset/01-load-wine-dataset-preview-left.png`: Wine dataset loading code and first rows.
- `screenshots/load_prepare_dataset/02-load-wine-dataset-preview-right.png`: Continued preview of the Wine dataset columns.
- `screenshots/load_prepare_dataset/03-feature-summary-statistics.png`: Feature summary statistics including mean, standard deviation, minimum, and maximum.
- `screenshots/load_prepare_dataset/04-class-distribution.png`: Class distribution for the three wine classes.
- `screenshots/load_prepare_dataset/05-train-test-split-class-counts.png`: 80/20 train-test split and class counts.

### KNN
- `screenshots/KNN/knn-accuracy-results.png`: KNN accuracy results for `k=1`, `k=5`, `k=11`, `k=15`, and `k=21`.

### RNN
- `screenshots/RNN/rnn-accuracy-results.png`: Radius Neighbors accuracy results for radius values 350, 400, 450, 500, 550, and 600.

### Compare Results
- `screenshots/compare_results/01-knn-accuracy-trend-plot.png`: KNN accuracy trend plot.
- `screenshots/compare_results/02-rnn-accuracy-trend-plot.png`: Radius Neighbors accuracy trend plot.
- `screenshots/compare_results/03-best-model-comparison-table.png`: Best KNN and RNN model comparison.
- `screenshots/compare_results/04-best-knn-confusion-matrix-classification-report.png`: Confusion matrix and classification report for the best KNN model.

## Key Insights
- KNN produced the stronger results in this experiment. The best KNN accuracy was 0.806, achieved with `k=5`, `k=11`, `k=15`, and `k=21`.
- The `k=1` KNN model scored 0.778, which suggests it was more sensitive to individual nearby samples.
- RNN performed best at radius 350 with an accuracy of 0.722. Accuracy decreased as the radius increased, reaching 0.667 at radius 550 and 600.
- KNN was preferable for this dataset and parameter range because it consistently used a fixed number of nearest neighbors. RNN was more sensitive to radius choice and feature scale.

## Challenges and Decisions
- A stratified 80/20 train-test split was used to preserve the class distribution across the training and testing sets.
- `outlier_label="most_frequent"` was used for Radius Neighbors so predictions remain valid if any test sample has no neighbors inside a selected radius.
- Feature scaling was not applied because the assigned RNN radius values are based on the original Wine feature ranges. If scaling is used, radius values should be retuned.

## Run the Notebook
```bash
cd MSCS_634_Lab_2
pip install -r requirements.txt
jupyter notebook MSCS_634_Lab_2.ipynb
```

If the notebook shows `ModuleNotFoundError: No module named 'sklearn'`, select the project kernel from the notebook menu:

`Kernel` -> `Change Kernel` -> `Python (.venv MSCS 634)`
