# MSCS 634 Lab 4: Regression Analysis and Regularization

## Purpose
This lab applies regression techniques to the Diabetes dataset from `sklearn.datasets`. The goal is to compare Simple Linear Regression, Multiple Linear Regression, Polynomial Regression, Ridge Regression, and Lasso Regression using consistent evaluation metrics and visual analysis.

## Files
- `MSCS_634_Lab_4.ipynb`: Jupyter Notebook containing data preparation, regression models, metrics, visualizations, and interpretation.
- `requirements.txt`: Python dependencies used for the notebook.
- `screenshots/`: PNG images of notebook plots and tables.

## Screenshot Guide
### Plots
- `screenshots/01-target-distribution.png`: Histogram of the disease progression target.
- `screenshots/02-simple-linear-regression-bmi.png`: Simple Linear Regression line for BMI versus disease progression.
- `screenshots/03-multiple-regression-predicted-vs-actual.png`: Multiple Regression predicted values versus actual values.
- `screenshots/04-polynomial-train-test-rmse.png`: Polynomial degree comparison showing train and test RMSE.
- `screenshots/05-polynomial-degree-2-predicted-vs-actual.png`: Degree 2 Polynomial Regression predicted versus actual values.
- `screenshots/06-regularization-alpha-vs-test-rmse.png`: Ridge and Lasso test RMSE across alpha values.
- `screenshots/07-ridge-vs-lasso-predicted-vs-actual.png`: Best Ridge and best Lasso predicted versus actual values.
- `screenshots/08-model-comparison-rmse-r2.png`: Final model comparison using test RMSE and R-squared.
- `screenshots/09-best-model-residual-plot.png`: Residual plot for the best-performing model.

### Tables
- `screenshots/tables/01-diabetes-dataset-preview.png`: First five rows of the Diabetes dataset.
- `screenshots/tables/02-missing-values.png`: Missing-value count for each column.
- `screenshots/tables/03-feature-summary-statistics.png`: Mean, standard deviation, minimum, and maximum for features.
- `screenshots/tables/04-target-summary-statistics.png`: Summary statistics for the disease progression target.
- `screenshots/tables/05-simple-linear-regression-metrics.png`: Simple Linear Regression metrics.
- `screenshots/tables/06-multiple-regression-metrics.png`: Multiple Regression metrics.
- `screenshots/tables/07-polynomial-degree-comparison.png`: Polynomial Regression metrics by degree.
- `screenshots/tables/08-ridge-alpha-comparison.png`: Ridge Regression metrics by alpha.
- `screenshots/tables/09-lasso-alpha-comparison.png`: Lasso Regression metrics by alpha.
- `screenshots/tables/10-ridge-lasso-coefficients.png`: Best Ridge and Lasso coefficient comparison.
- `screenshots/tables/11-final-model-comparison.png`: Final model comparison table.

## Requirement Coverage
- Created a Jupyter Notebook with name, course title, and lab assignment title.
- Loaded the Diabetes dataset from `sklearn.datasets`.
- Explored feature details, target values, missing values, and data distribution.
- Implemented Simple Linear Regression using `bmi` as the independent variable.
- Split the data into training and testing sets.
- Evaluated each model with MAE, MSE, RMSE, and R-squared.
- Implemented Multiple Linear Regression using all independent variables.
- Implemented Polynomial Regression and compared degrees 1 through 4.
- Demonstrated overfitting through polynomial train-test RMSE trends.
- Implemented Ridge Regression and Lasso Regression across multiple alpha values.
- Compared regularized models with earlier regression models.
- Visualized predictions, residuals, regularization behavior, and model comparison results.

## Methods
- The Diabetes dataset was loaded using `load_diabetes`.
- The same 80/20 train-test split with `random_state=42` was used across all models.
- Simple Linear Regression used only the `bmi` feature.
- Multiple Linear Regression used all 10 features.
- Polynomial Regression used all features expanded to degrees 1, 2, 3, and 4.
- Ridge and Lasso were evaluated with alpha values `0.001`, `0.01`, `0.1`, `1`, `10`, and `100`.
- Model performance was compared using MAE, MSE, RMSE, and R-squared.

## Key Insights
- Simple Linear Regression using BMI was useful as a baseline, but it had the weakest performance with test RMSE `63.732` and R-squared `0.233`.
- Multiple Linear Regression improved performance by using the full feature set, reaching test RMSE `53.853` and R-squared `0.453`.
- Polynomial Regression showed clear overfitting at higher degrees. Degree 3 and degree 4 had very low training error but much worse test error.
- Ridge Regression slightly improved test RMSE by shrinking coefficients and reducing variance. The best Ridge result used alpha `100` with test RMSE `53.462`.
- Lasso Regression with alpha `1.0` produced the best test RMSE in this split at `53.147` and R-squared `0.467`.
- The Diabetes dataset contains meaningful linear signal, but the moderate R-squared values show that disease progression is not fully explained by these features alone.

## Challenges and Decisions
- The dataset had no missing values, so no imputation was required.
- BMI was selected for Simple Linear Regression because it is interpretable and relevant to diabetes progression.
- Polynomial degrees above 2 were included specifically to demonstrate overfitting.
- Ridge and Lasso were tested across several alpha values to show how regularization strength affects model behavior.
- This lab includes a requirement checklist, direct interpretation after major outputs, and saved screenshots for plots and tables.

## Run the Notebook
```bash
cd MSCS_634_Lab_4
pip install -r requirements.txt
jupyter notebook MSCS_634_Lab_4.ipynb
```

If the notebook shows a missing package error, install the requirements in the Python environment used by Jupyter.
