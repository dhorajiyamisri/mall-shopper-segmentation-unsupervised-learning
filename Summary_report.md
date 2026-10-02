# Mall Shopper Segmentation — Summary Report

## 1. Business Problem and Dataset

The objective of this project is to segment mall customers into meaningful shopper groups using unsupervised learning. The business problem is to understand how customers differ in terms of age, annual income and spending behaviour so that retail operations teams can design more targeted marketing campaigns, promotions, loyalty rewards and customer experiences.

The project uses the Mall Customer Segmentation dataset containing **200 customers and 5 original columns**: CustomerID, Genre, Age, Annual Income (k$), and Spending Score (1–100). The `Genre` column was renamed to `Gender`, while income and spending columns were renamed to `AnnualIncome` and `SpendingScore`.

## 2. Feature Selection and Preprocessing

Two feature representations were explored.

The **2D clustering experiment** used `AnnualIncome` and `SpendingScore`. These features provide a clear view of customer purchasing behaviour and allow the resulting clusters to be visualised directly.

The **multivariate experiment** used `Age`, `AnnualIncome`, `SpendingScore`, and `Gender_enc`. Gender was encoded as Female = 0 and Male = 1 while the original Gender column was retained for interpretation.

Additional features including IncomeGroup, AgeGroup and SpendingCategory were engineered for exploratory and business analysis. StandardScaler was applied separately to the clustering feature sets because K-Means, Agglomerative Clustering and DBSCAN are distance-sensitive algorithms.

## 3. Clustering Algorithm Comparison

Three clustering algorithms were evaluated:

* K-Means
* Agglomerative Hierarchical Clustering
* DBSCAN

The models were compared using Silhouette Score, Davies-Bouldin Index and Calinski-Harabasz Index. DBSCAN was additionally evaluated using its percentage of noise points.

| Algorithm     |  Clusters | Silhouette | Davies-Bouldin | Calinski-Harabasz |   Noise % |
| ------------- | --------: | ---------: | -------------: | ----------------: | --------: |
| K-Means       | `[value]` |  `[value]` |      `[value]` |         `[value]` |         0 |
| Agglomerative | `[value]` |  `[value]` |      `[value]` |         `[value]` |         0 |
| DBSCAN        | `[value]` |  `[value]` |      `[value]` |         `[value]` | `[value]` |

The final model selection should be based on the combined internal metrics and the interpretability of the resulting shopper segments.

## 4. Shopper Segments

### Big Spenders

This segment contains customers with relatively high annual income and high spending scores. They represent high-value shoppers and can be considered for premium retail experiences, loyalty benefits and premium-brand campaigns.

### Budget Shoppers

This segment contains customers with relatively lower income and lower spending scores. Value-oriented promotions, discounts, bundle offers and budget-friendly stores may be relevant for this group.

### Careful Spenders

These customers have relatively higher income but comparatively lower spending scores. Their profile suggests that income alone does not result in high spending, so selective promotions and personalised recommendations may be more appropriate.

### Young Aspirers

This segment is characterised by younger customers combined with moderate or high spending behaviour. Fashion, entertainment, digital campaigns and trend-oriented promotions can be considered for this group.

### Mature Savers

These customers are relatively older and show lower or moderate spending behaviour. Practical offers, convenience-focused services and loyalty rewards may be suitable for this segment.

> The final cluster-to-persona mapping should be updated according to the actual cluster profile produced by the executed notebook.

## 5. Business Interpretation

The segmentation demonstrates how unsupervised learning can convert basic customer attributes into actionable shopper profiles. Retail teams can use these segments to design differentiated promotions rather than applying the same campaign to every customer.

The results can also support decisions related to store layouts, promotional events, loyalty programmes and personalised customer experiences.

## 6. Future Improvements

The current dataset contains limited demographic and spending information. Segmentation could be improved by collecting purchase-category data, average transaction value, visit frequency, loyalty-app behaviour, preferred stores, promotion response and footfall-sensor information.

Future work could also explore semi-supervised learning when labelled customer outcomes become available. A real-time persona-tagging API could eventually integrate the segmentation model into a mall application and assign shopper personas dynamically.

## Conclusion

This project demonstrates a complete unsupervised-learning workflow covering EDA, feature engineering, scaling, K-Means, hierarchical clustering, DBSCAN, internal evaluation, shopper profiling and business interpretation. The final executed notebook and model files provide a reusable foundation for customer segmentation and future retail analytics applications.
