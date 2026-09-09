# Customer Segmentation and Transaction Analysis

A comprehensive machine learning project for analyzing customer behavior and segmenting customers into distinct groups using clustering algorithms.

## 📋 Project Overview

This project performs customer segmentation and transaction analysis on e-commerce data using two popular clustering algorithms: **KMeans** and **DBSCAN**. It identifies customer segments based on spending patterns and purchase frequency, enabling data-driven business decisions.

## 🎯 Objectives

- Analyze customer transaction data to understand spending behaviors
- Segment customers into meaningful groups using multiple clustering algorithms
- Identify high-value customers and patterns in purchase behavior
- Provide actionable insights for targeted marketing and retention strategies

## 📊 Dataset

**Source:** [UCI Machine Learning Repository - Online Retail Dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00352/Online%20Retail.xlsx)

**Features:**
- **InvoiceDate:** Transaction date and time
- **CustomerID:** Unique customer identifier
- **Quantity:** Number of units purchased
- **UnitPrice:** Price per unit
- **Country:** Customer location
- **StockCode:** Product identifier

**Data Preprocessing:**
- Removed returns (Quantity ≤ 0)
- Filtered out invalid prices (UnitPrice ≤ 0)
- Aggregated data at customer level
- Calculated total spending and purchase intervals

## 🛠️ Technologies & Libraries

- **Python 3.x**
- **pandas** - Data manipulation and aggregation
- **scikit-learn** - Clustering algorithms (KMeans, DBSCAN)
- **matplotlib** - Data visualization
- **seaborn** - Statistical data visualization
- **openpyxl** - Excel file handling

## 🔍 Methodology

### 1. **Data Aggregation**
Customer-level features extracted:
- `Total_Bill_Size` - Sum of all purchases per customer
- `Purchase_Interval_Days` - Days between first and last purchase
- `Most_Common_Location` - Primary customer location
- `Top_Item` - Most frequently purchased product

### 2. **Feature Scaling**
StandardScaler normalization for clustering algorithms

### 3. **KMeans Clustering**
- **Algorithm:** K-Means with k=3 clusters
- **Features Used:** Total Bill Size (scaled)
- **Insights Generated:**
  - Cluster 0: 4,303 regular customers (Avg Spend: $1,455.66)
  - Cluster 1: 5 VIP customers (Avg Spend: $209,342.33)
  - Cluster 2: 30 high-value customers (Avg Spend: $53,366.49)

### 4. **DBSCAN Clustering**
- **Algorithm:** Density-Based Spatial Clustering
- **Parameters:** eps=0.5, min_samples=5
- **Features Used:** Total Bill Size & Purchase Interval (scaled)
- **Insights Generated:**
  - Cluster 0: 4,300 core customers
  - Cluster 1: 15 loyal high-spenders
  - Cluster 2: 6 ultra-premium customers

## 📈 Key Findings

### KMeans Results
| Metric | Cluster 0 | Cluster 1 | Cluster 2 |
|--------|-----------|-----------|-----------|
| Customers | 4,303 | 5 | 30 |
| Avg Spend | $1,455.66 | $209,342.33 | $53,366.49 |
| Avg Purchase Interval | 128.94 days | 330.80 days | 313.33 days |
| Top Location | United Kingdom | United Kingdom | United Kingdom |

### DBSCAN Results
| Metric | Cluster 0 | Cluster 1 | Cluster 2 |
|--------|-----------|-----------|-----------|
| Customers | 4,300 | 15 | 6 |
| Avg Spend | $1,438.19 | $31,642.51 | $56,736.39 |
| Avg Purchase Interval | 128.79 days | 353.33 days | 365.33 days |

## 📊 Visualizations

The analysis includes the following key visualizations generated from the notebook:

### 1. **KMeans Spend Distribution by Cluster**
Box plot showing the distribution of customer spending across the three KMeans clusters. This visualization clearly shows the separation between regular customers (Cluster 0), high-value customers (Cluster 2), and VIP customers (Cluster 1).

- **Figure Size:** 800x500
- **Chart Type:** Box Plot
- **Key Insight:** Demonstrates significant spending variation, with Cluster 1 showing extreme outliers representing VIP customers with exceptional spending power

### 2. **Top 10 Customer Locations per KMeans Cluster**
Count plot revealing geographic distribution of customers across the top 10 locations, color-coded by cluster membership. Shows how each cluster is distributed geographically.

- **Figure Size:** 1200x500
- **Chart Type:** Stacked Count Plot
- **Key Finding:** 
  - United Kingdom dominates all clusters with 3,890+ customers in Cluster 0
  - Germany and France are secondary markets with significant representation
  - Most high-value customers (Cluster 1 & 2) are concentrated in UK

### 3. **DBSCAN Clustering: Spend vs. Purchase Interval**
Scatter plot displaying the relationship between total spending (X-axis) and purchase frequency/interval (Y-axis) in the DBSCAN model. Points are colored by cluster membership.

