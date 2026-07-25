# MSCS 634 Project Deliverable 2: Regression Modeling and Performance Evaluation

## Purpose
This deliverable builds regression models to predict invoice revenue using engineered invoice-level features from the Online Retail dataset.

## Dataset
`data/invoice_features.csv` contains invoice-level records derived from cleaned transaction data. The target is `invoice_total`, transformed with `log1p` for modeling because invoice revenue is right-skewed.

## Models
- Multiple Linear Regression
- Ridge Regression
- Random Forest Regression

## Process Rationale
- Invoice-level modeling was used because the target, invoice revenue, belongs to the full order rather than an individual product line.
- `log1p(invoice_total)` was used to reduce the effect of extreme invoice totals and make model error more stable.
- Numeric features were standardized so linear and regularized models were not affected by feature scale.
- `Country` was one-hot encoded because it is categorical and should not be interpreted as an ordered number.
- Cross-validation was included to check whether model performance generalizes beyond a single train-test split.

## Evaluation
Models are evaluated using RMSE, R-squared, and 5-fold cross-validation RMSE. Visualizations compare model performance and predicted versus actual values.

## Model Comparison and Selection
Three regression models were used in this deliverable:
- **Multiple Linear Regression**: used as the baseline model to test whether invoice revenue could be predicted with a simple linear relationship.
- **Ridge Regression**: used as a regularized linear model to reduce coefficient instability and compare whether regularization improved the baseline.
- **Random Forest Regression**: used as a nonlinear model that can capture interactions among quantity, item variety, average price, country, and invoice timing.

Random Forest Regression was selected as the preferred model because it produced the strongest performance. It had the lowest test RMSE (`0.2648`) and the highest test R-squared (`0.9360`). Multiple Linear Regression and Ridge Regression had much higher RMSE values around `0.878` and lower R-squared values around `0.29`. This shows that the nonlinear model explained invoice revenue much better than the linear models.

The reason for choosing Random Forest over the other models is that retail invoice revenue is not purely linear. A customer's order value depends on combined effects between basket size, number of unique items, average unit price, country, and purchase timing. Random Forest can model those interactions more effectively, while Linear Regression and Ridge Regression are still useful as simpler baseline comparisons.

## Key Insights
- Invoice-level feature engineering creates meaningful predictors from transaction-line data.
- Log-transforming invoice totals reduces skew and stabilizes modeling.
- Cross-validation helps evaluate whether model performance generalizes beyond one train-test split.
- Tree-based regression can capture nonlinear relationships among quantity, item variety, average price, timing, and country.
- The main outcome is that engineered invoice features can support revenue prediction, with more flexible models capturing patterns that linear models may miss.

## Visual Artifacts
The notebook outputs were also exported as PNG files for easier review. Chart screenshots are stored in `screenshots/`, and notebook-style table screenshots are stored in `screenshots/tables/`.

Chart screenshots:
- `screenshots/01_regression_model_comparison_rmse.png`
- `screenshots/02_actual_vs_predicted_invoice_revenue.png`

Table screenshots:
- `screenshots/tables/01-invoice-feature-preview.png`
- `screenshots/tables/02-feature-engineered-regression-preview.png`
- `screenshots/tables/03-regression-model-metrics.png`

## Challenges
- Invoice revenue contained extreme values and a right-skewed distribution. This mattered because models trained directly on raw revenue could be overly influenced by a small number of unusually large invoices. The issue was handled by modeling `log1p(invoice_total)`, which reduced skew while preserving the ordering of invoice values.
- The project required predicting invoice-level revenue, but the original retail data was recorded at the transaction-line level. Using individual product lines as the modeling unit would not fully represent total order value. This was handled by using an invoice-level feature table with aggregated predictors such as total quantity, number of unique items, line count, average unit price, country, and invoice timing.
- `Country` is a categorical feature, so it could not be treated as a continuous numeric variable. This was handled with one-hot encoding inside the preprocessing pipeline, allowing the model to use country information without creating a false numeric order.
- Different models have different preprocessing needs. Linear and Ridge Regression are sensitive to feature scale, while Random Forest is less sensitive. The workflow handled this by using a shared `ColumnTransformer` and `Pipeline`, which made preprocessing consistent and reduced the risk of data leakage.
- A single train-test split can give an incomplete picture of model performance. Cross-validation RMSE was included to check whether each model's performance was reasonably stable across different folds of the data.

## Run
```bash
pip install -r requirements.txt
jupyter notebook MSCS_634_ProjectDeliverable_2.ipynb
```
