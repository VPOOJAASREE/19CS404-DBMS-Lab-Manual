# Experiment 5: Subqueries and Views

```
NAME: V. POOJAA SREE
REG.NO.: 212223040147

```

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
---
![1](https://github.com/user-attachments/assets/6f02cc01-182d-4d05-b275-21475562cc27)



```
SELECT * FROM Employee
WHERE age < (
SELECT AVG(age)
FROM Employee
WHERE income > 250000
);

```

**Output:**

![1](https://github.com/user-attachments/assets/3a15c8c5-d160-4164-bf7e-2ff919af541b)




**Question 2**
---

![2](https://github.com/user-attachments/assets/a8c3fed1-1e2f-4668-bf2e-22e7581bb475)


```
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);


```

**Output:**

![2](https://github.com/user-attachments/assets/17bf300d-8cf3-45a3-b39d-9b58d6976972)


**Question 3**
---

![3](https://github.com/user-attachments/assets/a9f50f73-d7e4-485f-95a1-306ac9ce5b6c)


```
SELECT * FROM CUSTOMERS
WHERE SALARY>1500;

```

**Output:**

![3](https://github.com/user-attachments/assets/bad6bc60-b96f-48eb-9949-43b89af2e386)



**Question 4**
---

![4](https://github.com/user-attachments/assets/9b1d968a-fe14-4a6b-b827-9af49bc39893)


```
SELECT * FROM CUSTOMERS
WHERE SALARY<2500;

```

**Output:**

![4](https://github.com/user-attachments/assets/dc2580d6-7672-4942-8a52-03e1e8edccc7)



**Question 5**
---

![5](https://github.com/user-attachments/assets/1968a560-cf92-41b3-b52a-a9ef7070e5d5)


```
SELECT * FROM CUSTOMERS
WHERE ADDRESS = (
SELECT ADDRESS 
FROM CUSTOMERS
WHERE ADDRESS ="Delhi"
);

```

**Output:**

![5](https://github.com/user-attachments/assets/e34f3014-5773-47e4-b9ba-65afb9f2e7e0)


**Question 6**
---

![6](https://github.com/user-attachments/assets/d602fd4c-5025-4663-a34a-e82c507e9a8d)


```
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 1000000
);


```

**Output:**

![6](https://github.com/user-attachments/assets/206e5e0a-9d9b-4275-b00c-1321c145b5bc)



**Question 7**
---

![7](https://github.com/user-attachments/assets/f04f016b-36df-459d-9de0-f4482f1c912e)


```
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'London';


```

**Output:**

![7](https://github.com/user-attachments/assets/56318caf-c012-41bb-ae46-652a6b73b502)




**Question 8**
---

![8](https://github.com/user-attachments/assets/8b4b0371-cd80-4f04-abd2-5fac0d382412)


```
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';


```

**Output:**

![8](https://github.com/user-attachments/assets/bca0f433-17ed-42cb-a8ad-1617c8195e9d)



**Question 9**
---

![9](https://github.com/user-attachments/assets/563272e9-b773-4b53-98ae-695b819ff71e)


```
SELECT *
FROM customer
WHERE customer_id = (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);


```

**Output:**

![9](https://github.com/user-attachments/assets/16591cf4-84ce-4dbf-9c73-10d1c543fe0f)



**Question 10**
---

![10](https://github.com/user-attachments/assets/145871a1-ca26-444f-8b42-46fe25f45e72)


```
SELECT
student_name, grade
FROM GRADES g
WHERE grade = (
SELECT MAX(grade)
FROM GRADES
WHERE subject=g.subject
);

```

**Output:**

![10](https://github.com/user-attachments/assets/4de838bf-9cde-470e-8efe-63009aeccaef)



### Screenshot of Module 4 SEB Completion Grade:

![seb 4](https://github.com/user-attachments/assets/89823322-f598-4d7e-b670-ac0eaeff1476)


```
## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
