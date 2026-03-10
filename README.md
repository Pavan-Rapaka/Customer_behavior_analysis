# Customer Shopping Behavior Data Analytics Project

## 📌 Overview

This project analyzes customer shopping behavior using a complete data analytics workflow.
The dataset is processed using Python, stored and queried in SQL Server, and visualized using Power BI to generate insights about purchasing patterns, customer demographics, and product categories.

The goal of this project is to demonstrate end-to-end data analysis skills including data cleaning, exploratory data analysis (EDA), SQL querying, and dashboard creation.

---

## 📊 Dataset

**Dataset Name:** Customer Shopping Behavior Dataset

The dataset contains information about customer purchases including:

* Customer ID
* Age
* Gender
* Item Purchased
* Category
* Purchase Amount
* Location
* Size
* Color
* Season
* Subscription Status
* Shipping Type
* Discount Applied
* Promo Code Used
* Previous Purchases
* Payment Method
* Frequency of Purchases

---

## 🛠 Tools & Technologies

| Tool             | Purpose                                   |
| ---------------- | ----------------------------------------- |
| Python (Pandas)  | Data loading and preprocessing            |
| Jupyter Notebook | Data analysis and EDA                     |
| SQL Server       | Database storage and querying             |
| SQL              | Data analysis queries                     |
| Power BI         | Interactive dashboard visualization       |
| GitHub           | Project documentation and version control |

---

## ⚙️ Project Workflow

### 1️⃣ Data Loading

The dataset is loaded into Python using Pandas.

```python
import pandas as pd

df = pd.read_csv("customer_shopping_behavior.csv")
```

---

### 2️⃣ Exploratory Data Analysis (EDA)

Initial exploration was performed using:

* `df.head()`
* `df.info()`
* `df.describe()`
* `df.shape`

This helped understand:

* Data types
* Missing values
* Data distribution

---

### 3️⃣ Data Storage in SQL Server

The dataset was inserted into SQL Server using SQLAlchemy.

```python
df.to_sql("customer", engine, if_exists="replace", index=False)
```

---

### 4️⃣ SQL Analysis

Several SQL queries were executed to extract insights.

Examples:

**Revenue by Gender**

```sql
SELECT gender, SUM(purchase_amount) AS revenue
FROM customer
GROUP BY gender;
```

**Top Products by Category**

```sql
WITH item_counts AS (
SELECT category,
item_purchased,
COUNT(customer_id) AS total_orders,
ROW_NUMBER() OVER (PARTITION BY category ORDER BY COUNT(customer_id) DESC) AS rank
FROM customer
GROUP BY category, item_purchased
)

SELECT * FROM item_counts
WHERE rank <= 3;
```

---

### 5️⃣ Power BI Dashboard

An interactive dashboard was built to visualize:

* Total Customers
* Revenue by Category
* Subscription Status
* Purchase Distribution
* Product Category Analysis
* Customer Demographics

---

## 📈 Dashboard Insights

Key insights obtained:

* Clothing category generates the highest sales.
* Majority of customers do not have subscription plans.
* Certain products dominate purchase frequency in each category.
* Younger customers tend to purchase more frequently.

---

## ▶️ How to Run the Project

1. Download the dataset.
2. Open the Jupyter Notebook.
3. Install required libraries:

```
pip install pandas sqlalchemy pyodbc
```

4. Run the Python notebook to load the data.
5. Insert data into SQL Server.
6. Execute SQL queries for analysis.
7. Open the Power BI dashboard (.pbix file).

---

## 📂 Project Structure

```
Customer-Shopping-Behavior-Analysis
│
├── dataset
│   └── customer_shopping_behavior.csv
│
├── notebooks
│   └── analysis.ipynb
│
├── sql
│   └── queries.sql
│
├── dashboard
│   └── customer_behavior_dashboard.pbix
│
└── README.md
```

---

## 🎯 Project Outcome

This project demonstrates a full data analytics pipeline including:

* Data ingestion
* Data exploration
* SQL analysis
* Data visualization
* Business insight generation

---

## 👨‍💻 Author

**Pavan Shekar**
MCA – Computer Science & IT
Data Analytics & Software Development Enthusiast
