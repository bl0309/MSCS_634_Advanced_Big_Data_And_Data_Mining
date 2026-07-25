# MSCS 634 Project Deliverable 1: Data Collection, Cleaning, and Exploration

## Purpose
This deliverable prepares and explores the UCI Online Retail dataset for later data mining tasks. The dataset is appropriate because it contains real customer transaction records, 8 original attributes, and far more than 500 records.

## Dataset
- Source: UCI Machine Learning Repository, Online Retail Dataset
- Original rows: 541,909
- Cleaned rows: 392,692
- Original attributes: InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country

## Major Steps
- Loaded and inspected the Online Retail dataset.
- Removed cancelled invoices, missing customer/product records, duplicates, and invalid quantity or price values.
- Added `TotalPrice`, invoice month, day-of-week, and hour features.
- Explored country volume, product frequency, revenue distribution, monthly trend, and numeric correlations.

## Process Rationale
- Cleaning was performed first because invalid transactions would distort revenue, customer behavior, and product frequency patterns.
- `TotalPrice` was engineered because revenue is not directly stored as one column in the raw data.
- Calendar features were created because retail purchasing often changes by month, day, and hour.
- EDA was used to decide how later deliverables should structure the data: invoice-level data for prediction, customer-level data for clustering, and basket-level data for association rules.

## Key Insights
- The United Kingdom dominates transaction volume.
- Product popularity is concentrated among repeat-purchased gift and household items.
- Revenue is right-skewed, so later modeling benefits from aggregation and log transformation.
- Monthly revenue patterns suggest seasonality should be considered in modeling.
- The main outcome of this deliverable is a cleaned and better-understood dataset that can support regression, classification, clustering, and pattern mining.

## Visual Artifacts
The notebook outputs were also exported as PNG files for easier review. Chart screenshots are stored in `screenshots/`, and notebook-style table screenshots are stored in `screenshots/tables/`.

Chart screenshots:
- `screenshots/01_top_10_countries_by_transaction_count.png`
- `screenshots/02_top_15_products_by_frequency.png`
- `screenshots/03_transaction_line_revenue_distribution.png`
- `screenshots/04_monthly_revenue_trend.png`
- `screenshots/05_numeric_feature_correlation_heatmap.png`

Table screenshots:
- `screenshots/tables/01-cleaned-sample-preview.png`
- `screenshots/tables/02-dataframe-info.png`
- `screenshots/tables/03-descriptive-statistics.png`
- `screenshots/tables/04-missing-value-summary.png`
- `screenshots/tables/05-cleaning-validation-summary.png`

## Challenges
- The raw data contained cancelled invoices, missing customer identifiers, duplicate rows, and invalid quantity or price values. These records were problematic because they could inflate or reduce revenue incorrectly, distort product popularity, and create misleading customer behavior patterns. They were handled by removing cancelled invoice numbers, dropping records with missing customer or product information, removing duplicates, and filtering out non-positive quantities and prices.
- Revenue values were highly right-skewed, with many small purchases and a smaller number of much larger purchases. This made it important to examine revenue distribution carefully before later modeling. The issue was handled by using visual inspection during EDA and preparing later deliverables to use invoice-level aggregation and log transformation.
- The raw Excel file was large, which could make the repository difficult to manage and slow to review. To keep the work reproducible and easier to submit, the full dataset was cleaned first, then a representative cleaned sample was included for EDA while derived modeling datasets were saved separately.
- The dataset includes multiple possible units of analysis, such as transaction lines, invoices, customers, and baskets. Using the wrong unit could lead to weak modeling decisions. This was handled by using transaction-line data for EDA and preparing separate invoice-level, customer-level, and basket-level files for later project deliverables.

## Run
```bash
pip install -r requirements.txt
jupyter notebook MSCS_634_ProjectDeliverable_1.ipynb
```
