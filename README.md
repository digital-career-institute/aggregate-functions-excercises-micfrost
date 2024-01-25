# java-DB-aggregate-function

# java-DB-aggregate-function

### 1. Select the total number of Orders.
```sql
SELECT COUNT(order_id) as total_No_Orders FROM orders;
```
### 2. Select number of orders that have ship region.
```sql
SELECT COUNT(*) AS number_of_orders_with_ship_region
FROM Orders
WHERE ship_region IS NOT NULL;
```
### 3. Select the most expensive product.
```sql
SELECT *
FROM Products
WHERE unit_price = (SELECT MAX(unit_price) FROM Products);
```

### 4. Select total price of order with id = 10258;
```sql
SELECT
    o.Order_ID,
    ROUND(SUM(od.Quantity * od.Unit_Price),2) AS total_price
FROM
    Orders o
JOIN
    Order_Details od ON o.Order_ID = od.Order_ID
WHERE
    o.Order_ID = 10258
GROUP BY
    o.Order_ID;
```
### 5. Select the least expensive product from order with id = 10263
```sql
SELECT
    od.Order_ID,
    p.Product_ID,
    p.Product_Name,
    od.Unit_Price AS unit_price
FROM
    Order_Details od
JOIN
    Products p ON od.Product_ID = p.Product_ID
JOIN
    Orders o ON od.Order_ID = o.Order_ID
WHERE
    o.Order_ID = 10263
	ORDER BY
    od.Unit_Price
LIMIT 1;
```

### 6. Select all products that have price which is above the average price.

### 7. Calculate number of products from category Seafood.

### 8. Sumarize total value of products in orders made in 1996 (before discount).
