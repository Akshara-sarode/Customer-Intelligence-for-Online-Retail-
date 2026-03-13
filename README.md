# 🧠 Customer Intelligence for Online Retail

### 📊 Segmentation, Retention Analysis, and Re-Purchase Risk Modeling

---

# 📌 Project Overview

This project analyzes a **UK-based online retail transactional dataset** to understand customer behavior and generate actionable business insights.

The analysis focuses on:

* 🎯 **Customer segmentation using RFM analysis**
* 📈 **Cohort-based retention analysis**
* 🔁 **Repeat purchase behavior**
* ⚠️ **Short-horizon re-purchase risk modeling**
* ↩️ **Return and cancellation behavior**
* 💰 Corrected customer value using **NetRevenue**

The project was developed as a **full end-to-end applied data science case study** using Python and Jupyter Notebook, emphasizing both **business interpretation and technical rigor**.

---

# 💼 Business Problem

For an online retail business, understanding **customer value, retention, and purchasing behavior** is essential for sustainable growth.

This project addresses key business questions:

* Who are the **most valuable customers**? 💎
* Which **customer segments drive the majority of revenue**? 💰
* How well are customers **retained over time**? 📊
* How quickly do customers **return for a second purchase**? 🔁
* Which customers are **at risk of not purchasing again soon**? ⚠️
* How do **returns and cancellations affect true customer value**? ↩️

These insights can help businesses improve **targeted marketing, retention strategies, and revenue forecasting**.

---

# 🎯 Project Objectives

The main goals of this analysis are:

* 📊 Perform **customer segmentation using RFM analysis**
* 📈 Measure **customer retention with cohort analysis**
* 🔁 Analyze **repeat purchase behavior**
* 🤖 Build a **predictive model for short-term re-purchase risk**
* ↩️ Incorporate **returns and cancellations into value estimation**
* 🎯 Identify **high-value customers at risk of churn**

---

# 🗂 Dataset

The project uses the **Online Retail Dataset**, a transactional dataset from a UK-based non-store online retailer.

📎 Dataset source:
https://www.kaggle.com/datasets/ulrikthygepedersen/online-retail-dataset

### 📋 Available Variables

| Column      | Description                                                                 |
| ----------- | --------------------------------------------------------------------------- |
| InvoiceNo   | Unique invoice number (invoices starting with **C** indicate cancellations) |
| StockCode   | Product/item code                                                           |
| Description | Product description                                                         |
| Quantity    | Number of units purchased                                                   |
| InvoiceDate | Transaction timestamp                                                       |
| UnitPrice   | Price per unit (GBP)                                                        |
| CustomerID  | Unique customer identifier                                                  |
| Country     | Customer country                                                            |

---

# 🛠 Tools and Libraries

* 🐍 Python
* 📓 Jupyter Notebook
* 🐼 pandas
* 🔢 numpy
* 📊 matplotlib
* 🤖 scikit-learn

---

# ⚙️ Methodology

## 1️⃣ Data Cleaning and Preparation

To ensure accurate customer-level analysis, the dataset was cleaned and standardized.

Key preprocessing steps:

* Converted `InvoiceDate` to **datetime format**
* Converted `CustomerID` to **nullable integer type**
* Flagged **cancellations** (`InvoiceNo` starting with **C**)
* Flagged **return-like rows** (`Quantity ≤ 0` or `UnitPrice ≤ 0`)
* Separated **true sales** from **returns/cancellations**
* Removed rows with **missing CustomerID**

---

## 2️⃣ Invoice-Level Feature Engineering

Since invoices can contain multiple line items, transactions were aggregated to create **invoice-level summaries**, including:

* 💰 Total invoice value
* 🛒 Basket size
* 📦 Number of unique products per order

---

## 3️⃣ Customer-Level Feature Engineering

Customer behavioral features were engineered to describe purchasing patterns.

Key metrics include:

* ⏱ **Recency** – days since last purchase
* 🔁 **Frequency** – number of unique invoices
* 💰 **Monetary Value** – total revenue
* 💳 **Average Order Value**
* 🛒 **Average Basket Size**
* 📦 **Average Unique Items per Order**
* 📅 **Customer Age (days)**
* 📈 **Historical CLV within observation window**

---

# 🧩 RFM Customer Segmentation

Customers were segmented using **RFM scoring** based on:

