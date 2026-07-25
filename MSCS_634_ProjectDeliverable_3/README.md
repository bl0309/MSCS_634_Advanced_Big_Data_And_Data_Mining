# MSCS 634 Project Deliverable 3: Classification, Clustering, and Pattern Mining

## Purpose
This deliverable applies classification, clustering, and association rule mining to the Online Retail dataset. It predicts high-value invoices, segments customers, and finds product associations.

## Methods
- Classification: Logistic Regression and Random Forest
- Hyperparameter tuning: GridSearchCV for Random Forest
- Evaluation: Confusion matrix, ROC curve, Accuracy, F1 score, and ROC-AUC
- Clustering: K-Means on customer RFM-style features
- Pattern mining: FP-Growth frequent itemsets and association rules on product baskets

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

## Classification, Clustering, and Pattern Mining Insights
The classification analysis showed that invoice-level features can be used to predict whether an invoice is likely to be high value. Logistic Regression provided an interpretable baseline, while Random Forest performed better because it can capture nonlinear relationships among basket size, item variety, pricing, timing, and country. The tuned Random Forest model is useful because it can help identify invoices or customers that may deserve priority attention.

The clustering analysis grouped customers using RFM-style behavior, including recency, frequency, monetary value, quantity purchased, product variety, and average order value. This helped reveal that customers are not all alike: some customers purchase frequently and generate high revenue, while others are less active or have lower order values. These segments can support more targeted business strategies instead of treating all customers the same.

The pattern mining analysis identified products that often appear together in the same invoice. FP-Growth was used to find frequent itemsets, and association rules were evaluated using support, confidence, and lift. Rules with high lift are especially useful because they show product relationships that occur more often than expected by chance. These patterns can support recommendation systems, product bundles, and cross-selling decisions.

## Practical Relevance
The findings have direct real-world retail applications. A business could use the classification model to flag high-value invoices for priority service, loyalty offers, or retention campaigns. Customer clusters could guide segmented marketing, such as rewarding high-value customers, re-engaging inactive customers, or creating promotions for moderate-value customers with growth potential.

Association rules can be applied to product recommendation engines, online checkout suggestions, email promotions, and bundled product displays. For example, if two products frequently appear together with high confidence and lift, the retailer could recommend one product when the other is added to the cart. These insights can improve customer experience while also increasing average order value.

Together, the three methods provide a practical decision-support workflow: classification helps predict valuable transactions, clustering helps understand customer groups, and pattern mining helps identify product relationships that can be used for merchandising and recommendations.

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
