# Experiment 7: PL/SQL – Variables, Control Structures and Loops

```
NAME: V. POOJAA SREE
REG.NO.: 212223040147

```

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers.


### Program:

```
DECLARE
    num1 NUMBER := 80;
    num2 NUMBER := 60;
BEGIN
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
    ELSIF num2 > num1 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Both numbers are equal: ' || num1);
    END IF;
END;

```

### Output:

![1](https://github.com/user-attachments/assets/28283e07-79c4-477b-ac09-216ff696b3b4)


---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers.


### Program:

```
DECLARE
    n NUMBER := 10;
    i NUMBER := 1;
    sum NUMBER := 0;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;

```

### OUTPUT:

![2](https://github.com/user-attachments/assets/c73bae07-20f1-4f5c-9244-f4c166c47374)


---

## 3. Write a PL/SQL program to generate Fibonacci series.


### Program:

```

DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 3;
BEGIN
    DBMS_OUTPUT.PUT('Fibonacci sequence: ' || a || ', ' || b);
    WHILE i <= n LOOP
        c := a + b;
        DBMS_OUTPUT.PUT(', ' || c);
        a := b;
        b := c;
        i := i + 1;
    END LOOP;
    DBMS_OUTPUT.NEW_LINE;
END;

```

### Output:

![3](https://github.com/user-attachments/assets/2f6e0ded-b125-43a6-97bb-5fe2d2c945ec)


---


## 4. Write a PL/SQL Program to display the number in Reverse Order.


### Program:

```

DECLARE
    n NUMBER := 1535;
    reverse NUMBER := 0;
    digit NUMBER;
    temp NUMBER;
BEGIN
    temp := n;
    WHILE temp > 0 LOOP
        digit := MOD(temp, 10);
        reverse := (reverse * 10) + digit;
        temp := TRUNC(temp / 10);
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Reversed number is: ' || reverse);
END;

```

### OUTPUT:

![4](https://github.com/user-attachments/assets/ce9405ea-fbfc-4b4f-a327-89fccc932461)


---

## 5. Write a PL/SQL program to find the largest of three numbers.


### Program:

```

DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
BEGIN
    IF a >= b AND a >= c THEN
        DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || a);
    ELSIF b >= a AND b >= c THEN
        DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || b);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || c);
    END IF;
END;

```

### OUTPUT:

![5](https://github.com/user-attachments/assets/f746b179-33bc-4261-8768-0065afce324b)


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
