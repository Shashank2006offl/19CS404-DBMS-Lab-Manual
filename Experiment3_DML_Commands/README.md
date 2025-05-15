# Experiment 3: DML Commands
# Name: GURUMURTHY S
# Reference Number:212223230066
## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability

```sql
UPDATE products SET availability = availability*2 WHERE product_id = 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/0164df99-4e21-42c8-bbe8-b5e6572316b8)


**Question 2**
---
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT           
```sql
UPDATE Products SET category = 'Household' WHERE product_name like '%Detergent%';
```

**Output:**

![image](https://github.com/user-attachments/assets/4d9f146f-6fc8-4809-9753-37fe0d9c5604)


**Question 3**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT


```sql
UPDATE PRODUCTS SET reorder_lvl=40  WHERE category = 'Grocery';
```

**Output:**

![image](https://github.com/user-attachments/assets/f3ed1620-0160-40f1-980a-b1aebb4741c7)


**Question 4**
---
For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE Products SET sell_price = CAST(1.35*cost_price as INTEGER) WHERE (sell_price-cost_price) / sell_price < 0.30;
```

**Output:**

![image](https://github.com/user-attachments/assets/310851cd-0c58-41b6-8965-b5845f8ebd9f)

**Question 5**
---
Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE PRODUCTS SET sell_price =sell_price+(sell_price*0.10) WHERE supplier_id=6;
```

**Output:**
![image](https://github.com/user-attachments/assets/749e45c5-91f6-4b51-8e1b-cdb83936192f)


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

Sample table: Customer

```sql
DELETE FROM Customer WHERE CUST_CITY != "New York" AND OUTSTANDING_AMT > 5000;
```

**Output:**

![image](https://github.com/user-attachments/assets/55240228-5147-4c93-845e-2fb67c2057a0)

**Question 7**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

```sql
DELETE FROM Customer WHERE cust_city LIKE 'L%';
```

**Output:**

![image](https://github.com/user-attachments/assets/d0617729-86d7-4d7b-bc01-5b502d8216e8)

**Question 8**
---
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

Sample table: Customer
```sql
DELETE FROM Customer WHERE (GRADE > 2 AND PAYMENT_AMT < (SELECT AVG(PAYMENT_AMT) FROM Customer)) OR OUTSTANDING_AMT>8000;
```

**Output:**

![image](https://github.com/user-attachments/assets/9a6d6bce-1cb7-478b-b4bc-9e68099554ae)

**Question 9**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000

Sample table: Customer
```sql
DELETE FROM Customer WHERE GRADE = 3 AND CUST_NAME LIKE '%BBB%' AND PAYMENT_AMT > 2000;
```

**Output:**

![image](https://github.com/user-attachments/assets/26e9efe7-dd4a-4f1c-98df-c2773b4ca9c0)

**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

 
Sample table: Customer
```sql
DELETE FROM Customer WHERE GRADE<2;
```

**Output:**

![image](https://github.com/user-attachments/assets/69d09450-892e-44a7-b312-f9d43f3e2d64)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
