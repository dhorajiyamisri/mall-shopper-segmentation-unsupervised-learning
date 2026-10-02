# 🛍️ Mall Shopper Segmentation — Unsupervised Learning

> **Red & White Skill Education | Practical Exam — Unsupervised Learning (Set B)**
> **Student:** Misari Dhorajiya

## 📌 Project Overview

This project performs **Mall Shopper Profiling using Unsupervised Learning**.

The objective is to identify natural groups of mall customers based on their demographic and spending behaviour. The analysis can help retail operations teams understand different shopper types and design more targeted promotions, store layouts, loyalty rewards and customer experiences.

Three clustering algorithms are explored:

* K-Means Clustering
* Agglomerative Hierarchical Clustering
* DBSCAN

The project also compares clustering quality using internal evaluation metrics and converts the resulting clusters into meaningful retail shopper personas.

---

## 🎯 Business Problem

A large shopping mall receives customers with different income levels, ages and spending behaviours. Treating all customers in the same way may result in less targeted marketing.

The goal of this project is to discover customer segments automatically and translate them into actionable retail personas such as:

* **Big Spenders**
* **Budget Shoppers**
* **Careful Spenders**
* **Young Aspirers**
* **Mature Savers**

The final persona names are assigned based on the actual cluster profiles produced by the analysis.

---

## 📊 Dataset

**Dataset:** Mall Customer Segmentation Data

**Source:** Kaggle — Mall Customer Segmentation

**Dataset Link:**
https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python

### Dataset Information

* **Rows:** 200 customers
* **Original Columns:** 5
* `CustomerID`
* `Genre`
* `Age`
* `Annual Income (k$)`
* `Spending Score (1-100)`

The columns are renamed during preprocessing:

| Original Column        | Project Column |
| ---------------------- | -------------- |
| Genre                  | Gender         |
| Annual Income (k$)     | AnnualIncome   |
| Spending Score (1-100) | SpendingScore  |

---

## 🔎 Exploratory Data Analysis

The project includes:

* Dataset shape and information
* First 10 records
* Missing-value analysis
* Gender distribution
* Age distribution
* Annual income distribution
* Spending score distribution
* Boxplots for numerical features
* Gender countplot
* Annual Income vs Spending Score
* Age vs Spending Score
* Age vs Annual Income
* Numerical correlation matrix
* Correlation heatmap
* Gender-wise statistical summary

---

## ⚙️ Feature Engineering

The following features are created:

### Gender Encoding

```text
Female → 0
Male   → 1
```

The original `Gender` column is retained for interpretation.

### Income Groups

Annual income is divided into:

* Low
* Medium
* High

using quantile-based binning.

### Age Groups

* Young: 18–25
* Adult: 26–40
* Middle-Aged: 41–55
* Senior: 55+

### Spending Categories

* Low: 1–33
* Medium: 34–66
* High: 67–100

---

## 🧮 Clustering Features

Two feature representations are explored.

### 2D Feature Set

```text
AnnualIncome
SpendingScore
```

This representation is useful for direct visualisation of income-versus-spending behaviour.

### Multivariate Feature Set

```text
Age
AnnualIncome
SpendingScore
Gender_enc
```

The features are standardized using `StandardScaler` before distance-based clustering.

---

## 🔵 K-Means Clustering

K-Means is evaluated using:

* Elbow Method
* Silhouette Score

The final value of `k` is selected using the combined evidence from the Elbow Curve and Silhouette analysis.

Both 2D and multivariate K-Means clustering are performed.

Visualisations include:

* Annual Income vs Spending Score
* Cluster centroids
* Age vs Spending Score
* PCA representation of the multivariate clustering

**Final K-Means k:** `[FINAL_K]`

---

## 🌳 Agglomerative Hierarchical Clustering

Hierarchical clustering is performed using:

* Ward linkage
* Complete linkage
* Average linkage

A dendrogram is used to identify a suitable cluster cut.

The linkage methods are compared using Silhouette Score, and the selected model is used for final hierarchical cluster profiling.

---

## 🔴 DBSCAN

DBSCAN is tuned using a k-nearest-neighbour distance analysis.

The project includes:

