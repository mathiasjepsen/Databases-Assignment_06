# Databases-Assignment_06
## Exercise 1
```sql
SELECT customerNumber, salesRepEmployeeNumber FROM customers 
INNER JOIN employees ON employees.employeeNumber = customers.salesRepEmployeeNumber
INNER JOIN offices ON offices.officeCode = employees.officeCode
WHERE customers.city = offices.city
```
![alt-text](https://github.com/mathiasjepsen/Databases-Assignment_6/blob/master/Exercise_1_Execution_Plan.png "Exercise 1 Execution Plan")

## Exercise 3
```sql
SELECT 
	o.city AS c_city, 
    SUM(orderdetails.priceEach * orderdetails.quantityOrdered) AS SumOfOrders,
    MAX(p.amount) AS HighestPayment
FROM
	orderdetails
INNER JOIN 
	orders AS c_orders ON orderdetails.orderNumber = c_orders.orderNumber
INNER JOIN 
	customers AS c_custom ON c_orders.customerNumber = c_custom.customerNumber
INNER JOIN 
	employees AS e ON e.employeeNumber = c_custom.salesRepEmployeeNumber
INNER JOIN
	offices AS o ON e.officeCode = o.officeCode
INNER JOIN 
	payments AS p ON p.customerNumber = c_custom.customerNumber
GROUP BY 
	c_city
```
![alt-text](https://github.com/mathiasjepsen/Databases-Assignment_6/blob/master/Exercise_3_Execution_Plan_1.png "Exercise 3 Execution Plan 1")
```sql
SELECT 
	o.city AS c_city, 
    SUM(orderdetails.priceEach * orderdetails.quantityOrdered) OVER(PARTITION BY orderdetails.priceEach) AS SumOfOrders,
    MAX(p.amount) OVER(PARTITION BY p.amount) AS HighestPayment
FROM
	orderdetails
INNER JOIN 
	orders AS c_orders ON orderdetails.orderNumber = c_orders.orderNumber
INNER JOIN 
	customers AS c_custom ON c_orders.customerNumber = c_custom.customerNumber
INNER JOIN 
	employees AS e ON e.employeeNumber = c_custom.salesRepEmployeeNumber
INNER JOIN
	offices AS o ON e.officeCode = o.officeCode
INNER JOIN 
	payments AS p ON p.customerNumber = c_custom.customerNumber
```
![alt-text](https://github.com/mathiasjepsen/Databases-Assignment_6/blob/master/Exercise_3_Execution_Plan_2.png "Exercise 3 Execution Plan 2")

## Exercise 4
```sql

```

