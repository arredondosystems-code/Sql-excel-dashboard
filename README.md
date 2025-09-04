

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7f7e2e0b-58ea-4b79-81e8-6e64d72c7a2b" />


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/db624833-f21d-4c73-94df-0037c23bb1fd" />

PIZZA SALES SQL QUERIES
A. KPI’s
1. Total Revenue:
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;


 <img width="287" height="131" alt="image" src="https://github.com/user-attachments/assets/86c56ccd-a4cc-442d-ac7c-85fc1a6b2991" />

 
2. Average Order Value
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales


<img width="305" height="133" alt="image" src="https://github.com/user-attachments/assets/cf597603-5eb0-4a92-901d-a8a3b84b45eb" />

3. Total Pizzas Sold
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales
 

<img width="311" height="135" alt="image" src="https://github.com/user-attachments/assets/b1307ba3-a59c-436f-823e-d16801a16588" />


4. Total Orders
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales



<img width="315" height="128" alt="image" src="https://github.com/user-attachments/assets/6c3207e8-971f-48d7-9790-1dbcab75e180" />



5. Average Pizzas Per Order
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza_sales



<img width="325" height="141" alt="image" src="https://github.com/user-attachments/assets/6de81def-fecd-4cfe-9f5a-87fdb5e18945" />


 


B. Daily Trend for Total Orders
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)
Output:


<img width="367" height="325" alt="image" src="https://github.com/user-attachments/assets/6911c49a-748e-4ea4-bf33-2da22f634fab" />

 
C. Hourly Trend for Orders
SELECT DATEPART(HOUR, order_time) as order_hours, COUNT(DISTINCT order_id) as total_orders
from pizza_sales
group by DATEPART(HOUR, order_time)
order by DATEPART(HOUR, order_time)
Output


<img width="414" height="580" alt="image" src="https://github.com/user-attachments/assets/21cb3e71-5850-4744-9494-405d139a8458" />



 
D. % of Sales by Pizza Category
SELECT pizza_category, CAST(SUM(total_	price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category
Output


<img width="601" height="275" alt="image" src="https://github.com/user-attachments/assets/1449d344-af45-42d1-b5da-8eaa3a3e8811" />

 
E. % of Sales by Pizza Size
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size
Output


 <img width="549" height="318" alt="image" src="https://github.com/user-attachments/assets/0e0b7b24-0f53-43de-9290-2df7346963a1" />


F. Total Pizzas Sold by Pizza Category
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC
Output


<img width="565" height="271" alt="image" src="https://github.com/user-attachments/assets/abf78c7d-d7cd-4419-9d60-8d78fed4bffa" />

 
G. Top 5 Best Sellers by Total Pizzas Sold
SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC
Output
 

<img width="716" height="283" alt="image" src="https://github.com/user-attachments/assets/337712a6-a578-4a90-ab37-c71b6492cec6" />




H. Bottom 5 Best Sellers by Total Pizzas Sold
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC
Output
 

<img width="667" height="305" alt="image" src="https://github.com/user-attachments/assets/9c66611e-1be3-4153-8881-dc261733b1ca" />



<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d99b525c-b7b4-46b2-8a1c-79506162afdd" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e24a240a-3dcf-4a5e-a78a-5fc2d66bf224" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9d8d223c-05d2-4b8a-aa6e-321a725698d4" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/32ec3b57-9bb8-459c-b7f5-c00ee5cdcdc9" />
