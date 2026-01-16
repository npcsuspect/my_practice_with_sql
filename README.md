### SQL Sales Analysis Portfolio Project: Superstore Dataset
In this project, I analyze the Superstore retail dataset using SQL to uncover key business insights. 
I work with a denormalized sales table (orders, customers, products, and regions) and apply filtering, grouping, and window functions to answer practical business questions.

**Reviewing and verifying data**
```
--Overview of all data
SELECT *
FROM superstore;
```
![Query_1](https://github.com/npcsuspect/my_practice_with_sql/blob/main/Images/Query_1.jpg)
```
--Let's select 10 lines for review 
SELECT *
FROM superstore
LIMIT 10;
```
![Query_2](https://github.com/npcsuspect/my_practice_with_sql/blob/main/Images/Query_2.jpg)
```
--I will determine the number of rows in the table
SELECT COUNT(*) AS total_rows
FROM superstore;
```
![Query_3](https://github.com/npcsuspect/my_practice_with_sql/blob/main/Images/Query_3.jpg)
```
--I will check the table for NULL values in columns that are important for calculation
SELECT COUNT(*) 
FROM superstore 
WHERE sales IS NULL OR 
  profit IS NULL;
```
![Query_4](https://github.com/npcsuspect/my_practice_with_sql/blob/main/Images/Query_4.jpg)
```
--You can also view unique orders and count their number
SELECT DISTINCT(order_id) AS uniqe_orders 
FROM superstore;
```
![Query_5](https://github.com/npcsuspect/my_practice_with_sql/blob/main/Images/Query_5.jpg)
```
--Basic statistics, calculating the average or total value
SELECT 
    ROUND(AVG(sales), 2) AS avg_sales,
    ROUND(SUM(sales), 2) AS total_sales,
    ROUND(AVG(profit), 2) AS avg_profit,
    ROUND(SUM(profit), 2) AS total_profit
FROM superstore;
```

```
--GROUP BY, category segmentation, statistics
SELECT 
    category,
    COUNT(*) AS orders_count,
    ROUND(SUM(sales), 0) AS total_sales,
    ROUND(SUM(profit), 0) AS total_profit
FROM superstore
GROUP BY category
ORDER BY total_sales DESC;
```

**The results show that Technology is the leader in sales. Furniture is unprofitable**
```
--Data Segmentation
--Performed sales segmentation by region for the Consumer category using grouping (GROUP BY) and aggregate margin calculations.
SELECT 
    region,
    segment,
    ROUND(SUM(sales), 0) AS total_sales,
    ROUND(AVG(profit) / AVG(sales) * 100, 2) AS profit_margin_pct
FROM superstore
WHERE segment = 'Consumer'       -- 1. Filtration
GROUP BY region, segment       -- 2. Grouping
ORDER BY total_sales DESC;         -- 3. Sorting
```

**The results show that the Western region is the best in terms of sales.
The region with the lowest margin is Central.**
