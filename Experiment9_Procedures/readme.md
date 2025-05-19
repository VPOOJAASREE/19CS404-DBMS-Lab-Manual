# Experiment 9: PL/SQL – Procedures and Functions

```
NAME: V. POOJAA SREE
REG. NO.: 212223040147

```

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

### Program:

```
SET SERVEROUTPUT ON;
DECLARE
    num NUMBER := &Enter_a_number_for_square;
    square NUMBER;
BEGIN
    square := num * num;
    DBMS_OUTPUT.PUT_LINE('Square of ' || num || ' is ' || square);
END;
/

```

### Output:

![1](https://github.com/user-attachments/assets/238e88a2-53b6-4e69-8156-837c4eb5e83a)

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Program:

```
SET SERVEROUTPUT ON;
DECLARE
    num NUMBER := &Enter_a_number_for_factorial;
    fact NUMBER := 1;
BEGIN
    FOR i IN 1..num LOOP
        fact := fact * i;
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Factorial of ' || num || ' is ' || fact);
END;
/

```

### Output:

![2](https://github.com/user-attachments/assets/e31b8163-c0ba-40f6-9c18-1d20c5fa666b)

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Program:

```
SET SERVEROUTPUT ON;
DECLARE
    num NUMBER := &Enter_a_number_to_check_even_odd;
BEGIN
    IF MOD(num, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(num || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(num || ' is Odd');
    END IF;
END;
/

```

### Output:

![3a](https://github.com/user-attachments/assets/806d0b4d-6001-4804-8749-a9bb7c718ca6)

![3b](https://github.com/user-attachments/assets/6c639b22-bf77-4251-9900-0bb5279e820d)

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Program:

```
SET SERVEROUTPUT ON;
DECLARE
    num NUMBER := &Enter_a_number_to_reverse;
    rev NUMBER := 0;
    temp NUMBER;
BEGIN
    temp := num;
    WHILE temp > 0 LOOP
        rev := rev * 10 + MOD(temp, 10);
        temp := TRUNC(temp / 10);
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Reversed number of ' || num || ' is ' || rev);
END;
/

```

### Output:

![4](https://github.com/user-attachments/assets/8a78001a-dafa-4f64-ad61-fe2e683aabbd)


---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Program:

```
SET SERVEROUTPUT ON;
DECLARE
    num NUMBER := &Enter_a_number_for_table;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || num || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(num || ' x ' || i || ' = ' || (num * i));
    END LOOP;
END;
/

```

### Output:

![5](https://github.com/user-attachments/assets/e5b32f8b-0beb-4115-b8d3-a203cd6f64f9)

---


## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
