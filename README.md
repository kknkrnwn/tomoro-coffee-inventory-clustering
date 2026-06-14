# tomoro-coffee-inventory-clustering
Tomoro Coffee inventory and product stock clustering using K-Means algorithm for inventory optimization, data profiling, and sales strategy.

# ☕ Tomoro Coffee Inventory Clustering using K-Means

This project implements an Unsupervised Machine Learning algorithm, specifically **K-Means Clustering**, to analyze and segment product inventory data at Tomoro Coffee. The clustering is driven by two key business metrics: **Total Sales** and **Average Stock**, helping the management optimize their supply chain, prevent stockouts, and design efficient replenishment or promotional strategies.

## 📊 Project Overview
Using a data science approach, this project processes raw daily inventory data, handles extreme values (outliers), standardizes features, and evaluates the most ideal number of clusters. The final output provides multi-dimensional visualizations and strategic data profiling to classify product behaviors (e.g., separating fast-moving products from slow-moving inventory).

### Tech Stack:
* **Language:** Python
* **Data Wrangling:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn` (`StandardScaler`, `KMeans`, `PCA`)
* **Model Evaluation:** `silhouette_score`, `davies_bouldin_score`, `calinski_harabasz_score`
* **Model Persistence:** `joblib`

---

## 🛠️ Step-by-Step Notebook Workflow

The notebook `PRODUK_STOK_TOMORO_COFFEE_.ipynb` is systematically structured into 10 core steps:

### 1. Library Import & Configuration
Loading all essential libraries required for statistical data science, advanced visualizations, K-Means modeling, and multi-metric clustering evaluation.

### 2. Data Loading and Inspection
Reading raw inventory datasets (`.xlsx` or `.csv`) interactively, followed by checking data types, basic column structures, and initial data discovery.

### 3. Data Cleaning
* Handling missing values on crucial identifier columns.
* Converting string/object columns into appropriate numeric data types.
* Deduplicating redundant rows.
* Normalizing daily sales values to absolute (positive) numbers to align with clustering objectives.

### 4. Feature Engineering & Outlier Handling
* Aggregating transactional records to higher level product metrics: `TotalSales` and `AvgStock`.
* Detecting and removing extreme values (outliers) using the **IQR (Interquartile Range)** method so that K-Means cluster centers are not distorted.

### 5. Data Scaling (Standardization)
Applying `StandardScaler` (transforming data features to have a Mean = 0 and Variance = 1) to ensure sales magnitude and stock volumes are balanced fairly during distance calculations.

### 6. Number of Clusters (K) Evaluation
Determining the optimal number of groups (evaluating K = 2 to K = 9) by analyzing 4 evaluation metrics simultaneously:
* **Inertia / WCSS** (Elbow Method)
* **Silhouette Score**
* **Davies-Bouldin Index (DBI)**
* **Calinski-Harabasz Index (CHI)**

### 7. Final K-Means Modeling
Training the final K-Means model with the chosen best-performing K value derived from the combined evaluation step.

### 8. Clustering Visualization
* **2D Scatter Plot:** Mapping product distribution based on *Sales* vs *Stock* dimensions, color-coded by cluster membership.
* **3D Visualization:** Multi-perspective 3D scatter plotting involving Cluster ID to provide better cluster depth analysis.
* **Cluster Bar Chart:** A grouped bar chart comparing the mean values of each feature across clusters to distinguish their behavior.

### 9. Strategic Cluster Profiling
Analyzing the characteristics of each group to formulate tailored business recommendations or stock actions (e.g., highly sold products with low inventory levels are flagged with a "Re-order immediately" action plan).

### 10. Data & Model Export
* Saving the trained K-Means model (`model_kmeans_final.pkl`) and scaler object (`model_scaler_final.pkl`) using `joblib` for future re-use or deployment.
* Merging cluster labels back to the original unique product list and exporting it as a new Excel file named `HASIL_CLUSTERING_TOMORO.xlsx`.

---

## 🚀 How to Run the Project
1. Clone this repository to your local machine:
```bash
   git clone [https://github.com/your-username/tomoro-coffee-inventory-clustering.git](https://github.com/your-username/tomoro-coffee-inventory-clustering.git)