* Recency
* Frequency
* Monetary value

Quantile-based scores (1–5) were assigned and grouped into interpretable segments:

* 🏆 Champions
* 🤝 Loyal Customers
* 🌱 Potential Loyalists
* 💰 Big Spenders
* 🆕 New Customers
* ⚠️ At Risk
* 💤 Hibernating

---

# 📊 Cohort Retention Analysis

Customer retention was analyzed using **monthly cohorts** based on each customer’s first purchase month.

The analysis includes:

* 📋 Cohort retention matrix
* 🔥 Retention heatmap
* 📈 Average retention curve
* ⚖️ Weighted retention curve
* 📉 Cohort coverage analysis to account for **censoring effects**

---

# 🔁 Repeat Purchase Behavior

Repeat purchasing dynamics were examined through:

* 🔁 **Repeat purchase rate**
* ⏱ **Time to second purchase**
* 📊 Distribution of **days between first and second purchase**

---

# 🤖 Re-Purchase Risk Modeling

A **logistic regression model** was built to predict whether a customer would make another purchase within **30 days**.

Key features:

* Recency
* Frequency
* Monetary value
* Average Order Value
* Average Basket Size
* Average Unique Items
* Customer Age

A **time-safe cutoff date** was used to prevent **data leakage**.

📊 **Model performance**

**ROC-AUC ≈ 0.69**

---

# ↩️ Returns and Cancellation Analysis

Returns and cancellations were analyzed separately to better estimate customer value.

Metrics calculated:

* Number of **return rows**
* Number of **return invoices**
* **Return revenue**
* **Customer return rate**

---

# 💰 NetRevenue Correction

To avoid overstating customer value:

**NetRevenue = Monetary + ReturnRevenue**

Customers with **NetRevenue ≤ 0** were flagged as **fully returned customers**.

---

# 🚀 Key Results

* 🏆 **Champions generated ~69.20% of NetRevenue**
* 🤝 **Loyal Customers contributed ~13.74% of NetRevenue**
* 🔁 **Repeat purchase rate:** ~65.6%
* ⏱ **Median time to second purchase:** 50 days
* 📊 **Model ROC-AUC:** ~0.692
* 🎯 **13 high-value customers** identified as **high re-purchase risk**
* ↩️ **Fully returned customers:** ~0.44% of the customer base

---

# 📷 Key Visualizations

The analysis includes several visualizations:

* 📊 RFM segmentation distribution
* 🔥 Cohort retention heatmap
* 📈 Average retention curves
* 📉 Cohort coverage analysis
* ⏱ Time-to-second purchase distribution
* 🎯 Model lift chart
* ↩️ Returns behavior by segment

---

# 📁 Repository Structure

```
online-retail-customer-analytics/
│
├── online_retail_analysis.ipynb
├── README.md
├── .gitignore
│
└── images/
    ├── 01_rfm_segments_customers_revenue.png
    ├── 02_cohort_retention_heatmap.png
    ├── 03_avg_retention_curve.png
    ├── 04_weighted_retention_and_cohort_coverage.png
    ├── 05_time_to_second_purchase_hist.png
    ├── 06_lift_chart_deciles.png
    └── 07_returns_by_segment.png
```

---

# ▶️ How to Run

1️⃣ Download the dataset from Kaggle.

2️⃣ Place the dataset CSV in the same directory as the notebook.

3️⃣ Open the notebook:

```
online_retail_analysis.ipynb
```

4️⃣ Run all cells to reproduce the analysis.

---

# ⚠️ Limitations

* The dataset covers approximately **one year**, limiting long-term lifetime value estimation.
* Missing `CustomerID` values reduce coverage for customer-level analysis.
* Later-month cohort retention is based on fewer cohorts due to the observation window.
* Logistic regression is used as an interpretable baseline; more advanced models could improve performance.

---

# 🔮 Future Improvements

Potential extensions include:

* 🌲 Compare logistic regression with **Random Forest or XGBoost**
* 🎯 Apply **probability calibration and threshold optimization**
* 🧩 Convert notebook workflow into **modular Python scripts**
* 📊 Build an **interactive dashboard (Power BI / Tableau)**
* 💰 Implement **customer lifetime value prediction**

---

# 👨‍💻 Author

**Akshara Avinash Sarode**

**LinkedIn: https://www.linkedin.com/in/akshara-avinash-sarode/**
