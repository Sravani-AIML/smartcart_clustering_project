# smartcart_clustering_project
Customer segmentation for SmartCart using KNN and Agglomerative Clustering

### 1. Problem Statement
The goal of this project is to segment SmartCart customers based on purchasing behavior to improve targeted marketing and customer retention strategies.

### 2. Dataset Description
The SmartCart dataset consists of 2,240 customer records with 22 attributes, containing detailed information about customer demographics, purchasing behavior, website activity, and engagement history.
Each row represents a single customer and captures spending patterns, purchase frequency, and platform interaction.
1. Customer Demographics
These features describe the personal and household characteristics of customers:
- ID – Unique customer identifier
- Year_Birth – Year of birth
- Education – Highest education level achieved
- Marital_Status – Customer's marital status
- Income – Yearly household income
- Kidhome – Number of small children in the household
- Teenhome – Number of teenagers in the household
- Dt_Customer – Date of enrollment with SmartCart
  
2. Purchase Behaviour (Amount Spent)
These features represent the monetary value spent across product categories:
- MntWines – Amount spent on wine products
- MntFruits – Amount spent on fruits
- MntMeatProducts – Amount spent on meat products
- MntFishProducts – Amount spent on fish products
- MntSweetProducts – Amount spent on sweet products
- MntGoldProds – Amount spent on gold products

3. Purchase Behaviour (Frequency & Activity)
These features measure how frequently customers make purchases and interact with the platform:
- NumDealsPurchases – Purchases made using discounts
- NumWebPurchases – Purchases made through website
- NumCatalogPurchases – Purchases made through catalog
- NumStorePurchases – Purchases made in physical stores
- NumWebVisitsMonth – Number of website visits per month

4. Customer Feedback & Engagement
These features capture recency and customer satisfaction:
- Recency – Number of days since last purchase
- Complain – Whether the customer complained in the last 2 years (1 = Yes, 0 = No)

### 3. Data Preprocessing & Feature Engineering

The Income feature contained 24 missing values, which were imputed using the median to handle skewness. The Year_Birth column was converted into Age, and Dt_Customer was transformed into Customer Tenure (in days) to better represent customer lifecycle behavior.
To capture overall purchasing behavior, a new feature Total_Spending was created by combining MntWines, MntFruits, MntMeatProducts, MntFishProducts, MntSweetProducts, and MntGoldProds. Similarly, Total_Children was created by combining Kidhome and Teenhome.
Education levels were consolidated into three broader categories: Undergraduate (Basic, 2n Cycle), Graduate (Graduation), and Postgraduate (Master, PhD). Marital_Status was simplified into a new feature, Living_with, where Married and Together were grouped as Partner, and Single, Divorced, Widow, Absurd, and YOLO were grouped as Alone.
All categorical variables were encoded prior to modeling, and feature scaling was applied using StandardScaler since KMeans and Agglomerative Clustering are distance-based algorithms.

### 4. Outlier Detection

A pair plot was generated to visually inspect feature distributions and identify potential outliers. Extreme values were observed in the Income and Age features. These outliers were removed to prevent distortion in distance-based clustering algorithms and to improve model stability.
<img width="633" height="630" alt="image" src="https://github.com/user-attachments/assets/fb0203a1-67f7-4c0e-8d24-737c5cda68c9" />

### 5. Correlation Analysis

A correlation heatmap was generated to analyze relationships between numerical features. A strong positive correlation (~0.79) was observed between Income and Total_Spending, indicating that higher-income customers tend to spend more. No severe multicollinearity was identified.
<img width="891" height="687" alt="image" src="https://github.com/user-attachments/assets/d810b104-12fb-4003-bdee-03048f9fb2a4" />

### 6. Principal Component Analysis(PCA)

PCA was applied to reduce high-dimensional data into two principal components for visualization purposes. The first two components explained approximately 44% of the total variance, allowing cluster patterns to be visualized in a reduced two-dimensional space.

### 7. Determining Optimal Number of Clusters

The optimal number of clusters was determined using both the Elbow Method and Silhouette Score.
The elbow curve showed a significant reduction in inertia up to k = 4, after which the decrease became gradual, indicating diminishing returns. The silhouette score also improved noticeably at k = 4, suggesting better cluster separation.
Based on both methods, k = 4 was selected as the optimal number of clusters to balance model performance and interpretability.
<img width="720" height="541" alt="image" src="https://github.com/user-attachments/assets/d7f471ba-67a3-4cd8-a399-6ee776512217" />

### 8. Clustering

Both KMeans and Agglomerative Clustering were applied with k = 4. While KMeans identified distinct segments, some overlap between clusters was observed due to its assumption of spherical cluster shapes and reliance on centroid-based partitioning.

Agglomerative Clustering produced more clearly separated and hierarchically structured segments, capturing non-spherical relationships in the data more effectively.

This suggests that hierarchical clustering better captures the underlying customer structure in this dataset.
1.KMeans Clustering
<img width="449" height="435" alt="image" src="https://github.com/user-attachments/assets/fc10c8ba-3ccb-4a79-acf0-046ac4cf9ea9" />
2.Agglomerative Clustering
<img width="441" height="434" alt="image" src="https://github.com/user-attachments/assets/f6bc890f-2cd1-4994-aa00-1f5e694ae31a" />

### 9. Cluster Interpretation & Business Insights

<img width="450" height="528" alt="image" src="https://github.com/user-attachments/assets/90a491ae-878c-444f-b4e8-4e59303bb23f" />
1.Cluster 0 – Family-Oriented Budget Shoppers
- Low to moderate income and spending levels
- Higher number of children
- Frequent website visits
- Responsive to discount coupons

Business Insight:
This segment is price-sensitive and family-driven. Targeted family bundles, discount campaigns, and seasonal promotions may increase conversion.

2.Cluster 1 – Loyal High-Value Customers
- High income and highest total spending
- Strong engagement across store, catalog, and web purchases
- Consistent purchasing behavior

Business Insight:
This segment represents core revenue contributors. Loyalty programs, exclusive rewards, and premium membership benefits can strengthen retention.

3.Cluster 2 – Discount-Driven Low-Income Singles
- Low income and low overall spending
- High reliance on discount purchases
- Primarily living alone
- Frequent website visits

Business Insight:
This group is highly price-sensitive. Personalized coupon strategies and entry-level product promotions may improve engagement and spending.

4.Cluster 3 – High-Value Independent Shoppers
- Moderate to high income and high spending
- Living alone
- Strong response to promotional campaigns
- Active across store, catalog, and web channels

Business Insight:
This segment is responsive to marketing efforts and premium offerings. Personalized recommendations and exclusive services can maximize lifetime value.

### 10. Conclusion

This project demonstrates how unsupervised learning techniques such as PCA, KMeans, and Agglomerative Clustering can uncover meaningful customer segments. The derived clusters provide actionable insights for targeted marketing strategies and customer retention optimization.









  
