# sales-analysis-sql
Sales Analysis — SQL Project
Exploratory analysis of sales data using SQL (PostgreSQL).
The goal was to ansver key business questions about revenue, profitability, customers, and product performance.

Business Questions
#Question
1. What is the total revenue, profit, and number of orders?
2. How does revenue change month by month?
3. Which countries generate the most revenue?
4. Which product categories are most profitable?
5. Who are the top 10 customers by revenue?
6. How can customers be segmented by spending level?
7. What is the month-over-month revenue growth rate?
8. Which products have the lowest profit margin?

Database Schema
Three tables were used:
orders:
order_id, order_date, customer_id, product_id,quantity, discount, revenue,cost, profit
customers:
customer_id, customer_name, country, city, segment
products:
product_id, product_name, category, unit_cost, unit_price 

SQL Techniques Used
Aggregations: SUM, COUNT, ROUND
Joins: INNER JOIN across multiple tables
Grouping and filtering: GROUP BY, HAVING
Date functions: DATE_TRUNC
Window functions: LAG() OVER (ORDER BY ...)
CTEs: WITH for multi-step logic
Conditional logic: CASE WHEN
Safe division: NULLIF to avoid division-by-zero errors

Key Findings
Overall performance — calculated total orders, revenue, profit, and profit margin percentage across all time.
Monthly trend — identified revenue and profit dynamics over time to spot growth or decline periods.
Geography — ranked countries by total revenue to find the most valuable markets.
Product categories — compared categories by revenue and profit to identify the most and least efficient ones.
Top customers — identified the 10 highest-spending customers with their segment and country.
Customer segmentation — split customers into High / Medium / Low value groups based on total spending (thresholds: $5,000 and $2,000).
MoM growth — calculated month-over-month revenue change in % using the LAG() window function.
Low-margin products — found the 10 products with the lowest profit margin among those with revenue above $1,000.

Data Source
Dataset provided for educational purposes, based on a typical retail sales dataset (Kaggle).


Tools


PostgreSQL
DBeaver / pgAdmin
