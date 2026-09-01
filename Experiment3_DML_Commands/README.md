# Experiment 3: DML Commands

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
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 
```
name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```
```
update Suppliers set address='58 Lakeview, Magnolia' where supplier_id=5;
```

**Output:**
<img width="992" height="388" alt="Screenshot 2026-09-01 222511" src="https://github.com/user-attachments/assets/44cde5f5-5ba4-45e0-9ca1-efc7c2d73839" />


**Question 2**
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table
```
---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id
```
~~~
update Products set quantity=quantity*1.10;
~~~
**Output:**

<img width="977" height="511" alt="Screenshot 2026-09-01 222604" src="https://github.com/user-attachments/assets/c9f2325a-ee78-4bbb-99f5-c54e5e8b76af" />

**Question 3**
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
```
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT
```
```
update products set reorder_lvl=reorder_lvl*1.30 where category='Food' and quantity<0.50*reorder_lvl;
```
**Output:**

<img width="1016" height="393" alt="Screenshot 2026-09-01 222613" src="https://github.com/user-attachments/assets/1612e653-4757-4db0-862a-1a75bc04fdab" />


**Question 4**
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table
```
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```
update Employees set salary=salary+500,email='updated' where job_id='SA_REP' and commission_pct>0.15;
```
**Output:**

<img width="1003" height="487" alt="Screenshot 2026-09-01 222623" src="https://github.com/user-attachments/assets/17064b4d-6fed-4c84-90b8-d0fcfc9542ee" />


**Question 5**
Write a SQL statement to double the availability of the product with product_id 1.
```
products table

---------------
product_id
product_name
category_id
availability
```
```
update products set availability=availability*2 where product_id=1;
```

**Output:**

<img width="973" height="286" alt="Screenshot 2026-09-01 222633" src="https://github.com/user-attachments/assets/96a5e54e-0b68-4a54-aad5-6224eb5b6d84" />


**Question 6**
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.
```
Sample table: Doctors
attributes : doctor_id, first_name, last_name, specialization
```
```
delete from Doctors where doctor_id=1;
```

**Output:**
<img width="985" height="270" alt="Screenshot 2026-09-01 222642" src="https://github.com/user-attachments/assets/243b2b48-290a-4f74-bf8d-9cb193293fdc" />

**Question 7**
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.
```
Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```
```
delete from Doctors where (Specialization='Pediatrics' or Specialization='Cardiology') and last_name='Brown';
```

**Output:**

<img width="970" height="663" alt="Screenshot 2026-09-01 222656" src="https://github.com/user-attachments/assets/9a76580a-2700-49ad-b91b-0b11bd578032" />


**Question 8**
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000
```
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008     
```
```
delete from Customer where (GRADE='3' OR AGENT_CODE='A008') and OUTSTANDING_AMT<5000;
```

**Output:**

<img width="1010" height="377" alt="Screenshot 2026-09-01 222710" src="https://github.com/user-attachments/assets/26a43042-3875-449d-8486-80b0f21add75" />


**Question 9**
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.
```
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008     
```
```
DELETE FROM Customer where CUST_COUNTRY NOT IN('India','USA');
```

**Output:**

<img width="970" height="516" alt="Screenshot 2026-09-01 222720" src="https://github.com/user-attachments/assets/abae33c0-227d-4a17-859b-33352db424d0" />


**Question 10**
```
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
```
```
DELETE FROM Surgeries where surgery_id=3;
```

**Output:**

<img width="982" height="382" alt="Screenshot 2026-09-01 222759" src="https://github.com/user-attachments/assets/6c0f3c4e-f004-49cf-a2e3-2b526c6c203a" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
