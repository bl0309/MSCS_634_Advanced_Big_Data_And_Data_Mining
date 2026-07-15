# MSCS 634 Lab 6: Association Rule Mining with Apriori and FP-Growth

## Purpose
This lab applies association rule mining to a public Groceries transactional dataset. The goal is to identify frequent itemsets, generate association rules, compare Apriori and FP-Growth, and use Seaborn visualizations to interpret market-basket patterns.

## Files
- `MSCS_634_Lab_6.ipynb`: Jupyter Notebook containing data preparation, frequent itemset mining, association rule generation, visualizations, and analysis.
- `data/groceries.csv`: Public Groceries transactional dataset used for this lab.
- `requirements.txt`: Python dependencies used for the notebook.
- `screenshots/`: PNG images of notebook plots and tables.

## Screenshot Guide
### Plots
- `screenshots/01-top-15-frequent-items.png`: Seaborn barplot of the most frequent grocery items.
- `screenshots/02-top-10-item-cooccurrence-heatmap.png`: Seaborn heatmap showing item co-occurrence among top items.
- `screenshots/03-top-apriori-frequent-itemsets.png`: Seaborn barplot of top Apriori frequent itemsets by support.
- `screenshots/04-top-fpgrowth-frequent-itemsets.png`: Seaborn barplot of top FP-Growth frequent itemsets by support.
- `screenshots/05-association-rules-confidence-vs-lift.png`: Seaborn scatter plot of confidence versus lift for association rules.
- `screenshots/06-top-association-rules-by-lift.png`: Seaborn barplot of the top association rules by lift.
- `screenshots/07-algorithm-runtime-and-rule-count-comparison.png`: Runtime and rule-count comparison for Apriori and FP-Growth.

### Tables
- `screenshots/tables/01-cleaned-transaction-records.png`: Cleaned transaction-item records.
- `screenshots/tables/02-transaction-length-summary.png`: Summary statistics for transaction length.
- `screenshots/tables/03-top-15-frequent-items-table.png`: Top 15 item counts.
- `screenshots/tables/04-top-apriori-itemsets.png`: Top Apriori frequent itemsets.
- `screenshots/tables/05-top-fpgrowth-itemsets.png`: Top FP-Growth frequent itemsets.
- `screenshots/tables/06-algorithm-runtime-comparison.png`: Apriori and FP-Growth runtime comparison.
- `screenshots/tables/07-top-association-rules.png`: Top association rules ranked by lift.
- `screenshots/tables/08-final-algorithm-rule-comparison.png`: Final comparison of itemsets, rules, runtime, lift, and confidence.

## Dataset
The dataset is a public Groceries market-basket dataset. Each row represents one transaction and contains comma-separated grocery items. The cleaned dataset contains 9,835 transactions and 169 unique items.

Source URL:
`https://raw.githubusercontent.com/stedy/Machine-Learning-with-R-datasets/master/groceries.csv`

## Requirement Coverage
- Created a Jupyter Notebook with name, course title, and lab assignment title.
- Selected and loaded a public transactional dataset.
- Cleaned transaction item names and removed duplicate items within each transaction.
- Converted transactions into one-hot encoded item format.
- Used Seaborn barplots to show frequent items and frequent itemsets.
- Used a Seaborn heatmap to show item co-occurrence.
- Applied Apriori with a minimum support threshold.
- Applied FP-Growth with the same support threshold.
- Compared Apriori and FP-Growth runtime and output.
- Generated association rules using a confidence threshold.
- Reported support, confidence, and lift.
- Used Seaborn scatter and bar plots to visualize association-rule insights.
- Discussed algorithm efficiency, key rules, parameter decisions, and challenges.

## Methods
- Minimum support threshold: `0.02`
- Minimum confidence threshold: `0.30`
- Apriori and FP-Growth were run on the same one-hot encoded transaction matrix.
- Association rules were ranked mainly by lift and confidence.
- Runtime was measured with `time.perf_counter`.

## Interpretation Notes
- Transaction cleaning was necessary because association mining depends on accurate item counts. Extra spaces, empty values, or duplicate items inside a transaction could distort support values.
- One-hot encoding was used because Apriori and FP-Growth need a transaction-by-item matrix showing whether each item was purchased in each basket.
- Support was used to identify itemsets that appeared often enough to matter operationally.
- Confidence was used to measure how often a consequent item appeared when an antecedent item was present.
- Lift was used to identify associations that were stronger than item popularity alone. This helps avoid overvaluing rules whose consequents are simply common products.
- The Seaborn heatmap and barplots were included to connect the mined patterns back to visible transaction behavior.

## Key Insights
- Apriori and FP-Growth produced the same `122` frequent itemsets and `37` association rules because the same data and thresholds were used.
- Apriori was faster on this moderate-size one-hot encoded dataset.
- The most frequent grocery items included `whole milk`, `other vegetables`, `rolls/buns`, `soda`, and `yogurt`.
- Strong rules often involved staple grocery combinations, especially rules connected to `whole milk`, `other vegetables`, and `root vegetables`.
- Lift was useful for identifying relationships that were stronger than raw frequency alone.
- The main business outcome is that these rules can guide product placement, bundle promotions, and recommendation logic, but they should be treated as associations rather than proof of causation.

## Challenges and Decisions
- The main decision was selecting a support threshold. A low threshold creates too many rules, while a high threshold hides useful multi-item patterns.
- A support threshold of `0.02` produced a manageable number of frequent itemsets.
- A confidence threshold of `0.30` produced interpretable rules without overwhelming the analysis.
- Item names were stripped of extra whitespace during cleaning to avoid treating the same item as multiple different items.
- This lab includes a requirement checklist, direct interpretation after major outputs, and saved screenshots for plots and tables.

## Run the Notebook
```bash
cd MSCS_634_Lab_6
pip install -r requirements.txt
jupyter notebook MSCS_634_Lab_6.ipynb
```

If the notebook shows a missing package error, install the requirements in the Python environment used by Jupyter.
