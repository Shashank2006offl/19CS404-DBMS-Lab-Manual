# Experiment 6: Joins

### Name : SHASHANK R
### Register Number : 212223230205

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman_id values that have more than one associated customer.

```sql
SELECT s.name,c.cust_name,c.city,c.grade,c.salesman_id FROM Salesman s
LEFT JOIN Customer c ON s.salesman_id=c.salesman_id WHERE
s.salesman_id IN (SELECT salesman_id FROM Customer GROUP BY salesman_id HAVING COUNT(*)>1);
```

**Output:**

![image](https://github.com/user-attachments/assets/ca1eea9e-d3b9-4ccb-9575-9ce0d20f7761)


**Question 2**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

Sample table: customer,orders,salesman

```sql
SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt AS 'Order Amount',s.name,s.commission FROM customer c
LEFT JOIN orders o ON c.customer_id=o.customer_id LEFT JOIN salesman s ON o.salesman_id=s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/ee43cace-2277-4c43-b65b-d8e706b1573b)


**Question 3**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

Sample table: customer,salesman

```sql
SELECT c.cust_name,c.city,c.grade,s.name AS 'Salesman',s.city FROM customer c
JOIN salesman s ON c.salesman_id=s.salesman_id ORDER BY customer_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/99d9cf65-75f4-4fdf-a05a-f046133aeea4)


**Question 4**
---
Write the SQL query that achieves the selection of the date of birth from the "patients" table (aliased as "p") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id
APPOINTMENTS TABLE:ATTRIBUTES - appointment_id, patient_id, doctor_id, appointment_date

```sql
SELECT p.date_of_birth,a.appointment_id,a.patient_id,a.doctor_id,a.appointment_date FROM PATIENTS p
INNER JOIN APPOINTMENTS a ON p.patient_id=a.patient_id WHERE p.first_name='Alice';
```

**Output:**

![image](https://github.com/user-attachments/assets/7f1062e8-ec91-4c47-b958-b05b498f5106)


**Question 5**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

PATIENTS TABLE:ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id
TEST_RESULT TABLES:ATTRIBUTES - result_id, patient_id, test_name, result, test_date

```sql
SELECT p.first_name AS 'patient_name' FROM PATIENTS p
INNER JOIN TEST_RESULTS t ON p.patient_id=t.patient_id WHERE t.test_name='Blood Pressure';
```

**Output:**

![image](https://github.com/user-attachments/assets/8649e9fc-af29-4a42-8cbd-9d575f126404)


**Question 6**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

Sample table: orders,customer,salesman

```sql
SELECT o.ord_no,o.purch_amt,o.ord_date,c.cust_name,c.city AS 'customer_city',c.grade,s.name AS 'salesman_name',s.city AS 'salesman_city',s.commission
FROM orders o JOIN customer c ON o.customer_id=c.customer_id JOIN salesman s ON c.salesman_id=s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/dd9b7630-3950-416c-b4a6-58de1cffdf72)


**Question 7**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for test results with a test date between '2024-03-01' and '2024-03-31'.

PATIENTS TABLE:ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id
TEST_RESULT TABLES:ATTRIBUTES - result_id, patient_id, test_name, result, test_date

```sql
SELECT p.patient_id,p.first_name,p.last_name,p.date_of_birth,p.admission_date,p.discharge_date,p.doctor_id FROM PATIENTS p
INNER JOIN TEST_RESULTS t ON p.patient_id=t.patient_id WHERE t.test_date BETWEEN '2024-03-01' AND '2024-03-31';
```

**Output:**

![image](https://github.com/user-attachments/assets/6603d36a-30d6-45d1-a70a-b49b0cc095c8)


**Question 8**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'London'.

```sql
SELECT s.name FROM salesman s LEFT JOIN customer c ON s.salesman_id=c.salesman_id WHERE c.city='London';
```

**Output:**

![image](https://github.com/user-attachments/assets/70d2cbe4-2ad8-4faa-b82c-0dd297f10d79)


**Question 9**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

Sample table: customer,orders

```sql
SELECT o.ord_no,o.purch_amt,c.cust_name,c.city FROM orders o
JOIN  customer c ON o.customer_id=c.customer_id WHERE o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**

![image](https://github.com/user-attachments/assets/75e1de62-a7d9-423c-a5c1-fd32b58745cf)


**Question 10**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

Sample table: orders,customer

```sql
SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt AS 'Order Amount' FROM customer c
LEFT OUTER JOIN orders o ON c.customer_id=o.customer_id ORDER BY o.ord_date;
```

**Output:**

![image](https://github.com/user-attachments/assets/9e799f6f-ebf5-43d3-a290-96453c6d7a2a)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
