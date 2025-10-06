

# ☕ Coffee Sales Dashboard (SQL + Power BI)

## 📘 Project Overview

This end-to-end analytics project transforms raw coffee sales data into actionable business insights using SQL and Power BI. The goal was to analyze performance trends, customer behavior, and monthly growth patterns to support strategic decision-making.

I used SQL for data cleaning and aggregation, then built an interactive Power BI dashboard to visualize KPIs, top performers, and month-over-month (MoM) changes.

---

## 🧰 Tools & Technologies

| Tool        | Purpose                                      |
|-------------|----------------------------------------------|
| SQL         | Data cleaning, transformation, and analysis  |
| Power BI    | Dashboard development and storytelling        |
| Excel/CSV   | Initial data source                          |
| DAX         | Custom measures for MoM growth and KPIs      |

---

## ⚙️ SQL Workflow

Structured and prepared the dataset for seamless Power BI integration:

- Removed duplicates, handled nulls, standardized formats
- Calculated total revenue, quantity sold, and transaction count
- Created monthly summaries for trend analysis

**Sample Query:**
```sql
SELECT 
    MONTH(transaction_date) AS Month,
    SUM(unit_price * quantity) AS Total_Sales
FROM coffee_sales
GROUP BY MONTH(transaction_date);
```

---

## 📊 Power BI Dashboard Features

- **KPI Cards**: Total Sales, Quantity Sold, Transactions
- **Trend Analysis**: Monthly revenue trajectory
- **MoM Growth**: DAX-driven indicators (▲▼) with % and value change
- **Top 5 Visuals**: Best-selling coffee types and top-performing stores
- **Interactive Filters**: Drill-down by date, product, and region

### 📈 DAX Measure for MoM Growth
```DAX
MOM Growth & Diff Sales =
VAR month_diff = [CM Sales] - [PM Sales]
VAR mom = DIVIDE(month_diff, [PM Sales])
VAR _sign = IF(month_diff > 0, "+", "-")
VAR _trend = IF(month_diff > 0, "▲", "▼")
RETURN
    _trend & " " & FORMAT(mom, "0.0%") & " | " & _sign & FORMAT(month_diff / 1000, "0.0k") & " vs LM"
```

---

## 🔍 Key Business Insights

- 📈 Monthly sales showed consistent growth across most categories
- 🏆 Top 3 coffee types and regions contributed over 60% of total revenue
- 📉 Seasonal dips and peaks revealed cyclical demand patterns
- 🛍️ High-performing stores showed strong repeat customer behavior

---

## 📁 Project Structure

```
Coffee_Sales_Dashboard/
├── data/
│   └── coffee_sales.csv
├── SQL_Scripts/
│   └── coffee_sales_queries.sql
├── PowerBI/
│   └── coffee_dashboard.pbix
├── assets/
│   └── dashboard_preview.png
└── README.md
```

---

## 🧩 How to Use

1. Run the SQL script in MySQL or SQL Server to clean and prepare the data.
2. Load the cleaned dataset into Power BI.
3. Open the `.pbix` file to explore the dashboard and interact with filters.

---

## 👨‍💻 About Me

Hi, I’m **Rishu Anand**, an engineering student passionate about data analytics and business intelligence. I specialize in transforming raw data into compelling visual stories that drive decisions and spark insights.

📬 Email: anandrishu71@gmail.com  