- **Figure Size:** 800x500
- **Chart Type:** Scatter Plot with Color Coding
- **Key Insights:**
  - Premium customers visible in upper-left region (high spend, frequent purchases)
  - Regular customers clustered in lower-left (lower spend, frequent purchases)
  - High-interval customers visible in upper region (infrequent but valuable)

### 4. **KMeans Cluster Sizes**
Bar chart showing the distribution and count of customers across three KMeans clusters. Provides a clear view of segment prevalence.

- **Figure Size:** 600x400
- **Chart Type:** Count Plot
- **Distribution Breakdown:**
  - Cluster 0: 4,303 customers (99.2%)
  - Cluster 1: 5 customers (0.1%)
  - Cluster 2: 30 customers (0.7%)

### 5. **DBSCAN Cluster Sizes**
Bar chart displaying cluster sizes from DBSCAN algorithm, including noise points identified during clustering.

- **Figure Size:** 600x400
- **Chart Type:** Count Plot
- **Distribution Breakdown:**
  - Cluster 0: 4,300 customers (core segment)
  - Cluster 1: 15 customers (loyal high-spenders)
  - Cluster 2: 6 customers (ultra-premium)
  - Noise Points: ~22 outliers

## 💡 Business Insights

1. **Tiered Customer Base:**
   - Regular customers form the bulk of the customer base (Cluster 0: 99.2%)
   - Small but valuable VIP segment with exceptional spending (Cluster 1: $209K average spend per customer)
   - Mid-tier high-value customers for targeted upselling (Cluster 2: $53K average spend)

2. **Geographic Concentration:**
   - Majority of customers from United Kingdom (>90% in all clusters)
   - Secondary markets in Germany, France, and other European countries
   - Opportunity for geographic expansion strategies to reduce UK dependency

3. **Purchase Patterns:**
   - Regular customers make frequent purchases (~129 days interval)
   - High-value segments show longer purchase intervals (310+ days)
   - Suggests different engagement strategies needed per segment
   - VIP customers have 2.6x longer purchase intervals but 144x higher spend

4. **Strategic Recommendations:**
   - **For VIP Customers (Cluster 1):** Personal account management, exclusive offers, priority support, dedicated relationship managers
   - **For High-Value Customers (Cluster 2):** Loyalty programs, volume discounts, early access to new products, personalized recommendations
   - **For Regular Customers (Cluster 0):** Retention campaigns, upselling opportunities, frequency rewards, cross-sell initiatives

## 🚀 How to Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Ashwani-Pathak/Customer-Segmentation-and-Transaction-Analysis.git
   cd Customer-Segmentation-and-Transaction-Analysis
   ```

2. **Install dependencies:**
   ```bash
   pip install pandas scikit-learn matplotlib seaborn openpyxl
   ```

3. **Open the notebook:**
   - Use Google Colab: Click the "Open in Colab" link in the notebook
   - Or run locally with Jupyter:
   ```bash
   jupyter notebook Customer_Segmentation.ipynb
   ```

4. **Execute all cells** to generate analysis and visualizations

## 📁 Project Structure

```
Customer-Segmentation-and-Transaction-Analysis/
├── README.md
└── Customer_Segmentation.ipynb
```

## 🎯 Code Highlights

### Data Loading and Preprocessing
```python
# Load and clean data
data_url = 'https://archive.ics.uci.edu/ml/machine-learning-databases/00352/Online%20Retail.xlsx'
df = pd.read_excel(data_url)
df = df[df['Quantity'] > 0]  # Remove returns
df = df[df['UnitPrice'] > 0]
df['Total_Bill'] = df['Quantity'] * df['UnitPrice']
```

### Customer Aggregation
```python
# Aggregate to customer level
customer_df = df.groupby('CustomerID').agg(
    Total_Bill_Size=('Total_Bill', 'sum'),
    First_Purchase=('InvoiceDate', 'min'),
    Last_Purchase=('InvoiceDate', 'max'),
    Most_Common_Location=('Country', lambda x: x.mode()[0]),
    Top_Item=('StockCode', lambda x: x.value_counts().idxmax())
).reset_index()
```

### Clustering Implementation
```python
# KMeans
kmeans = KMeans(n_clusters=3, random_state=42, n_init=10)
customer_df['Cluster_KMeans'] = kmeans.fit_predict(customer_df[['Total_Bill_Scaled']])

# DBSCAN
dbscan = DBSCAN(eps=0.5, min_samples=5)
customer_df['Cluster_DBSCAN'] = dbscan.fit_predict(features_scaled)
```

## 🔗 References

- [Scikit-learn KMeans Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
- [Scikit-learn DBSCAN Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html)
- [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/index.php)

## 📝 License

This project is open source and available for educational and research purposes.

## 👤 Author

**Ashwani Pathak**

---

*Last Updated: 2026*
