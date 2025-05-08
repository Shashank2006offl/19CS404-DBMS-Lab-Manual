# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```sql
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary)
VALUES (1,"Sarah Parker","Manager","HR",60000);
```

**Output:**

![image](https://github.com/user-attachments/assets/c6ed276a-7d12-49d7-905d-11e80c51db87)


**Question 2**
---
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
INSERT INTO Books (ISBN,Title,Author,Publisher,YearPublished)
SELECT ISBN,Title,Author,Publisher,YearPublished FROM Out_of_print_books;
```

**Output:**

![image](https://github.com/user-attachments/assets/ecd2ff1d-cf28-4707-aa7b-e1bbe115978b)

**Question 3**
---
In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

ProductID   Name              Category    Price       Stock
----------  ---------------   ----------  ----------  ----------
106         Fitness Tracker   Wearables
107         Laptop            Electronics  999.99      50
108         Wireless Earbuds  Accessories              100
 
```sql
INSERT INTO Products(ProductID,Name,Category)
VALUES (106,"Fitness Tracker","Wearables");
INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES (107,"Laptop","Electronic",999.99,50);
INSERT INTO Products(ProductID,Name,Category,Stock)
VALUES (108 ,"Wireless Earbud","Accessorie",100);

```

**Output:**

![image](https://github.com/user-attachments/assets/820f795c-1bf4-46f0-8e8b-a95d43db2e00)

**Question 4**
---
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
CREATE TABLE Products(ProductID INTEGER PRIMARY KEY, ProductName TEXT UNIQUE NOT NULL, Price REAL CHECK(Price>0), StockQuantity INTEGER CHECK(StockQuantity>0));
```

**Output:**

![image](https://github.com/user-attachments/assets/5fc6819f-3139-49e2-a234-40d91a0ebe40)

**Question 5**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY, 
InvoiceDate DATE,
Amount REAL CHECK(Amount>0),
DueDate DATE CHECK(Duedate>InvoiceDate),
OrderID INTEGER,
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID));
```

**Output:**

![image](https://github.com/user-attachments/assets/c6cf140a-fc35-4a47-94ff-1d29a63eb545)

**Question 6**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY, 
InvoiceDate DATE,
DueDate DATE CHECK(Duedate>InvoiceDate),
Amount REAL CHECK(Amount>0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/bc9b5149-c661-4c31-ae18-f38ac861247b)

**Question 7**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY, 
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT CHECK(length(icom_id)=4),
FOREIGN KEY (icom_id) REFERENCES company(com_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

**Output:**

![image](https://github.com/user-attachments/assets/ebc27971-d5c7-49b1-bd46-757a226dffc5)

**Question 8**
---
Create a table named Events with the following columns:

EventID as INTEGER
EventName as TEXT
EventDate as DATE

```sql
CREATE TABLE Events(
EventID INTEGER,
EventName TEXT,
EventDate DATE
);
```

**Output:**

![image](https://github.com/user-attachments/assets/e76d34e3-07f8-47ad-8ebd-6d15343b04a0)

**Question 9**
---
Write an SQL query to change the name of the column id to employee_id in the table employee.

```sql
ALTER TABLE employee
RENAME COLUMN "id" TO "employee_id";
```

**Output:**

![image](https://github.com/user-attachments/assets/9f72cd86-7380-4ecf-90c4-c4c38bb143bb)

**Question 10**
---
Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
ALTER TABLE Companies
ADD COLUMN designation varchar(50);
ALTER TABLE Companies
ADD COLUMN net_salary number;
```

**Output:**

![image](https://github.com/user-attachments/assets/3f385611-a83e-472e-b136-71d03337a7b3)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
