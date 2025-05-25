# Experiment 3: DML Commands

```
NAME: V. POOJAA SREE
REG.NO.: 212223040147

```

## AIM:
To study and implement DML (Data Manipulation Language) commands.

## THEORY:

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
---


```
UPDATE products
SET reorder_lvl=reorder_lvl*1.3
WHERE category='Food'
AND quantity<(reorder_lvl*0.5);

```

**Output:**




**Question 2**
---



```
UPDATE Employees
SET salary=salary*2
WHERE department_id = 20
AND job_id LIKE '%MAN%';

```

**Output:**



**Question 3**
---



```
UPDATE suppliers
SET supplier_name='A1 Suppliers'
WHERE supplier_id=8;

```

**Output:**




**Question 4**
---



```
DELETE FROM Customer
WHERE GRADE>=2;

```

**Output:**



**Question 5**
---



```
DELETE FROM Customer
WHERE OPENING_AMT
BETWEEN 4000 AND 6000;

```

**Output:**



**Question 6**
---



```
SELECT
CategoryName,
Description
FROM categories
ORDER BY categoryName;

```

**Output:**



**Question 7**
---


```
SELECT patient_id,
first_name, 
admission_date
FROM Patients
WHERE admission_date >='2023-01-01'
AND admission_date<'2024-01-01';

```

**Output:**




**Question 8**
---



```
SELECT id,
value1,
ABS(value1) AS absolute_value
FROM Calculations;

```

**Output:**




**Question 9**
---



```
SELECT * FROM customer
WHERE grade=100;

```

**Output:**




**Question 10**
---



```
SELECT SUBSTR(EmpLname, 1, 4) FROM EmployeeInfo;

```

**Output:**




### Screenshot of Module 3 SEB Completion Grade:






## RESULT:
Thus, the SQL queries to implement DML commands have been executed successfully.
