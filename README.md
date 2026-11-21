# sales-analysis-sql
Sales Analysis — SQL Project
Exploratory analysis of sales data using SQL (PostgreSQL).
The goal was to answer key business questions about revenue, profitability, customers, and product performance.

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

## Key Findings & Conclusion

### 1. Overall Sales Performance
The analysis of **5,000 orders** revealed total revenue of **$5,888,816.91** and total profit of **$2,561,882.55**, resulting in a **43.5% profit margin**. This indicates strong overall profitability.

### 2. Monthly Revenue Trend
Monthly revenue fluctuated throughout the analyzed period, with both increases and decreases in sales. These changes highlight the importance of monitoring monthly performance to identify trends and potential opportunities for improvement.

### 3. Revenue by Country
**Germany** generated the highest revenue (**$1,017,404.70**) from **913 orders**, followed by **Ukraine** with **$1,004,213.64** from **862 orders**. These countries represent the strongest markets by revenue.

### 4. Product Category Performance
**Sports** was the best-performing category, generating **$1,691,908.63** in revenue and **$756,552.22** in profit. **Furniture** recorded the lowest revenue among the five categories.

### 5. Customer and Product Analysis
Customer segmentation identified **high-value customers**, while profitability analysis highlighted products with relatively low profit margins that could benefit from further optimization.

### Conclusion
The analysis demonstrates **strong profitability**, with **Sports** leading product sales and **Germany** generating the highest revenue. The results suggest opportunities to optimize low-margin products, focus on valuable customer segments, and improve sales strategies based on monthly performance.

Data Source
Dataset provided for educational purposes, based on a typical retail sales dataset (Kaggle).
