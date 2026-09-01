<img width="563" height="433" alt="image" src="https://github.com/user-attachments/assets/bb5d781f-14f2-4625-bc14-a3aaab7f07a7" /># Experiment 4: Aggregate Functions, Group By and Having Clause

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
<img width="832" height="200" alt="Screenshot 2026-09-01 223604" src="https://github.com/user-attachments/assets/53c0f259-e547-4205-a985-4265f62348c5" />
```
select PatientID,
COUNT(PatientID) AS AvgMedications
from MedicalRecords
group by PatientID;
```
**Output:**

<img width="586" height="552" alt="Screenshot 2026-09-01 223612" src="https://github.com/user-attachments/assets/a2ea8d76-43b7-44c4-ad61-729f9171d815" />


**Question 2**
<img width="825" height="208" alt="Screenshot 2026-09-01 223621" src="https://github.com/user-attachments/assets/b45ac859-01e8-4d23-ac56-deaf1f729d98" />

```
SELECT DoctorID,
COUNT(DoctorID) as TotalAppointments
from Appointments
group by DoctorID;
```

**Output:**
<img width="586" height="545" alt="Screenshot 2026-09-01 223627" src="https://github.com/user-attachments/assets/c68b21b1-d720-43a5-95df-a965c38ca604" />


**Question 3**
How many patients are covered by each insurance company?
```
Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT
```
```
select InsuranceCompany,
count(patientID) as TotalPatients
from Insurance
group by InsuranceCompany;

```
**Output:**
<img width="608" height="591" alt="Screenshot 2026-09-01 224033" src="https://github.com/user-attachments/assets/0b18767e-2733-48ad-8148-a4792bebfe12" />


**Question 4**
Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count. 

Note: Inventory attribute contains amount of fruits

Table: fruits
```
name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
```
```
select sum(inventory) as total_available_amount
from fruits
where price>0.5;
```
**Output:**
<img width="501" height="325" alt="Screenshot 2026-09-01 224514" src="https://github.com/user-attachments/assets/a7e46c68-7792-4413-a3e6-e30ae3d0620b" />


**Question 5**
<img width="942" height="397" alt="Screenshot 2026-09-01 224522" src="https://github.com/user-attachments/assets/1cb87344-915f-465f-8400-241cc3b21c9e" />
```
select sum(workhour) as 'Total working hours'
from employee1;
```

**Output:**

<img width="526" height="322" alt="Screenshot 2026-09-01 224530" src="https://github.com/user-attachments/assets/28102d76-70df-412a-9fa6-e17c250f88dc" />


**Question 6**
```
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```
```
select 
avg(purch_amt) as AVERAGE FROM orders;
```

**Output:**
<img width="385" height="332" alt="Screenshot 2026-09-01 224657" src="https://github.com/user-attachments/assets/f47609c8-17ae-42bf-9a50-0bc4e70a1c1c" />

**Question 7**
```
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```
```
select count(*) as employees_count
from employee
where income>50000;
```
**Output:**

<img width="426" height="307" alt="Screenshot 2026-09-01 224745" src="https://github.com/user-attachments/assets/84d9b71b-ec9c-42f2-95e1-c31adfbd893c" />


**Question 8**
<img width="1002" height="442" alt="Screenshot 2026-09-01 224804" src="https://github.com/user-attachments/assets/b5021eda-7aa9-4084-8889-d4f4834f3196" />
```
select age,MIN(income) as Income
from employee
group by age
having MIN(income) <1000000;

```

**Output:**

<img width="563" height="433" alt="Screenshot 2026-09-01 224813" src="https://github.com/user-attachments/assets/174cd0fe-2e2d-4643-bd5f-bb3f50a17b20" />

**Question 9**
<img width="967" height="416" alt="Screenshot 2026-09-01 224918" src="https://github.com/user-attachments/assets/f3232d67-d2b1-4c2e-af6a-345744ca2394" />


```
select category_id,AVG(Price)
from products
group by category_id
having AVG(Price) between 10 and 15;
```

**Output:**

<img width="605" height="350" alt="Screenshot 2026-09-01 224939" src="https://github.com/user-attachments/assets/726fce04-6ea8-40e6-aa3d-8eda3ebf8d6f" />


**Question 10**
<img width="982" height="428" alt="Screenshot 2026-09-01 225013" src="https://github.com/user-attachments/assets/55a736b6-cff6-4c0c-a6bd-75c079d5c287" />


```
select age,MIN(income) from employee group by age having MIN(income)<400000;
```

**Output:**

<img width="563" height="387" alt="Screenshot 2026-09-01 225044" src="https://github.com/user-attachments/assets/6132b4a7-8395-411f-aa9f-97c05f0a095f" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
