# Pizza Sales Analysis 🍕

This dataset was obtained on [Kaggle](https://www.kaggle.com/datasets/shilongzhuang/pizza-sales)!
All data in here are only from a single year.

Let's start by seeing how many orders we have on this dataset:

```sql
SELECT 
  COUNT(*)
FROM
  pizza_sales
```

<img src="https://github.com/fernandoprim/Assets/blob/main/Pizza_sales/Total.png"/>

<p>We got 48620 pizza orders in total!</p>
Let's start with our analysis.

## 1. What is the average order price?

```sql
SELECT 
  TRUNC(AVG(total_price), 2) AS average_order_price
FROM
  pizza_sales
```

### Outcome:

<img src="https://github.com/fernandoprim/Assets/blob/main/Pizza_sales/Q1.png"/>

## 2. What is the average order price for each category?

```sql
SELECT
  pizza_category AS category,
  TRUNC(AVG(total_price), 2) AS average_order_price
FROM
  pizza_sales
GROUP BY
  pizza_category
```

### Outcome:

<img src="https://github.com/fernandoprim/Assets/blob/main/Pizza_sales/Q2.png"/>

## 3. What is the best selling pizza?

```sql
SELECT
  pizza_name,
  COUNT(order_id) AS Sales
FROM
  pizza_sales
GROUP BY
  pizza_name
ORDER BY
  Sales DESC
LIMIT 1
```

### Outcome:

<img src="https://github.com/fernandoprim/Assets/blob/main/Pizza_sales/Q3.png"/>

## 4. What is the worst selling pizza?

```sql
SELECT
  pizza_name,
  COUNT(order_id) AS Sales
FROM
  pizza_sales
GROUP BY
  pizza_name
ORDER BY
  Sales ASC
LIMIT 1
```

### Outcome:

<img src="https://github.com/fernandoprim/Assets/blob/main/Pizza_sales/Q4.png"/>

## 5. What is the average ammount of sales per month?

```sql
SELECT
  TO_CHAR(order_date, 'Month') AS month,
  COUNT(order_id) AS sales
FROM
  pizza_sales
GROUP BY
  month,
  EXTRACT(MONTH FROM order_date)
ORDER BY
  EXTRACT(MONTH FROM order_date)
```

### Outcome:

<img src="https://github.com/fernandoprim/Assets/blob/main/Pizza_sales/Q5.png"/>
