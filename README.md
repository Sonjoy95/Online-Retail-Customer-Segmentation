# Online Retail Customer Segmentation
## Project Overview
This project focuses on performing customer segmentation for an online retail dataset using unsupervised machine learning techniques, specifically K-Means clustering. The primary goal is to identify distinct customer groups based on their purchasing behavior (Recency, Frequency, Monetary - RFM) to enable more targeted and effective marketing strategies. This project demonstrates a complete data science pipeline from data loading and exploratory data analysis (EDA) to feature engineering, clustering, and actionable insights.

## Key Features and Steps
1. #### **Data Loading & Initial Exploratory Data Analysis (EDA):**
- Imported the `OnlineRetail.csv` dataset, handling potential encoding issues.
- Conducted a thorough initial EDA, including:
  * `df.info()` for data types and non-null counts.
  * `df.describe()` for statistical summaries of numerical features.
  * Missing value analysis.
  * Statistical summaries of categorical features (value_counts()).


2. #### **Data Preprocessing & Cleaning:**
- Dropped rows with missing `CustomerID.`
- Removed canceled orders (identified by 'C' in `InvoiceNo`).
- Converted InvoiceDate to datetime objects.
- Calculated `TotalPrice` (`Quantity * UnitPrice`).
- Filtered out transactions with non-positive `Quantity` or `UnitPrice` to ensure valid sales data.


3. #### **EDA on Processed Data:**
- `df.info` to display basic information about datset after preprocessing
- Visualizations (histograms and box plots) for `Quantity`, `UnitPrice`, and `TotalPrice` after log1p transformation to address severe skewness and visualize distributions effectively.
- Bar plots for top countries by transaction count.


4. #### **RFM Feature Engineering:**
- Engineered three critical marketing metrics for each customer:
  * **Recency:** Days since last purchase.
  * **Frequency:** Number of unique purchases.
  * **Monetary:** Total spending.
- Applied outlier treatment to RFM features by capping values at the 5th and 95th percentiles to mitigate the influence of extreme values on clustering.
- Scaled the RFM features using `StandardScaler` to ensure all features contribute equally to distance calculations in K-Means.


5. #### **Optimal Cluster Determination & K-Means Clustering:**
- Utilized the Elbow Method (WCSS vs. K) and Silhouette Score (average silhouette score vs. K) to determine the optimal number of clusters.
- **Chosen K=4** based on a balance between statistical metrics and the desire for richer, more actionable customer segments for marketing purposes.
- Applied the K-Means algorithm to segment customers into these four distinct groups.


6. #### **Cluster Analysis & Visualization:**
- Calculated and analyzed the mean RFM values for each cluster to profile their unique characteristics.
- Visualized the customer segments using:
  * A 2D PCA-reduced scatter plot, clearly showing customer distribution, with cluster centroids marked and a legend displaying descriptive segment names (e.g., "Loyal Big Spenders").
  * Bar plots illustrating the average Recency, Frequency, and Monetary values for each cluster, providing clear visual comparisons.


## Data Source
The dataset used for this project is the "Online Retail" dataset, which contains transactional data from a UK-based online retail store.
- **Source:** UCI Machine Learning Repository or Kaggle (ensure you download Online Retail.xlsx and convert to Online Retail.csv or download the CSV version directly from the repository).

## Technologies Used
- **Python 3.13**
- **Pandas:** For data manipulation and analysis.
- **NumPy:** For numerical operations.
- **Scikit-learn:** For preprocessing (`StandardScaler`, `PCA`) and clustering (`KMeans`).
- **Matplotlib:** For creating static, interactive, and animated visualizations.
- **Seaborn:** For enhanced data visualizations.

How to Run the Project
Clone the Repository:

git clone <your-repository-url>
cd <your-repository-name>

Download the Dataset:

Download the Online Retail.csv file from the UCI Machine Learning Repository or Kaggle.

Place the Online Retail.csv file in the root directory of the cloned repository.

Install Dependencies:

pip install pandas numpy scikit-learn matplotlib seaborn openpyxl

Run the Python Script:

python customer_segmentation.py  # Assuming your main script is named customer_segmentation.py

The script will print various analyses to the console and display several plots.

Key Findings & Customer Segments
The project identified four distinct customer segments, each with unique RFM characteristics:

Loyal Big Spenders (Cluster 3): Very recent, highly frequent, and extremely high spending customers. Your most valuable segment.

Promising Regular Spenders (Cluster 1): Relatively recent, good frequency, and high spending customers. Active with growth potential.

Occasional/Moderately Spending Customers (Cluster 0): Moderate recency, low frequency, and moderate spending customers. Buy occasionally and need nurturing.

At-Risk/Rarely Spending Customers (Cluster 2): Very high recency, very low frequency, and lowest spending customers. One-time buyers or inactive/churned.

Actionable Insights
These segments provide a clear roadmap for targeted marketing:

Loyal Big Spenders: Focus on retention, exclusive offers, and personalized recommendations.

Promising Regular Spenders: Encourage increased frequency and average order value through cross-selling and tiered rewards.

Occasional/Moderately Spending Customers: Implement targeted promotions and re-engagement campaigns.

At-Risk/Rarely Spending Customers: Initiate win-back campaigns and feedback surveys to understand inactivity.

Author
[Your Name/GitHub Username]
[Your LinkedIn Profile URL (Optional)]
[Your Portfolio Website URL (Optional)]

This README was generated with assistance from a large language model.
