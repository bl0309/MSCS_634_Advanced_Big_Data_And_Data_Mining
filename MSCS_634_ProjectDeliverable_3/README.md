# MSCS 634 Project Deliverable 3: Classification, Clustering, and Pattern Mining

## Purpose
This deliverable applies classification, clustering, and association rule mining to the Online Retail dataset. It predicts high-value invoices, segments customers, and finds product associations.

## Methods
- Classification: Logistic Regression and Random Forest
- Hyperparameter tuning: GridSearchCV for Random Forest
- Evaluation: Confusion matrix, ROC curve, Accuracy, F1 score, and ROC-AUC
- Clustering: K-Means on customer RFM-style features
- Pattern mining: Apriori association rules on product baskets

## Process Rationale
- The high-value invoice label was created from the top quartile of invoice totals to make the classification task business-relevant.
- Logistic Regression was used as an interpretable baseline, while Random Forest was used to capture nonlinear transaction behavior.
- GridSearchCV was used so Random Forest parameters were selected through cross-validation rather than guesswork.
- RFM-style customer features were used for clustering because they summarize recency, frequency, value, and product variety.
- Association rule mining was applied to invoice baskets because it identifies products that customers tend to purchase together.

## Key Insights
- High-value invoice classification can support customer prioritization and campaign targeting.
- Customer clustering reveals behavior groups based on recency, frequency, monetary value, product variety, and order value.
- Association rules reveal product combinations useful for merchandising, bundles, and recommendations.
- The main outcome is a combined predictive and descriptive view of retail behavior: invoice value prediction, customer segmentation, and product relationship discovery.

## Visual Artifacts
The notebook outputs were also exported as PNG files for easier review. Chart screenshots are stored in `screenshots/`, and notebook-style table screenshots are stored in `screenshots/tables/`.

Chart screenshots:
- `screenshots/01_tuned_random_forest_confusion_matrix.png`
- `screenshots/02_tuned_random_forest_roc_curve.png`
- `screenshots/03_customer_segments_pca_scatter.png`
- `screenshots/04_association_rules_confidence_vs_lift.png`

Table screenshots:
- `screenshots/tables/01-project-modeling-tables-preview.png`
- `screenshots/tables/02-classification-model-metrics.png`
- `screenshots/tables/03-tuned-random-forest-metrics.png`
- `screenshots/tables/04-customer-cluster-summary.png`
- `screenshots/tables/05-frequent-itemsets.png`

## Challenges
- The classification task required a clear definition of a "high-value" invoice. Since the original dataset does not include a high-value label, a business-driven threshold had to be created. This was handled by labeling invoices in the top quartile of invoice totals as high value, which created a practical target for prioritization and campaign planning.
- The high-value and non-high-value classes were not equally distributed. This mattered because accuracy alone could overstate performance if the model mainly predicted the majority class. The issue was handled by using multiple metrics, including Accuracy, F1 score, ROC-AUC, a confusion matrix, and an ROC curve.
- Customer behavior was highly skewed because a small number of customers had unusually high purchase frequency, quantity, or monetary value. These extreme values could dominate the clustering process. The issue was handled by clipping clustering features at the 99th percentile before standardization.
- Clustering required careful scaling because features such as recency, monetary value, and product variety are measured on very different scales. Standardization was used before K-Means so that one large-scale variable did not control the cluster assignments.
- Basket mining can produce too many weak or hard-to-interpret rules when too many rare products are included. To keep the association rules meaningful, the analysis focused on frequent UK basket items and used minimum support and confidence thresholds.
- Association rules show co-occurrence, not causation. This was handled by interpreting rules as product relationship signals for possible cross-selling or bundling rather than claiming that one product directly causes another purchase.

## Run
```bash
pip install -r requirements.txt
jupyter notebook MSCS_634_ProjectDeliverable_3.ipynb
```
