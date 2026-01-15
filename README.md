### SQL Sales Analysis Portfolio Project: Superstore Dataset
In this project, I analyze the Superstore retail dataset using SQL to uncover key business insights. 
I work with a denormalized sales table (orders, customers, products, and regions) and apply filtering, grouping, and window functions to answer practical business questions.

Okay, I'll start from the beginning and introduce you to the data. Next, I'll enter the queries and results.

**Reviewing and verifying data**
```
--Overview of all data
SELECT *
FROM superstore;
```
![Query_1](https://github.com/npcsuspect/my_practice_with_sql/blob/main/Images/Query_1.jpg)
```
SELECT *
FROM superstore
LIMIT 10;
```
![Query_2](https://github.com/npcsuspect/my_practice_with_sql/blob/main/Images/Query_2.jpg)
```
SELECT COUNT(*) AS total_rows
FROM superstore;
```
![Query_3](https://github.com/npcsuspect/my_practice_with_sql/blob/main/Images/Query_3.jpg)
```
SELECT COUNT(*) 
FROM superstore 
WHERE sales IS NULL OR 
  profit IS NULL;
```
![Query_4](https://github.com/npcsuspect/my_practice_with_sql/blob/main/Images/Query_4.jpg)
```
SELECT DISTINCT(order_id) AS uniqe_orders 
FROM superstore;
```
![Query_5](https://github.com/npcsuspect/my_practice_with_sql/blob/main/Images/Query_5.jpg)
