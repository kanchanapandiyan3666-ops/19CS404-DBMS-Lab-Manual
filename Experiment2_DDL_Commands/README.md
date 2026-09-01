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
```
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
```
```
CREATE TABLE Invoices(
InvoiceID INTEGER primary key, InvoiceDate date,
Amount real check(Amount>0),
DueDate date,
OrderID int,
check(DueDate>InvoiceDate),
foreign key(OrderID) references Orders(OrderID)
);
```

**Output:**

<img width="972" height="272" alt="Screenshot 2026-09-01 214422" src="https://github.com/user-attachments/assets/86d28e59-ad83-4b82-8ffb-31c12e8252eb" />


**Question 2**
```
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
```
```
CREATE TABLE Invoices(
InvoiceID INTEGER primary key,
InvoiceDate Date,
DueDate DATE CHECK (DueDate>InvoiceDate),
Amount REAL CHECK (Amount>0)
);
```

**Output:**
<img width="977" height="276" alt="Screenshot 2026-09-01 215627" src="https://github.com/user-attachments/assets/75563444-7bfe-43c0-a567-30ec0b5f75cd" />


**Question 3**
Write a SQL query to Add a new column State as text in the Student_details table.

Sample table: Student_details
```

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
```

```
ALTER TABLE Student_details ADD State TEXT;
```

**Output:**

<img width="987" height="347" alt="Screenshot 2026-09-01 215751" src="https://github.com/user-attachments/assets/1b0f73f8-0fec-43d6-b8b3-bcb3b240926a" />


**Question 4**
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.
```
CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St 4
```     

Note: The City and ZipCode columns will use their default values.


```
insert into Customers (CustomerID,Name,Address) Values (304,'Peter Parker','Spider St');
```

**Output:**

<img width="957" height="291" alt="Screenshot 2026-09-01 215841" src="https://github.com/user-attachments/assets/27af5b07-e2bc-4e22-a7e7-938b0f8184a3" />


**Question 5**
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.
```
EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT
```

```
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary)
VALUES(5,'George Clark','Consultant',NULL,NULL);
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary)
VALUES(7,'Noah Davis','Manager','HR',60000);
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary)
VALUES(8,'Ava Miller','Consultant','IT',NULL);

```

**Output:**

<img width="997" height="286" alt="Screenshot 2026-09-01 215933" src="https://github.com/user-attachments/assets/407b0110-88ce-4a4b-9703-17924d3d0d43" />


**Question 6**
```
Create a table named Events with the following columns:

EventID as INTEGER
EventName as TEXT
EventDate as DATE
```

```
Create table Events(
EventID INTEGER,
EventName TEXT,
EventDate DATE
);
```

**Output:**

<img width="976" height="368" alt="Screenshot 2026-09-01 220026" src="https://github.com/user-attachments/assets/e80af598-0a55-42aa-bcb1-a8e8fe1e0c61" />


**Question 7**
```
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.
```

```
CREATE TABLE Department(
DepartmentID int,DepartmentName text not null unique,Location Text,primary key(DepartmentID));
```

**Output:**
<img width="990" height="286" alt="Screenshot 2026-09-01 220114" src="https://github.com/user-attachments/assets/1c05d985-77de-4a07-b0f2-8e8a944090e4" />



**Question 8**
Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.


```
ALTER TABLE Student_details
ADD COLUMN ParentsNumber number;
ALTER TABLE Student_details 
ADD COLUMN Adhar_Number number;

```

**Output:**
<img width="988" height="358" alt="Screenshot 2026-09-01 220157" src="https://github.com/user-attachments/assets/bf17039e-c046-4f38-aa34-d55aaa5c4102" />


**Question 9**
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished


```
INSERT INTO Books(ISBN,Title,Author,Publisher,YearPublished)
SELECT ISBN,Title,Author,Publisher,YearPublished
FROM Out_of_print_books;
```

**Output:**
<img width="953" height="293" alt="Screenshot 2026-09-01 220241" src="https://github.com/user-attachments/assets/d98a53f0-6261-4a2f-8847-9028aa43afbe" />


**Question 10**
```
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.
```

```
CREATE TABLE Employees(
EmployeeID INT primary key,
FirstName VARCHAR(100) NOT NULL,
LastName VARCHAR(100) NOT NULL,
Email VARCHAR(255) NOT NULL unique,
Salary DECIMAL(10,2) check (salary>0),
DepartmentID INT NOT NULL,
FOREIGN KEY(DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1007" height="397" alt="Screenshot 2026-09-01 220324" src="https://github.com/user-attachments/assets/22146e0a-57cf-4c0d-b188-5c731c580bd1" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
