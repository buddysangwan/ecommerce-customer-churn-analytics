# End-to-End E-Commerce Customer Churn Analysis & Retention Strategy

## 📌 Project Summary
* **Project Title:** End-to-End E-Commerce Customer Churn Analysis & Retention Strategy
* **Domain:** E-Commerce / Customer Analytics
* **Project Duration:** 3 Weeks
* **Role:** Data Analyst
* **Tools & Technologies:** Python (Pandas, NumPy, Matplotlib, Seaborn), SQL (MySQL), Power BI, MS Excel

---

## 🎯 Problem Statement
E-commerce businesses often face significant revenue loss due to customer churn. Acquiring a new customer costs 5x to 7x more than retaining an existing one. The objective of this project is to analyze customer transaction history, demographical patterns, and behavioral metrics across **100,000+ records** to:
1. Identify key drivers and indicators of customer churn.
2. Segment high-value and high-risk customers using **RFM (Recency, Frequency, Monetary)** framework.
3. Build an interactive **Power BI Executive Dashboard** for ongoing retention monitoring.
4. Provide data-driven retention recommendations to reduce churn rate.

---

## 📊 Key Insights & Analytical Outcomes
* **RFM Segmentation:** Identified that **18.4%** of customers were in the "At Risk" category, contributing to a high proportion of dormant revenue.
* **Churn Driver Analysis:** Customers with fewer than 2 orders within their first 90 days had a **64% higher probability of churning**.
* **Payment Method Correlation:** Cash-on-Delivery (COD) users exhibited a higher churn rate compared to Credit Card / Wallet users.
* **Predicted Impact:** Implementing the recommended targeted campaign for the "At Risk" segment is estimated to reduce overall churn by **12%** within two quarters.

---

## 🛠️ Data Pipeline & Methodology

### 1. Data Cleaning & Preprocessing (Python)
* Handled missing values and standardized data types across transaction records.
* Extracted date features (Year, Month, Day of Week) to identify seasonality trends.
* Detected and treated outliers in order value and purchase frequency metrics.

```python
import pandas as pd
import numpy as np

# Sample Data Loading and Data Cleaning Snippet
df = pd.read_csv("ecommerce_data.csv")
df.drop_duplicates(inplace=True)
df['OrderDate'] = pd.to_datetime(df['OrderDate'])
df['TotalAmount'] = df['Quantity'] * df['UnitPrice']
```

### 2. SQL Analysis & RFM Calculations
* Querying data to calculate Recency, Frequency, and Monetary scores per customer.
* Classifying customers into segments: *Champions, Loyal Customers, At Risk, Lost*.

```sql
-- SQL Query Snippet for RFM Metrics
SELECT 
    CustomerID,
    DATEDIFF(MAX(OrderDate), '2023-12-31') AS Recency,
    COUNT(DISTINCT OrderID) AS Frequency,
    SUM(TotalAmount) AS MonetaryValue
FROM SalesData
GROUP BY CustomerID;
```

### 3. Business Intelligence Dashboard (Power BI)
* Created a multi-page dynamic dashboard featuring:
  * **KPI Cards:** Total Revenue, Active Customers, Churn Rate %, Average Order Value (AOV).
  * **Customer Demographics Page:** Churn distribution by region, gender, and age brackets.
  * **Behavioral Analysis Page:** Order history, payment preferences, and ticket category breakdown.

---

## 📁 Repository Structure
```text
├── data/                  # Raw and Cleaned Data files (.csv)
├── notebooks/             # Jupyter Notebooks (Data Cleaning, EDA, RFM Modeling)
├── sql/                   # SQL scripts for data transformation & aggregation
├── dashboards/            # Power BI file (.pbix) & Dashboard Screenshots
├── reports/               # Final Executive Summary & Presentation Slides
└── README.md              # Project Overview
```

---

## 🚀 How to Run / Replicate This Project
1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/ecommerce-customer-churn-analytics.git
   ```
2. **Setup Environment:** Install required Python dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
3. **Database Setup:** Execute the SQL scripts in `sql/` to set up and populate the database.
4. **Dashboard View:** Open `dashboards/churn_analysis_dashboard.pbix` in **Power BI Desktop** to explore the interactive visual analytics.