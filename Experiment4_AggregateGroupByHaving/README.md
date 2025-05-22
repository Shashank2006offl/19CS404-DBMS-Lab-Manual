# Experiment 4: Aggregate Functions, Group By and Having Clause

### Name : Shashank R
### Register Number : 212223230205

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```
**Question 1**
---
How many prescriptions were written for each medication?
Sample table:Prescriptions Table

```sql
SELECT Medication,COUNT(*) AS TotalPrescriptions FROM Prescriptions GROUP BY Medication;
```

**Output:**

![image](https://github.com/user-attachments/assets/33eca2bd-8e56-4500-8273-b62f43eb6200)

**Question 2**
--
How many appointments are scheduled for each patient?
Sample table: Appointments Table

```sql
SELECT PatientID,COUNT(*) AS TotalAppointments FROM Appointments GROUP BY PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/320c3321-98ef-42e9-8fc8-8e4316548b0e)



**Question 3**
---
How many appointments are scheduled in each hour of the day?
Sample table:Appointments Table

```sql
SELECT strftime('%H',AppointmentDateTime) AS HourOfDay,
COUNT(*) AS TotalAppointments FROM Appointments GROUP BY HourOfDay;
```

**Output:**

![image](https://github.com/user-attachments/assets/9cb88d9a-428f-4b10-bced-c0e8bd94fa25)


**Question 4**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 
Table: employee

```sql
SELECT AVG(income) AS avg_income FROM employee WHERE name LIKE 'A%';
```

**Output:**

![image](https://github.com/user-attachments/assets/34a737bb-48cd-40ee-90c1-ebff0645244e)


**Question 5**
---
Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city
Table: customer

```sql
SELECT AVG(LENGTH(email)) AS avg_email_length_below_30 FROM customer WHERE city="Mumbai";
```

**Output:**

![image](https://github.com/user-attachments/assets/3bdd895b-fc92-468a-81b3-3ec39f0f8f9b)


**Question 6**
---
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.
Sample table: employee

```sql
SELECT COUNT(DISTINCT age) AS COUNT FROM employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/93209a82-d5ab-4445-87d7-94db9d6e978a)


**Question 7**
---
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.
Note: Inventory attribute contains amount of fruits

Table: fruits
```sql
SELECT SUM(inventory) AS total FROM fruits WHERE unit='LB';
```

**Output:**

![image](https://github.com/user-attachments/assets/42854056-b20b-4908-a1af-a2cd0f35be5b)


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.

Sample table: employee

```sql
SELECT age,AVG(income) AS 'AVG(income)' FROM employee
GROUP BY age HAVING AVG(income) BETWEEN 300000 AND 500000;
```

**Output:**

![image](https://github.com/user-attachments/assets/f2d65799-a485-423d-b7e2-eb3090cec963)


**Question 9**
---
Write a SQL query to identify the cities (addresses) where the average salary is greater than Rs. 5000, as per the "customer1" table.

Sample table: customer1

```sql
SELECT address,AVG(salary) AS 'AVG(salary)' FROM customer1
GROUP BY address HAVING AVG(salary)>5000;
```

**Output:**

![image](https://github.com/user-attachments/assets/53d9ddee-2737-4919-ae92-3f7816b5dca7)


**Question 10**
---
Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.

Sample table: products

```sql
SELECT category_id,COUNT(category_id) AS COUNT FROM products
GROUP BY category_id HAVING category_id>2;
```

**Output:**

![image](https://github.com/user-attachments/assets/42ea05e7-ae5d-4fc4-8797-a3ae3d84bcce)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
