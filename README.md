TASK 6: Sales Trend Analysis Using Aggregations
🎯 Objective

To analyze monthly revenue and order volume trends using SQL aggregation functions and time-based grouping.

🧰 Tools Used

Google Colab

SQLite (via Python sqlite3 library)

Pandas for displaying SQL results

📊 Dataset

Table: online_sales
Columns:

Column	Description
order_id	Unique order identifier
order_date	Date when the order was placed
product_id	Product identifier
amount	Total sale amount for that order
⚙️ Code Overview (Colab Script)
1. Create and Insert Data

A SQLite in-memory database is created and populated with a sample dataset of sales data from Jan–Jun 2024.

2. Analyze Monthly Revenue & Orders

Using SQL:

SELECT 
  STRFTIME('%Y', order_date) AS year,
  STRFTIME('%m', order_date) AS month,
  SUM(amount) AS total_revenue,
  COUNT(DISTINCT order_id) AS total_orders
FROM online_sales
GROUP BY year, month
ORDER BY year, month;

3. Get Top 3 Months by Revenue
SELECT 
  STRFTIME('%Y', order_date) AS year,
  STRFTIME('%m', order_date) AS month,
  SUM(amount) AS total_revenue
FROM online_sales
GROUP BY year, month
ORDER BY total_revenue DESC
LIMIT 3;

📈 Expected Output
Year	Month	Total_Revenue	Total_Orders
2024	01	1700	2
2024	02	2200	2
2024	03	2700	2
2024	04	3000	2
2024	05	5000	3
2024	06	2700	1

🏆 Top 3 Months by Revenue

Year	Month	Total_Revenue
2024	05	5000
2024	04	3000
2024	06	2700
🧠 Key Learnings

How to use aggregate functions: SUM(), COUNT(), etc.

How to group data by month and year using STRFTIME() (SQLite) or EXTRACT() (PostgreSQL/MySQL).

How to find top-performing periods using ORDER BY and LIMIT.

**Conclusion

This task demonstrates how SQL aggregation and time-based grouping can reveal trends in sales data.
By analyzing monthly revenue and order volume, we can identify high-performing months and support better business decision-making.

How to visualize SQL results in Google Colab using Pandas.
