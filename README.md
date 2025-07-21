# Customer Segmentation Using RFM Analysis and KMeans Clustering

## Project Overview

This project focuses on identifying distinct customer segments using RFM (Recency, Frequency, Monetary) analysis in conjunction with KMeans clustering. The goal is to derive actionable customer insights that allow for effective personalization, improved engagement, and higher customer retention.

## Objective

To segment customers based on their purchasing behavior by analyzing transactional data and applying unsupervised learning techniques. These customer segments can help businesses:

* Tailor marketing campaigns
* Optimize resource allocation
* Predict and improve customer retention

## Business Context

In e-commerce, understanding customer behavior is crucial for building loyalty and sustaining competitive advantage. The RFM model provides a powerful yet simple framework to assess customer value based on:

* **Recency**: Time since last purchase
* **Frequency**: Number of purchases
* **Monetary**: Amount spent

By clustering customers based on these metrics, businesses can develop a deeper understanding of their audience and align strategies accordingly.

## Dataset Source

The dataset used is the **Online Retail Dataset** available on the UCI Machine Learning Repository:
[https://archive.ics.uci.edu/dataset/352/online+retail](https://archive.ics.uci.edu/dataset/352/online+retail)

### Dataset Characteristics

* Transactions from a UK-based online retail store
* Time period: December 1, 2010 to December 9, 2011
* 541,909 instances
* 8 attributes including InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country

## Methodology

### 1. Data Exploration

* Initial inspection of dataset structure and feature types
* Identification of missing values and data quality issues
* Exploration of transaction patterns across time and geography

### 2. Data Cleaning

* Removal of rows with missing `CustomerID`
* Filtering out cancellations (invoices with 'C')
* Exclusion of non-positive quantities and unit prices
* Conversion of `InvoiceDate` to datetime

### 3. Feature Engineering: RFM Calculation

* **Recency**: Number of days since the customer’s last purchase
* **Frequency**: Count of unique transactions per customer
* **Monetary**: Sum of total spending per customer

### 4. Outlier Detection

* Boxplot and distribution-based detection of extreme values in RFM metrics
* Separate handling and profiling of outliers to avoid skewed clustering
* Intersection analysis of overlapping outliers (e.g., high monetary and frequency)

### 5. Data Scaling

* Standardization using `StandardScaler` from `sklearn.preprocessing`
* Ensures RFM features are on a comparable scale before clustering

### 6. Optimal Cluster Selection

* **Elbow Method**: Inertia plot used to identify point of diminishing returns
* **Silhouette Score**: Measures cohesion and separation of clusters
* Silhouette Score Reference: [https://medium.com/@hazallgultekin/what-is-silhouette-score-f428fb39bf9a](https://medium.com/@hazallgultekin/what-is-silhouette-score-f428fb39bf9a)

### 7. Clustering using KMeans

* KMeans algorithm from `sklearn.cluster`
* `fit_predict` used to assign clusters to each customer
* Optimal number of clusters selected based on combined Elbow and Silhouette evaluation
* Guide Reference: [https://www.analyticsvidhya.com/blog/2019/08/comprehensive-guide-k-means-clustering/](https://www.analyticsvidhya.com/blog/2019/08/comprehensive-guide-k-means-clustering/)

### 8. Cluster Profiling

* Cluster-wise average RFM metrics computed
* Assigning segment labels like "Loyal Customers", "Frequent Shoppers", "Dormant High Spenders"
* Visualization using radar charts and dual-axis plots

### 9. Combining Outliers and Non-Outliers

* Merging outlier segments with general customer clusters
* Unified analysis and visualization for complete customer base segmentation

## Tools and Technologies

* **Platform**: Jupyter Notebook
* **Language**: Python
* **Libraries**:

  * `pandas`, `numpy` for data manipulation
  * `matplotlib`, `seaborn` for visualization
  * `scikit-learn` for scaling, clustering, evaluation
* **Markdown Creation**: ChatGPT, Grok
* **Code Reference and Learning Resources**:

  * [Silhouette Score Article](https://medium.com/@hazallgultekin/what-is-silhouette-score-f428fb39bf9a)
  * [KMeans Clustering Guide on Analytics Vidhya](https://www.analyticsvidhya.com/blog/2019/08/comprehensive-guide-k-means-clustering/)
  * [KMeans Tutorial on YouTube](https://youtu.be/afPJeQuVeuY?si=r0UUzaXZXFLddIYj)

## Key Outcomes

* Successful segmentation of customers into behavior-driven clusters
* Visual insights into customer loyalty, purchase habits, and revenue contribution
* Profiling of special segments such as high-value but infrequent customers
* Framework for building targeted marketing and retention strategies

## Future Enhancements

* Use PCA or t-SNE for cluster visualization in reduced dimensions
* Deploy the segmentation model in a production environment for real-time use
* Integrate demographic or location data for deeper segmentation
* Extend analysis to predict Customer Lifetime Value (CLV)

---

This project offers a robust and reproducible approach for segmenting retail customers using transactional data and unsupervised machine learning. The combination of exploratory data analysis, domain knowledge, and statistical rigor makes it a valuable tool for strategic decision-making in customer relationship management.
