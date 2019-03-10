# Databases-Assignment_06
## Exercise 1
```sql
SELECT customerNumber, salesRepEmployeeNumber FROM customers 
INNER JOIN employees ON employees.employeeNumber = customers.salesRepEmployeeNumber
INNER JOIN offices ON offices.officeCode = employees.officeCode
WHERE customers.city = offices.city
```
![alt-text](https://github.com/mathiasjepsen/Databases-Assignment_6/blob/master/Exercise_1_Execution_Plan.png "Exercise 1 Execution Plan")

## Exercise 2
```sql

