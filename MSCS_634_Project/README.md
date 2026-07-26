# MSCS 634 Final Project: Advanced Data Mining for Data-Driven Insights and Predictive Modeling

## Purpose
This final project consolidates the complete data mining workflow using the UCI Online Retail dataset. It includes data preparation, exploratory analysis, feature engineering, regression, classification, clustering, association rule mining, recommendations, and ethical considerations.

## Dataset
The UCI Online Retail dataset contains transactional sales records from a UK-based online retailer. It is appropriate for this project because it contains real-world customer purchases, more than 500 records, and 8 original attributes: invoice number, stock code, product description, quantity, invoice date, unit price, customer ID, and country.

The final analysis uses cleaned and derived versions of the dataset:
- `online_retail_cleaned_sample.csv`: cleaned transaction-line sample used for EDA.
- `invoice_features.csv`: invoice-level table used for regression and classification.
- `customer_features.csv`: customer-level table used for clustering.
- `basket_transactions.csv`: invoice-product basket table used for association rule mining.

## Project Steps
- Deliverable 1: Data collection, cleaning, and exploratory data analysis.
- Deliverable 2: Regression modeling for invoice revenue prediction.
- Deliverable 3: Classification, customer clustering, and association rule mining.
- Deliverable 4: Consolidated final notebook, written report, presentation, findings, recommendations, and ethical considerations.

## Process Rationale
- The project uses one dataset but creates multiple analytical views because each data mining method requires a different unit of analysis.
- Transaction-line data is best for EDA and product frequency analysis.
- Invoice-level data is best for revenue prediction and high-value invoice classification.
- Customer-level data is best for segmentation because it summarizes behavior over time.
- Basket-level data is best for association rules because product relationships must be measured within shared transactions.
- Cleaning removed cancelled invoices, missing customer IDs, duplicates, and invalid quantities or prices so that the analysis reflects completed sales behavior.
- Log transformation was used for invoice revenue because retail purchase values are strongly right-skewed.
- Cross-validation and hyperparameter tuning were included to make model comparison more reliable than a single train-test result.

## Major Findings
- Online sales are highly concentrated in the United Kingdom.
- Invoice totals are right-skewed, making log transformation useful for regression.
- Invoice-level features can predict revenue and high-value invoices, especially when nonlinear models are used.
- Customer clustering can support segmentation and marketing strategy.
- Association rules reveal product combinations that can guide cross-selling and recommendations.
- The main outcome is an integrated retail decision-support workflow covering forecasting, prioritization, segmentation, and product recommendation.

## Visualizations Included
The final notebook includes visualizations for:
- Country-level transaction concentration.
- Most frequently purchased products.
- Transaction revenue distribution.
- Monthly revenue trend.
- Correlation heatmap for numeric transaction features.
- Regression model RMSE comparison.
- Actual versus predicted invoice revenue.
- Classification confusion matrix and ROC curve.
- Customer segment PCA scatter plot.
- Association rule confidence versus lift.
- Frequent itemset support comparison.

## Ethical Considerations
Customer identifiers should be protected, models should not unfairly exclude customer groups, and association rules should be treated as correlations rather than proof that one purchase causes another.

## Files
- `MSCS_634_Project.ipynb`: Consolidated final notebook.
- `Final_Project_Report.pdf`: Academic-style written report with title page, abstract, methods, results, tables, figures, ethical considerations, recommendations, limitations, conclusion, and APA-style references.
- `data/`: Derived project datasets.
- `screenshots/`: Supporting visualizations used in the final report.

## Supporting Visualizations
- `screenshots/01-final-revenue-trend.png`: Monthly invoice revenue trend.
- `screenshots/02-top-countries-by-revenue.png`: Top countries by invoice revenue.

## Run
```bash
pip install -r requirements.txt
jupyter notebook MSCS_634_Project.ipynb
```
