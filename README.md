# Databases-Assignment_06
## Exercise 1
```sql
SELECT customerNumber, salesRepEmployeeNumber FROM customers 
INNER JOIN employees ON employees.employeeNumber = customers.salesRepEmployeeNumber
INNER JOIN offices ON offices.officeCode = employees.officeCode
WHERE customers.city = offices.city
```
