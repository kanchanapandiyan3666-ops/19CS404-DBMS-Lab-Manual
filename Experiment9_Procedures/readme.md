<img width="412" height="166" alt="image" src="https://github.com/user-attachments/assets/e8a6c610-94be-4a19-adc3-2b40b8bae249" /># Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

**Expected Output:**  
Square of 6 is 36

## PROGRAM:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE find_square(num IN NUMBER)
IS
    result NUMBER;
BEGIN
    result := POWER(num, 2);

    DBMS_OUTPUT.PUT_LINE('The square of ' || num || ' = ' || result);
END;
/
```
## OUTPUT:

<img width="315" height="105" alt="Screenshot 2026-08-25 211746" src="https://github.com/user-attachments/assets/ef740d13-aab5-4ec3-b533-2c86b75b811e" />

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

**Expected Output:**  
Factorial of 5 is 120

## PROGRAM:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE FUNCTION get_factorial(n NUMBER)
RETURN NUMBER
IS
    fact NUMBER := 1;
BEGIN
    FOR i IN 1..n LOOP
        fact := fact * i;
    END LOOP;

    RETURN fact;
END;
/

BEGIN
    DBMS_OUTPUT.PUT_LINE('Factorial of 5 is ' || get_factorial(5));
END;
/
```
## OUTPUT

<img width="423" height="153" alt="Screenshot 2026-08-25 212055" src="https://github.com/user-attachments/assets/9464b57a-98b7-4528-99ac-77c9b4627078" />

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
12 is Even

## PROGRAM
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE check_even_odd(n NUMBER)
IS
BEGIN
    IF MOD(n, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(n || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(n || ' is Odd');
    END IF;
END;
/

BEGIN
    check_even_odd(12);
END;
/
```
## OUTPUT


<img width="436" height="158" alt="Screenshot 2026-08-25 212232" src="https://github.com/user-attachments/assets/2e51a5cf-1246-4f87-bca9-8e7cb299a68c" />

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

**Expected Output:**  
Reversed number of 1234 is 4321

## PROGRAM
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE FUNCTION reverse_number(n NUMBER)
RETURN NUMBER
IS
    num NUMBER := n;
    rev NUMBER := 0;
BEGIN
    WHILE num > 0 LOOP
        rev := rev * 10 + MOD(num, 10);
        num := TRUNC(num / 10);
    END LOOP;

    RETURN rev;
END;
/

BEGIN
    DBMS_OUTPUT.PUT_LINE('Reversed number of 1234 is ' || reverse_number(1234));
END;
/
```
## OUTPUT


<img width="412" height="166" alt="Screenshot 2026-08-25 212411" src="https://github.com/user-attachments/assets/087ea51f-ccb9-4520-94e1-22b5540ccfa4" />

---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

## PROGRAM
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE print_table(n NUMBER)
IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || n || ':');

    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(n || ' x ' || i || ' = ' || (n * i));
    END LOOP;
END;
/

BEGIN
    print_table(5);
END;
/
```
## OUTPUT

<img width="465" height="350" alt="Screenshot 2026-08-25 212613" src="https://github.com/user-attachments/assets/e1aeea50-f5db-47a4-9187-46e7ca6c3f34" />


## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
