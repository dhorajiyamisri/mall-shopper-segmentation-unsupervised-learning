# Mall Shopper Profiling — Unsupervised Learning Summary Report

## 1. Business Problem and Dataset

The objective of this project is to identify meaningful shopper segments from mall customer data and translate them into actionable retail personas. A mall management team can use customer segmentation to understand spending behaviour, design targeted promotions, improve store placement, and provide personalised loyalty rewards.

The project uses the Mall Customer Segmentation dataset containing 200 customers and five original attributes: CustomerID, Gender, Age, Annual Income (k$), and Spending Score (1–100). Exploratory Data Analysis was performed using distributions, boxplots, gender analysis, scatter plots, and correlation analysis. The Annual Income versus Spending Score visualization showed clear natural groupings, making it the primary clustering space.

## 2. Features and Preprocessing

Two feature representations were prepared for clustering. The 2D feature set consisted of AnnualIncome and SpendingScore because these variables directly represent customer purchasing power and spending behaviour and provide an interpretable visual clustering space.

A multivariate feature set was also created using Age, AnnualIncome, SpendingScore, and encoded Gender. Gender was encoded as Female = 0 and Male = 1, while additional categorical features such as IncomeGroup, AgeGroup, and SpendingCategory were engineered for analysis. StandardScaler was applied before clustering so that differences in feature scales would not disproportionately affect distance-based algorithms.

## 3. Clustering Algorithm Comparison

Three clustering algorithms were evaluated: K-Means, Agglomerative Hierarchical Clustering, and DBSCAN.

K-Means generated 5 clusters with a Silhouette Score of **0.5547**, Davies-Bouldin Index of **0.5722**, and Calinski-Harabasz Index of **248.6493**. Agglomerative Clustering also generated 5 clusters, with a Silhouette Score of **0.5530**, Davies-Bouldin Index of **0.5779**, and Calinski-Harabasz Index of **244.4103**.

DBSCAN generated 4 clusters and achieved the strongest internal metric values: Silhouette Score **0.5972**, Davies-Bouldin Index **0.4734**, and Calinski-Harabasz Index **263.6118**. However, DBSCAN classified **25.5% of customers as noise**. Therefore, its stronger separation metrics need to be considered together with the loss of a substantial number of customers from the main segments.

K-Means was highly stable across random seeds 0, 7, 21, 42, and 99, producing a mean Silhouette Score of **0.5547** with a standard deviation of **0.0000**.

## 4. Shopper Personas

The K-Means profiles produced five interpretable retail personas:

- **Big Spenders:** 39 customers, with average income of 86.54k and spending score of 82.13. These customers show both strong purchasing power and high spending activity and can be targeted with premium products and loyalty benefits.

- **Young Aspirers:** 22 customers, with average age 25.27, income of 25.73k, and spending score of 79.36. Youth-focused offers, affordable premium products, and digital campaigns can be used to engage this group.

- **Balanced Shoppers:** 81 customers, the largest segment, with average income of 55.30k and spending score of 49.52. General promotions, loyalty rewards, and cross-category offers can support this broad customer group.

- **Budget Shoppers:** 23 customers, with average income of 26.30k and spending score of 20.91. Value-for-money offers, discounts, and budget-focused promotions may be relevant for this segment.

- **High-Income Careful Shoppers:** 35 customers, with average income of 88.20k but a low spending score of 17.11. Personalised offers and premium experiences could be used to understand and potentially increase their mall engagement.

## 5. Future Improvements

Future segmentation could be improved by collecting purchase-category data, transaction value, visit frequency, preferred stores, loyalty-program activity, and footfall-sensor information. Further work could also explore semi-supervised learning and a real-time persona tagging API for the mall application.

Overall, the project demonstrates how unsupervised learning can convert basic demographic and spending information into interpretable shopper segments that can support data-driven retail decision-making.