* 4th-nearest-neighbour distance curve
* Epsilon analysis
* `min_samples` tuning
* DBSCAN parameter grid
* Silhouette-based comparison
* Noise-point analysis

Noise points are labelled as:

```text
-1
```

---

## 📊 Model Evaluation

The three clustering approaches are compared using:

| Metric                  | Interpretation      |
| ----------------------- | ------------------- |
| Silhouette Score        | Higher is better    |
| Davies-Bouldin Index    | Lower is better     |
| Calinski-Harabasz Index | Higher is better    |
| Noise %                 | Reported for DBSCAN |

Final comparison is available in the executed notebook.

---

## 👥 Shopper Personas

The personas are assigned using the actual cluster-level:

* Average Age
* Average Annual Income
* Average Spending Score
* Gender distribution

### 🟣 Big Spenders

High-income customers with high spending behaviour. These shoppers can be associated with premium products, loyalty benefits and high-value retail experiences.

### 🟢 Budget Shoppers

Customers with relatively lower income and lower spending behaviour. Value-oriented offers, discounts and budget-friendly promotions may be relevant.

### 🔵 Careful Spenders

Customers with relatively high income but comparatively lower spending behaviour. Their behaviour may indicate a more selective or cautious purchasing pattern.

### 🟠 Young Aspirers

Younger shoppers showing moderate-to-high spending behaviour. Trend-focused promotions, fashion campaigns and digital engagement can be considered for this segment.

### 🟡 Mature Savers

Older customers with relatively low-to-moderate spending behaviour. Practical offers, loyalty rewards and convenience-oriented promotions can be considered.

> **Note:** The final cluster-to-persona mapping is based on the executed cluster profile rather than fixed cluster numbers.

---

## 💼 Business Applications

The segmentation can support:

* Targeted marketing campaigns
* Personalised loyalty rewards
* Store-placement decisions
* Promotional event planning
* Customer experience design
* Segment-specific offers
* Retail campaign analysis

---

## 📁 Project Structure

```text
mall-shopper-segmentation-unsupervised-learning/
│
├── MallShopperSegmentation_UnsupervisedLearning.ipynb
├── Mall_Customers.csv
├── mall_scaler.pkl
├── mall_segmentation_model.pkl
├── summary_report.md
├── requirements.txt
└── README.md
```

---

## 🚀 Installation & Setup

Clone the repository:

```bash
git clone https://github.com/dhorajiyamisri/mall-shopper-segmentation-unsupervised-learning.git
```

Move into the project folder:

```bash
cd mall-shopper-segmentation-unsupervised-learning
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
MallShopperSegmentation_UnsupervisedLearning.ipynb
```

Run the notebook from top to bottom.

---

## 📦 Required Libraries

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
scipy
plotly
joblib
```

---

## 💾 Saved Model Files

### `mall_scaler.pkl`

Stores the final feature scaling object used by the segmentation pipeline.

### `mall_segmentation_model.pkl`

Stores the selected final clustering model.

These files support reuse of the trained segmentation pipeline for new shoppers.

---

## 🧪 New Shopper Prediction

The notebook includes a reusable `classify_shopper()` function.

It accepts new shopper information such as:

```text
Age
AnnualIncome
SpendingScore
Gender (optional)
```

and returns:

* Cluster label
* Retail persona

The notebook tests the pipeline on five hypothetical shoppers.

---

## 🎥 Practical Exam Video

**Video:** `[PASTE GOOGLE DRIVE / YOUTUBE UNLISTED LINK HERE]`

The video demonstrates:

* Face + screen recording
* EDA
* Feature engineering
* K-Means
* Hierarchical clustering
* DBSCAN
* Cluster interpretation
* Business recommendations

**Duration:** 5–10 minutes

---

## 📄 Summary Report

Detailed project findings are available in:

```text
summary_report.md
```

The report covers the business problem, feature selection, algorithm comparison, shopper personas and future improvements.

---

## 👨‍💻 Author

**Misari Dhorajiya**

AI & ML with Data Science
Red & White Skill Education

---

## 📌 Practical Exam

**Red & White Skill Education**
**Practical Exam — Unsupervised Learning (Set B)**

> Quality is our Motto.
