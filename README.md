# 🛒 E-Commerce Business Intelligence & Customer Churn Prediction

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![SQL](https://img.shields.io/badge/SQL-SQLite3-orange.svg)](https://www.sqlite.org/)
[![Machine Learning](https://img.shields.io/badge/Scikit--Learn-Random%20Forest%20%7C%20K--Means-green.svg)](https://scikit-learn.org/)
[![BI Dashboard](https://img.shields.io/badge/BI-Google%20Looker%20Studio%20%7C%20Plotly-purple.svg)](https://lookerstudio.google.com/)

## 📌 Project Overview
An end-to-end Data Analytics and Machine Learning capstone project analyzing **2,000+ e-commerce order records** to uncover revenue drivers, identify discount-induced margin erosion, segment customers by purchasing behavior, and predict customer churn.

* **📓 Interactive Notebook:** `Ecommerce_Analytics_Capstone.ipynb`
* **📊 Live Looker Studio Dashboard:** *[Paste your Looker Studio public share link here]*
* **🌐 Interactive Plotly Dashboard:** `Ecommerce_Executive_Dashboard.html`

---

## 🛠️ Tech Stack & Tools
* **Data Wrangling & Analysis:** Python (`Pandas`, `NumPy`)
* **Database & Querying:** SQL (`SQLite3` — CTEs, Window Functions: `DENSE_RANK`, `LAG`)
* **Statistical Analysis:** `SciPy` (Independent Two-Sample T-Test, Chi-Square Test of Independence)
* **Data Visualization:** `Matplotlib`, `Seaborn`, `Plotly`, and **Google Looker Studio**
* **Machine Learning:** `Scikit-Learn` (`StandardScaler`, `K-Means Clustering`, `Random Forest Classifier`)

---

## 🔄 End-to-End Analytics Workflow

### 1. Data Cleaning & Feature Engineering
* **Deduplication & Standardization:** Removed 25 duplicate order records and normalized inconsistent `City` formatting (e.g., `' surat '`, `'MUMBAI'` $\rightarrow$ `'Surat'`, `'Mumbai'`).
* **Missing Value Imputation:** Imputed missing `Sales` values using the **Median** (robust to skew) and missing `Payment_Mode` entries using the **Mode**.
* **Outlier Treatment (IQR Method):** Detected extreme sales anomalies and capped values at the upper IQR threshold of **`₹34,512.37`**.
* **Feature Engineering:** Created `Order_Month` and `Profit_Margin_Pct` to evaluate monthly trends and unit profitability.

### 2. SQL Business Analytics (`SQLite3`)
* **Top Customers per City:** Used Common Table Expressions (CTEs) and `DENSE_RANK()` partitioned by city to identify top revenue-generating customers (e.g., `CUST-545` leading Surat with **`₹106,744.62`** in delivered spend).
* **Month-over-Month (MoM) Growth:** Applied the `LAG()` window function to track monthly revenue shifts and seasonal dips.

### 3. Exploratory Data Analysis (EDA) & Hypothesis Testing
* **Discount vs. Profitability:** Visualized average profit across discount tiers, pinpointing that **discounts at `35%` push orders into net negative profit (loss)**.
* **Two-Sample T-Test (`0%` vs. `35%` Discount Profit):** Confirmed a statistically significant drop in profitability at high discount levels ($p < 0.05$).
* **Chi-Square Test (`Payment_Mode` vs. `Customer_Churn`):** Tested independence ($p = 0.0647 > 0.05$), showing payment method alone does not significantly drive churn.

### 4. Machine Learning (Segmentation & Churn Prediction)
* **Customer Segmentation (`K-Means Clustering`):** Grouped customers into **3 distinct segments** (High-Value VIPs, Regular Buyers, and Budget Shoppers) based on `Total_Spend` and `Total_Orders`.
* **Churn Prediction (`Random Forest Classifier`):**
  * **Baseline Model:** Achieved `69.38%` accuracy with only **`9.09%` Recall** on churned customers due to severe class imbalance.
  * **Tuned Model:** Engineered behavioral signals (`Cancelled`/`Returned` status and negative profit) and applied `class_weight='balanced'`, boosting **Churn Recall to `78.29%`** and **Overall Accuracy to `89.88%`**.

---

## 💡 Key Business Recommendations
1. **Cap Promotional Discounts at 25%:** Eliminate blanket `35%` discounts on standard categories to prevent direct margin erosion.
2. **Proactive Retention for Returned/Cancelled Orders:** Trigger automated customer support outreach whenever an order is cancelled or returned, as this is the strongest predictor of churn.
3. **VIP Loyalty Program:** Target the top K-Means cluster (high-spend repeat buyers) with exclusive early access rather than heavy price discounts.

---

## 👤 Author
**Shiva Singh**  
Data Analyst | SQL • Python • Power BI • Looker Studio • Generative AI  
* **GitHub:** [github.com/shivasingh0007](https://github.com/shivasingh0007)  
* **Email:** Shivasingh604@gmail.com
