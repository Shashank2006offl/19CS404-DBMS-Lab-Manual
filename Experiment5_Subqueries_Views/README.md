# Experiment 5: Subqueries and Views

### Name : SHASHANK R
### Register number : 212223230205

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
---
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
SELECT student_name,grade FROM GRADES g WHERE
grade=(SELECT MIN(grade) FROM GRADES WHERE subject=g.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/09478049-7730-4bf8-b1b3-533da63ac621)


**Question 2**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

Employee Table

```sql
SELECT * FROM Employee WHERE age<(SELECT AVG(age) FROM Employee WHERE income>1000000);
```

**Output:**

![image](https://github.com/user-attachments/assets/e62f8497-f56f-40e3-914f-b8ed7c8b97a4)


**Question 3**
---
Write a SQL query to Identify customers whose city is different from the city of the customer with the highest ID

SAMPLE TABLE: customer

```sql
SELECT * FROM customer WHERE city NOT IN (SELECT city FROM customer WHERE id=(SELECT MAX(ID) FROM customer));
```

**Output:**

![image](https://github.com/user-attachments/assets/eaf56e05-f3d6-498a-bb66-06ba722c93a7)

**Question 4**
--
From the following tables write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count.
customer table

```sql
SELECT grade,COUNT(*) FROM customer WHERE
grade>(SELECT AVG(grade) FROM customer WHERE city='New York') GROUP BY grade;
```

**Output:**

![image](https://github.com/user-attachments/assets/3d57743d-38bd-4928-ae42-8a6a146542db)


**Question 5**
---
From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
salesman table , 
orders table

```sql
SELECT * FROM orders WHERE salesman_id=(SELECT salesman_id FROM salesman WHERE name='Paul Adam');
```

**Output:**

![image](https://github.com/user-attachments/assets/46c571cc-e9d5-4d09-b213-4a70b9dc2ade)


**Question 6**
---
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
SALESMAN TABLE AND ORDERS TABLE

```sql
SELECT * FROM ORDERS WHERE salesman_id IN (SELECT salesman_id FROM SALESMAN WHERE city='New York');
```

**Output:**

![image](https://github.com/user-attachments/assets/5a83e287-89b5-4792-935e-36b83da8eebf)


**Question 7**
---
From the following tables, write a SQL query to determine the commission of the salespeople in Paris. Return commission.

salesman table and customer table

```sql
SELECT commission FROM salesman WHERE salesman_id IN (SELECT salesman_id FROM customer WHERE city = 'Paris');
```

**Output:**

![image](https://github.com/user-attachments/assets/5d006fb4-a37f-4b8e-b72f-5cacd283a9d5)



**Question 8**
---
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage
Table Name: Medications (attributes: medication_id, medication_name, dosage)

```sql
SELECT * FROM Medications WHERE dosage=(SELECT MAX(dosage) FROM Medications);
```

**Output:**

![image](https://github.com/user-attachments/assets/f71096ae-282a-4b90-a961-6725809a6f32)


**Question 9**
---
Write a SQL query to Retrieve the names of customers who have a phone number that is not shared with any other customer.

SAMPLE TABLE: customer

```sql
SELECT name FROM customer WHERE phone IN (SELECT phone FROM customer GROUP BY phone HAVING COUNT(phone)=1);
```

**Output:**

![image](https://github.com/user-attachments/assets/1a7e2b77-ccf5-49a7-a17d-93e5c25e3c80)


**Question 10**
---
Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

SAMPLE TABLE: customer

```sql
SELECT name,city FROM customer WHERE
city IN (SELECT city FROM customer WHERE id IN (3,7));
```

**Output:**

![image](https://github.com/user-attachments/assets/8cb3ecd9-7af9-47b2-804d-3b2b9925e55c)



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
