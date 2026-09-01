# Experiment 5: Subqueries and Views

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

Write a SQL query to List departments with names longer than the average length
Departments Table (attributes: department_id, department_name)
```
SELECT department_id,department_name
from departments
where length(department_name)>(
select avg(length(department_name))
from departments);
```


**Output:**

<img width="646" height="376" alt="Screenshot 2026-09-01 230121" src="https://github.com/user-attachments/assets/e752a049-ff34-48a1-a538-5e6a4913ac87" />


**Question 2**
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.
```
Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000
```
```
select * from CUSTOMERS WHERE SALARY<2500;
```
**Output:**

<img width="727" height="440" alt="Screenshot 2026-09-01 230215" src="https://github.com/user-attachments/assets/a57033e2-f927-47d1-b624-194cf6cc293d" />

**Question 3**
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)
```
SELECT student_name, grade
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
);
```

**Output:**

<img width="681" height="413" alt="Screenshot 2026-09-01 230415" src="https://github.com/user-attachments/assets/1a4ad903-f02c-4ea9-b66a-e38fb20e02c4" />


**Question 4**
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.
```
Sample table: GRADES (attributes: student_id, student_name, subject, grade)

For example:

Result
student_id       student_name     subject          grade
---------------  ---------------  ---------------  ---------------
2                Bob              Math             85
6                Frank            Science          85
7                John             Social           85
```

```
SELECT student_id,student_name,subject,grade from GRADES WHERE (subject,grade) in (select subject,min(grade)
from GRADES GROUP BY subject);
```
**Output:**

<img width="713" height="430" alt="Screenshot 2026-09-01 230515" src="https://github.com/user-attachments/assets/ccdeb9d5-7b57-4c8d-9d14-7ff0ecff6a4c" />

**Question 5**
```
From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```

```
select ord_no,purch_amt,ord_date,customer_id,salesman_id
from orders
where salesman_id=(
select salesman_id
from salesman
where name='Paul Adam');
```

**Output:**


<img width="702" height="362" alt="Screenshot 2026-09-01 230626" src="https://github.com/user-attachments/assets/2df53b6e-d534-4f6e-a421-0f2b13711d70" />


**Question 6**
```
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

name             type

------------   ---------------

id                    INTEGER
name              TEXT
age                 INTEGER
city                 TEXT
income           INTEGER
```
```
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 250000
);
```

**Output:**


<img width="697" height="413" alt="Screenshot 2026-09-01 230751" src="https://github.com/user-attachments/assets/d21926a7-4a32-4049-b5ed-ccd9473040f9" />


**Question 7**
```
From the following tables, write a SQL query to find all orders generated by the salespeople who may work for customers whose id is 3007. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Table Name: orders

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```
```
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM orders
    WHERE customer_id = 3007
);
```

**Output:**

<img width="702" height="441" alt="Screenshot 2026-09-01 230833" src="https://github.com/user-attachments/assets/d21cda27-5343-4d60-95b6-0d5d442f8b90" />


**Question 8**
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade

```
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**


<img width="697" height="421" alt="Screenshot 2026-09-01 230928" src="https://github.com/user-attachments/assets/c072a2cc-cf2e-4313-92ec-20e81246fbe3" />


**Question 9**
```
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

SALESMAN TABLE

name               type
-----------        ----------
salesman_id  numeric(5)
name             varchar(30)
city                 varchar(15)
commission   decimal(5,2)

ORDERS TABLE

name            type
----------      ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int
```
```
SELECT o.ord_no,
       o.purch_amt,
       o.ord_date,
       o.customer_id,
       o.salesman_id
FROM orders o
JOIN salesman s
ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';
```


**Output:**


<img width="721" height="471" alt="Screenshot 2026-09-01 231021" src="https://github.com/user-attachments/assets/4531cec8-9bed-43ca-a709-67b9e9518a0a" />


**Question 10**
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000
```
```
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```
**Output:**

<img width="717" height="360" alt="Screenshot 2026-09-01 231106" src="https://github.com/user-attachments/assets/ab13a7a8-ad4d-4ef7-8bc4-6c5d1bfadeb3" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
