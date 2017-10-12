# Code Bits


## Week 8

### View - Product Orders
```sql
SELECT
	orders.orderNumber 'Order Number',
    orders.orderDate 'Date Ordered',
    orders.requiredDate 'Date Required',
    orders.shippedDate 'Date Shipped',
    orders.status 'Status',
    products.productName 'Name',
    details.quantityOrdered 'Quantity',
    details.priceEach 'Price Each',
    products.quantityInStock 'In Stock',
    products.productDescription 'Description',
    details.quantityOrdered * details.priceEach 'Total Cost'
FROM classicmodels.orderdetails details
	JOIN classicmodels.orders orders
		USING (orderNumber)
	JOIN classicmodels.products products
		USING (productCode)
GROUP BY details.orderNumber
ORDER BY details.priceEach DESC
```

### Views - Product Analysis
```sql
```
