# Experiment 8: PL/SQL Cursor Programs

```
NAME: V. POOJAA SREE
REG. NO.: 212223040147

```
## AIM
To write and execute PL/SQL programs using cursors and exception handling to manage runtime errors effectively and display appropriate messages.

## THEORY

In PL/SQL, cursors are used to handle query result sets row-by-row. 

There are two types of cursors:

- Implicit Cursors: Automatically created by PL/SQL for single-row queries.
- Explicit Cursors: Declared and controlled by the programmer for multi-row queries.

Types of Explicit Cursors:

1. Simple Cursor: Basic cursor to iterate over multiple rows.

2. Parameterized Cursor: Accepts parameters to filter the result dynamically.

3. Cursor FOR Loop: Simplifies cursor operations (open, fetch, close).

4. %ROWTYPE Cursor: Fetches entire row into a record using %ROWTYPE.

5. Cursor with FOR UPDATE: Used for row-level locking and updating the rows while looping.

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

**Exception Handling**

PL/SQL provides a robust mechanism to handle runtime errors using exception handling blocks. When an error occurs during execution, control is passed to the EXCEPTION section, where specific or general errors can be handled gracefully.

### Components of Exception Handling:
- Predefined Exceptions: Automatically raised by PL/SQL for common errors (e.g., NO_DATA_FOUND, TOO_MANY_ROWS, ZERO_DIVIDE).
- User-defined Exceptions: Declared explicitly in the declaration section using the EXCEPTION keyword.
- WHEN OTHERS: A generic handler for all exceptions not handled explicitly.

```sql
BEGIN
   -- Statements
EXCEPTION
   WHEN exception_name THEN
      -- Handling code
   WHEN OTHERS THEN
      -- Handling for unknown errors
END;
```

### **Question 1: Simple Cursor with Exception Handling**

**Write a PL/SQL program using a simple cursor to fetch employee names and designations from the `employees` table. Implement exception handling for the following cases:**

### Program:

```
-- Step 1: Create Table
CREATE TABLE employees (
  emp_id      NUMBER(5),
  emp_name    VARCHAR2(50),
  designation VARCHAR2(50)
);

-- Step 2: Insert sample data
INSERT INTO employees VALUES (101, 'Alice', 'Manager');
INSERT INTO employees VALUES (102, 'Bob', 'Developer');
INSERT INTO employees VALUES (103, 'Charlie', 'Analyst');

-- Step 3: PL/SQL block with a simple cursor and exception handling
DECLARE
  CURSOR emp_cursor IS
    SELECT emp_name, designation FROM employees;

  v_emp_name    employees.emp_name%TYPE;
  v_designation employees.designation%TYPE;
  
  v_found BOOLEAN := FALSE; -- To check if any row is fetched

BEGIN
  OPEN emp_cursor;

  LOOP
    FETCH emp_cursor INTO v_emp_name, v_designation;
    EXIT WHEN emp_cursor%NOTFOUND;

    DBMS_OUTPUT.PUT_LINE('Name: ' || v_emp_name || ', Designation: ' || v_designation);
    v_found := TRUE;
  END LOOP;

  CLOSE emp_cursor;

  IF NOT v_found THEN
    RAISE NO_DATA_FOUND;
  END IF;

EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('No employee data found.');

  WHEN OTHERS THEN
    DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/

```

### Output:

