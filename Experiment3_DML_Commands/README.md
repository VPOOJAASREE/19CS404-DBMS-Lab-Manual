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
![1](https://github.com/user-attachments/assets/e1a463ba-3ab6-4c89-81ad-c642ccbd8309)


```
UPDATE products
SET reorder_lvl=reorder_lvl*1.3
WHERE category='Food'
AND quantity<(reorder_lvl*0.5);

```

**Output:**

![1](https://github.com/user-attachments/assets/203ffdc4-d006-440d-9573-70e78ff3b39e)



**Question 2**
---

![2](https://github.com/user-attachments/assets/e1e5366b-e047-43c8-b624-378208c8215f)


```
UPDATE Employees
SET salary=salary*2
WHERE department_id = 20
AND job_id LIKE '%MAN%';

```

**Output:**

![2](https://github.com/user-attachments/assets/b3e95d54-67c0-41bf-906b-eb7344d75d1d)


**Question 3**
---

![3](https://github.com/user-attachments/assets/c1d4c005-edbe-4fbc-b239-dd5de5e7f2ca)


```
UPDATE suppliers
SET supplier_name='A1 Suppliers'
WHERE supplier_id=8;

```

**Output:**

![3](https://github.com/user-attachments/assets/404d77c2-c508-40df-8551-6cf4c83431d8)



**Question 4**
---

![4](https://github.com/user-attachments/assets/dcf56389-10e5-409d-871f-029d25559daf)


```
DELETE FROM Customer
WHERE GRADE>=2;

```

**Output:**

![4](https://github.com/user-attachments/assets/9563eaf4-041b-4974-87b0-f7ca0db96b42)



**Question 5**
---

![5](https://github.com/user-attachments/assets/a7bb3e44-c92c-4477-a5e8-9916a746cd8c)


```
DELETE FROM Customer
WHERE OPENING_AMT
BETWEEN 4000 AND 6000;

```

**Output:**

![5](https://github.com/user-attachments/assets/e0cd27ff-de1c-4a9d-a967-a8e6a72dd88e)



**Question 6**
---

![6](https://github.com/user-attachments/assets/a80d8759-9425-4a58-aa6d-a55ccf34581c)


```
SELECT
CategoryName,
Description
FROM categories
ORDER BY categoryName;

```

**Output:**

![6](https://github.com/user-attachments/assets/226b63a5-778f-4056-a9dc-4b920c17a2dc)



**Question 7**
---

![7](https://github.com/user-attachments/assets/e1f7353e-03fc-45fd-94e0-08b1d23a65be)


```
SELECT patient_id,
first_name, 
admission_date
FROM Patients
WHERE admission_date >='2023-01-01'
AND admission_date<'2024-01-01';

```

**Output:**

![7](https://github.com/user-attachments/assets/68482881-a13d-49da-bbbf-45184c81e872)



**Question 8**
---

![8](https://github.com/user-attachments/assets/57ca4371-98f6-4777-bd9f-b5f8b3075a0c)


```
SELECT id,
value1,
ABS(value1) AS absolute_value
FROM Calculations;

```

**Output:**

![8](https://github.com/user-attachments/assets/e86dbd5d-ba7e-4e7c-ad9a-6aeec7f4e336)



**Question 9**
---

![9](https://github.com/user-attachments/assets/a16acf75-a9ac-4603-b097-ec65fd03b17e)


```
SELECT * FROM customer
WHERE grade=100;

```

**Output:**

![9](https://github.com/user-attachments/assets/8c441c8f-733a-47be-87a3-5504b52ddd1d)



**Question 10**
---

![10](https://github.com/user-attachments/assets/d3568a69-db81-4b8f-8496-5df767dd8c8f)


```
SELECT SUBSTR(EmpLname, 1, 4) FROM EmployeeInfo;

```

**Output:**

![10](https://github.com/user-attachments/assets/5938ec27-0e0b-48d4-ae94-0e47828d9e83)



### Screenshot of Module 2 SEB Completion Grade:

![seb 2](https://github.com/user-attachments/assets/f70154e9-e5a3-41dc-8107-bd3e4f713f03)



## RESULT:
Thus, the SQL queries to implement DML commands have been executed successfully.
