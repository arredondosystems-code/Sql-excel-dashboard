

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7f7e2e0b-58ea-4b79-81e8-6e64d72c7a2b" />


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/db624833-f21d-4c73-94df-0037c23bb1fd" />

PIZZA SALES SQL QUERIES
A. KPI’s
1. Total Revenue:
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
 
2. Average Order Value
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales
 
3. Total Pizzas Sold
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales
 
4. Total Orders
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales
 
5. Average Pizzas Per Order
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza_sales
 
B. Daily Trend for Total Orders
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)
Output:
 
C. Hourly Trend for Orders
SELECT DATEPART(HOUR, order_time) as order_hours, COUNT(DISTINCT order_id) as total_orders
from pizza_sales
group by DATEPART(HOUR, order_time)
order by DATEPART(HOUR, order_time)
Output
 
D. % of Sales by Pizza Category
SELECT pizza_category, CAST(SUM(total_	price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category
Output
 
E. % of Sales by Pizza Size
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size
Output
 

F. Total Pizzas Sold by Pizza Category
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC
Output
 
G. Top 5 Best Sellers by Total Pizzas Sold
SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC
Output
 




H. Bottom 5 Best Sellers by Total Pizzas Sold
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC
Output
 



<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d99b525c-b7b4-46b2-8a1c-79506162afdd" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e24a240a-3dcf-4a5e-a78a-5fc2d66bf224" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9d8d223c-05d2-4b8a-aa6e-321a725698d4" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/32ec3b57-9bb8-459c-b7f5-c00ee5cdcdc9" />