![1](https://github.com/user-attachments/assets/edc2986f-c08e-48f2-af6a-93e43dc4092d)


---

### **Question 2: Parameterized Cursor with Exception Handling**

**Write a PL/SQL program using a parameterized cursor to retrieve and display employees with a salary in a given range. Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees meet the salary criteria.
2. **OTHERS**: For any unexpected errors during the execution.

### Program:

```
-- Step 1: Modify the employees table to add a salary column
ALTER TABLE employees ADD (salary NUMBER(10,2));

-- Step 2: Update salary values for existing employees
UPDATE employees SET salary = 60000 WHERE emp_id = 101;
UPDATE employees SET salary = 45000 WHERE emp_id = 102;
UPDATE employees SET salary = 70000 WHERE emp_id = 103;

-- Step 3: PL/SQL block with parameterized cursor and exception handling
DECLARE
  -- Parameterized cursor
  CURSOR emp_cursor(min_salary NUMBER, max_salary NUMBER) IS
    SELECT emp_name, designation, salary
    FROM employees
    WHERE salary BETWEEN min_salary AND max_salary;

  -- Variables to hold fetched values
  v_emp_name    employees.emp_name%TYPE;
  v_designation employees.designation%TYPE;
  v_salary      employees.salary%TYPE;

  -- Input range
  v_min_salary NUMBER := 40000;
  v_max_salary NUMBER := 65000;

  v_found BOOLEAN := FALSE;

BEGIN
  -- Open and fetch from cursor
  FOR emp_rec IN emp_cursor(v_min_salary, v_max_salary) LOOP
    DBMS_OUTPUT.PUT_LINE('Name: ' || emp_rec.emp_name || 
                         ', Designation: ' || emp_rec.designation || 
                         ', Salary: ' || emp_rec.salary);
    v_found := TRUE;
  END LOOP;

  -- If no data was found
  IF NOT v_found THEN
    RAISE NO_DATA_FOUND;
  END IF;

EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('No employees found in the given salary range.');

  WHEN OTHERS THEN
    DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/

```

### Output:

![2](https://github.com/user-attachments/assets/d7667bf1-48d7-4125-b894-bbb85a3043fb)


---

### **Question 3: Cursor FOR Loop with Exception Handling**

**Write a PL/SQL program using a cursor FOR loop to retrieve and display all employee names and their department numbers from the `employees` table. Implement exception handling for the following cases:**

### Program:

```
ALTER TABLE employees ADD (dept_no NUMBER);
UPDATE employees SET dept_no = 10 WHERE emp_id = 101;
UPDATE employees SET dept_no = 20 WHERE emp_id = 102;
UPDATE employees SET dept_no = 30 WHERE emp_id = 103;

SET SERVEROUTPUT ON;

DECLARE
  -- Cursor to fetch employee names and department numbers
  CURSOR emp_cursor IS
    SELECT emp_name, dept_no FROM employees;

  v_found BOOLEAN := FALSE;

BEGIN
  -- Using a FOR loop to iterate over the cursor
  FOR emp_rec IN emp_cursor LOOP
    DBMS_OUTPUT.PUT_LINE('Name: ' || emp_rec.emp_name || 
                         ', Department Number: ' || emp_rec.dept_no);
    v_found := TRUE;
  END LOOP;

  -- If no data was found
  IF NOT v_found THEN
    RAISE NO_DATA_FOUND;
  END IF;

EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('No employees found in the database.');

  WHEN OTHERS THEN
    DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/



```

### Output:

![3](https://github.com/user-attachments/assets/97bda04a-4ef9-4678-85f8-d8e1689a0424)


---

### **Question 4: Cursor with `%ROWTYPE` and Exception Handling**

**Write a PL/SQL program that uses a cursor with `%ROWTYPE` to fetch and display complete employee records (emp_id, emp_name, designation, salary). Implement exception handling for the following errors:**

### Program:

```
-- Add emp_id column (Primary Key)
ALTER TABLE employees ADD (emp_id NUMBER);

-- Add emp_name column
ALTER TABLE employees ADD (emp_name VARCHAR2(50));

-- Add designation column
ALTER TABLE employees ADD (designation VARCHAR2(50));

-- Add salary column
ALTER TABLE employees ADD (salary NUMBER(10,2));

-- Add Primary Key constraint on emp_id
ALTER TABLE employees
ADD CONSTRAINT employees_pk PRIMARY KEY (emp_id);

SET SERVEROUTPUT ON;

DECLARE
  CURSOR emp_cursor IS
    SELECT emp_id, emp_name, designation, salary 
    FROM employees
    ORDER BY emp_id;  -- 👈 Ensures the output is sorted by emp_id

  emp_record emp_cursor%ROWTYPE;
  v_found BOOLEAN := FALSE;

BEGIN
  OPEN emp_cursor;
  
  LOOP
    FETCH emp_cursor INTO emp_record;
    EXIT WHEN emp_cursor%NOTFOUND;
    
    DBMS_OUTPUT.PUT_LINE('Emp ID: ' || emp_record.emp_id || 
                         ', Name: ' || emp_record.emp_name ||
                         ', Designation: ' || emp_record.designation || 
                         ', Salary: ' || emp_record.salary);
    v_found := TRUE;
  END LOOP;

  CLOSE emp_cursor;

  IF NOT v_found THEN
    RAISE NO_DATA_FOUND;
  END IF;

EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('No employees found in the database.');
  WHEN OTHERS THEN
    DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/


```

### Output:

![4](https://github.com/user-attachments/assets/37dd7d22-89d6-436a-9af6-7e9f27927546)

---

### **Question 5: Cursor with FOR UPDATE Clause and Exception Handling**

**Write a PL/SQL program using a cursor with the `FOR UPDATE` clause to update the salary of employees in a specific department. Implement exception handling for the following cases:**

### Program:

```
SET SERVEROUTPUT ON;

DECLARE
  CURSOR emp_cursor IS
    SELECT emp_id, salary
    FROM employees
    WHERE dept_no = 10
    FOR UPDATE;  -- Locks the rows in dept 10

  v_emp_id employees.emp_id%TYPE;
  v_salary employees.salary%TYPE;
  v_found BOOLEAN := FALSE;

BEGIN
  OPEN emp_cursor;

  LOOP
    FETCH emp_cursor INTO v_emp_id, v_salary;
    EXIT WHEN emp_cursor%NOTFOUND;

    -- Give a 10% raise
    UPDATE employees
    SET salary = v_salary * 1.10
    WHERE emp_id = v_emp_id;

    DBMS_OUTPUT.PUT_LINE('Updated salary for emp_id ' || v_emp_id);
    v_found := TRUE;
  END LOOP;

  CLOSE emp_cursor;

  IF NOT v_found THEN
    RAISE NO_DATA_FOUND;
  END IF;

  COMMIT;

EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('No employees found in the specified department.');
  WHEN OTHERS THEN
    DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
    ROLLBACK;
END;
/

```

### Output:

![5](https://github.com/user-attachments/assets/f6888b2c-0a79-4be3-bfd9-ddba62c17e02)


---

## RESULT
Thus, the programs are successfully executed and displayed employee details using a cursor. 

