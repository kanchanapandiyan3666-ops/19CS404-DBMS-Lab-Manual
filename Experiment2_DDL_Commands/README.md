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
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

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

<img width="773" height="285" alt="Screenshot 2026-09-01 215558" src="https://github.com/user-attachments/assets/582833cf-9032-4422-a96e-8377a5f1fb84" />

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

<img width="967" height="488" alt="Screenshot 2026-09-01 215739" src="https://github.com/user-attachments/assets/db18e179-afc0-49b4-9f49-041be734c21c" />

```
ALTER TABLE Student_details ADD State TEXT;
```

**Output:**

<img width="987" height="347" alt="Screenshot 2026-09-01 215751" src="https://github.com/user-attachments/assets/1b0f73f8-0fec-43d6-b8b3-bcb3b240926a" />


**Question 4**
<img width="933" height="350" alt="Screenshot 2026-09-01 215832" src="https://github.com/user-attachments/assets/9666fca3-a4ff-4605-bf4a-18ae61df6ac7" />


```
insert into Customers (CustomerID,Name,Address) Values (304,'Peter Parker','Spider St');
```

**Output:**

<img width="957" height="291" alt="Screenshot 2026-09-01 215841" src="https://github.com/user-attachments/assets/27af5b07-e2bc-4e22-a7e7-938b0f8184a3" />


**Question 5**
<img width="1095" height="407" alt="Screenshot 2026-09-01 215923" src="https://github.com/user-attachments/assets/de4ac1bd-f1c5-4b3d-84cd-dfed231110a0" />


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
<img width="1032" height="333" alt="Screenshot 2026-09-01 220016" src="https://github.com/user-attachments/assets/3aac006e-ea8f-4b21-9dcb-4a337df994fa" />


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
<img width="1106" height="280" alt="Screenshot 2026-09-01 220103" src="https://github.com/user-attachments/assets/0c8627f9-1022-4595-a3d5-96d73d166190" />


```
CREATE TABLE Department(
DepartmentID int,DepartmentName text not null unique,Location Text,primary key(DepartmentID));
```

**Output:**
<img width="990" height="286" alt="Screenshot 2026-09-01 220114" src="https://github.com/user-attachments/assets/1c05d985-77de-4a07-b0f2-8e8a944090e4" />



**Question 8**
<img width="1065" height="337" alt="Screenshot 2026-09-01 220147" src="https://github.com/user-attachments/assets/7ebb33dc-c087-4e1c-9077-7ac9008e6001" />


```
ALTER TABLE Student_details
ADD COLUMN ParentsNumber number;
ALTER TABLE Student_details 
ADD COLUMN Adhar_Number number;

```

**Output:**
<img width="988" height="358" alt="Screenshot 2026-09-01 220157" src="https://github.com/user-attachments/assets/bf17039e-c046-4f38-aa34-d55aaa5c4102" />


**Question 9**
<img width="1021" height="308" alt="Screenshot 2026-09-01 220232" src="https://github.com/user-attachments/assets/a72f6934-a5d4-4596-80ea-c5f9d9bbf884" />


```
INSERT INTO Books(ISBN,Title,Author,Publisher,YearPublished)
SELECT ISBN,Title,Author,Publisher,YearPublished
FROM Out_of_print_books;
```

**Output:**
<img width="953" height="293" alt="Screenshot 2026-09-01 220241" src="https://github.com/user-attachments/assets/d98a53f0-6261-4a2f-8847-9028aa43afbe" />


**Question 10**
<img width="1120" height="325" alt="Screenshot 2026-09-01 220316" src="https://github.com/user-attachments/assets/8b1beeb3-bff6-40cb-bf29-c5bbcbb84769" />


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
