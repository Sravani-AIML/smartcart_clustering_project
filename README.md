# smartcart_clustering_project
Customer segmentation for SmartCart using KNN and Agglomerative Clustering

### 1. Problem Statement
The goal of this project is to segment SmartCart customers based on purchasing behavior to improve targeted marketing and customer retention strategies.

### 2. Dataset Description
The SmartCart dataset consists of 2,240 customer records with 22 attributes, containing detailed information about customer demographics, purchasing behavior, website activity, and engagement history.
Each row represents a single customer and captures their spending patterns, purchase frequency, and interaction with the platform.
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

### 3.Data Preprocessing & Feature Engineering

The Income feature contained 24 missing values, which were imputed using the median to handle skewness. The Year_Birth column was converted into Age, and Dt_Customer was transformed into Customer Tenure (in days) to better represent customer lifecycle behavior.
To capture overall purchasing behavior, a new feature Total_Spending was created by combining MntWines, MntFruits, MntMeatProducts, MntFishProducts, MntSweetProducts, and MntGoldProds. Similarly, Total_Children was created by combining Kidhome and Teenhome.
Education levels were consolidated into three broader categories: Undergraduate (Basic, 2n Cycle), Graduate (Graduation), and Postgraduate (Master, PhD). Marital_Status was simplified into a new feature, Living_with, where Married and Together were grouped as Partner, and Single, Divorced, Widow, Absurd, and YOLO were grouped as Alone.
All categorical variables were encoded prior to modeling, and feature scaling was applied using StandardScaler since KNN and Agglomerative Clustering are distance-based algorithms.

### 4.Outlier Detection

A pair plot was generated to visually inspect feature distributions and identify potential outliers. Extreme values were observed in the Income and Age features. These outliers were removed to prevent distortion in distance-based clustering algorithms and to improve model stability.
<img width="633" height="630" alt="image" src="https://github.com/user-attachments/assets/fb0203a1-67f7-4c0e-8d24-737c5cda68c9" />



  
