-- 1. Total revenue, profit and number of orders
SELECT
    COUNT(order_id) AS total_orders,
    ROUND(SUM(revenue), 2) AS total_revenue,
    ROUND(SUM(profit), 2) AS total_profit,
    ROUND(SUM(profit) / NULLIF(SUM(revenue), 0) * 100, 2) AS profit_margin_percent
FROM orders;

-- 2. Monthly revenue trend
SELECT
    DATE_TRUNC('month', order_date)::date AS month,
    ROUND(SUM(revenue), 2) AS monthly_revenue,
    ROUND(SUM(profit), 2) AS monthly_profit,
    COUNT(order_id) AS orders_count
FROM orders
GROUP BY month
ORDER BY month;

-- 3. Revenue by country
SELECT
    c.country,
    ROUND(SUM(o.revenue), 2) AS total_revenue,
    ROUND(SUM(o.profit), 2) AS total_profit,
    COUNT(o.order_id) AS orders_count
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
GROUP BY c.country
ORDER BY total_revenue DESC;

-- 4. Revenue by product category
SELECT
    p.category,
    ROUND(SUM(o.revenue), 2) AS total_revenue,
    ROUND(SUM(o.profit), 2) AS total_profit,
    COUNT(o.order_id) AS orders_count
FROM orders o
JOIN products p ON o.product_id = p.product_id
GROUP BY p.category
ORDER BY total_revenue DESC;

-- 5. Top 10 customers by revenue
SELECT
    c.customer_name,
    c.country,
    c.segment,
    ROUND(SUM(o.revenue), 2) AS total_revenue,
    ROUND(SUM(o.profit), 2) AS total_profit
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
GROUP BY c.customer_name, c.country, c.segment
ORDER BY total_revenue DESC
LIMIT 10;

-- 6. Customer segmentation by spending
WITH customer_revenue AS (
    SELECT
        c.customer_id,
        c.customer_name,
        SUM(o.revenue) AS total_revenue
    FROM customers c
    JOIN orders o ON c.customer_id = o.customer_id
    GROUP BY c.customer_id, c.customer_name
)
SELECT
    customer_id,
    customer_name,
    ROUND(total_revenue, 2) AS total_revenue,
    CASE
        WHEN total_revenue >= 5000 THEN 'High value'
        WHEN total_revenue >= 2000 THEN 'Medium value'
        ELSE 'Low value'
    END AS customer_value_segment
FROM customer_revenue
ORDER BY total_revenue DESC;

-- 7. Month-over-month revenue change
WITH monthly_revenue AS (
    SELECT
        DATE_TRUNC('month', order_date)::date AS month,
        SUM(revenue) AS revenue
    FROM orders
    GROUP BY month
)
SELECT
    month,
    ROUND(revenue, 2) AS revenue,
    ROUND(LAG(revenue) OVER (ORDER BY month), 2) AS previous_month_revenue,
    ROUND(
        (revenue - LAG(revenue) OVER (ORDER BY month)) 
        / NULLIF(LAG(revenue) OVER (ORDER BY month), 0) * 100, 2
    ) AS revenue_growth_percent
FROM monthly_revenue
ORDER BY month;

-- 8. Products with low profitability
SELECT
    p.product_name,
    p.category,
    ROUND(SUM(o.revenue), 2) AS total_revenue,
    ROUND(SUM(o.profit), 2) AS total_profit,
    ROUND(SUM(o.profit) / NULLIF(SUM(o.revenue), 0) * 100, 2) AS profit_margin_percent
FROM orders o
JOIN products p ON o.product_id = p.product_id
GROUP BY p.product_name, p.category
HAVING SUM(o.revenue) > 1000
ORDER BY profit_margin_percent ASC
LIMIT 10;

