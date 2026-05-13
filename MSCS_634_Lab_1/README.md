# MSCS_634_Lab_1

## Purpose
This lab applies data visualization, data preprocessing, and statistical analysis techniques using Jupyter Notebook. The dataset used in this lab is a product sales dataset that includes sales records, product categories, regions, marketing spend, customer ratings, and revenue.

## Files Included
- `MSCS_634_Lab_1.ipynb` - Main Jupyter Notebook for the lab
- `product_sales_data.csv` - Dataset used in the notebook
- `/screenshots` - Folder where required screenshots should be saved

## Key Insights
- Product revenue varies across categories, helping identify stronger and weaker product performers.
- Sales revenue distribution shows common revenue ranges and highlights possible outliers.
- Missing values were handled using mean replacement for numeric columns.
- IQR was used to detect and remove revenue outliers.
- Data reduction was performed through sampling and column elimination.
- Min-Max scaling was applied to normalize numeric fields.
- Sales revenue was discretized into Low, Medium, and High categories.
- Correlation analysis was used to examine relationships among numeric variables.

## Challenges and Decisions
One decision made in this lab was to use a created product sales dataset instead of downloading an external dataset. This made it easier to intentionally include missing values and outliers so that preprocessing techniques could be clearly demonstrated. Mean replacement was selected for missing numeric values because the dataset is numerical and suitable for basic statistical cleaning. IQR was selected for outlier detection because it is easy to interpret and works well for identifying extreme values in skewed data.

## Screenshot Checklist
All the screenshots are in the `/screenshots` folder
