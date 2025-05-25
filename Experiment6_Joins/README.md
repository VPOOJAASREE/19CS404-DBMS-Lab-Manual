# Experiment 6: Joins

```
NAME: V. POOJAA SREE
REG. NO.: 212223040147

```

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
---

![1](https://github.com/user-attachments/assets/f1039931-d31a-45b8-b622-83bbc516e564)


```
SELECT
a.patient_id,
p.first_name, 
p.last_name, 
p.date_of_birth,
p.admission_date,
p.discharge_date,
a.doctor_id
FROM 
PATIENTS p
INNER JOIN
APPOINTMENTS a ON p.patient_id=a.patient_id
WHERE 
appointment_date BETWEEN '2024-01-01' and '2024-01-31';

```

**Output:**

![1](https://github.com/user-attachments/assets/bd3ba3d2-8b9b-4164-b830-bb0da4cf2261)



**Question 2**
---

![2](https://github.com/user-attachments/assets/cff1965a-4858-490e-b1c2-79e1aa0f2228)


```
SELECT
c.cust_name, 
s.name
FROM 
Customer c
LEFT JOIN
Salesman s ON c.salesman_id=s.salesman_id
WHERE
c.city=s.city;

```

**Output:**

![2](https://github.com/user-attachments/assets/4442bd02-50e8-4fed-b477-5a9faeec4a50)


**Question 3**
---

![3](https://github.com/user-attachments/assets/1497d954-938d-4c03-a1dc-1fd633cfefd3)


```
SELECT
c.cust_name, 
c.city,
c.grade,
s.name AS "Salesman",
s.city
FROM
customer c
JOIN
salesman s ON c.salesman_id=s.salesman_id
WHERE
c.grade<300
ORDER BY
c.customer_id ASC;

```

**Output:**

![3](https://github.com/user-attachments/assets/c6c84cc2-55a9-406b-973a-9048bed811a8)




**Question 4**
---

![4](https://github.com/user-attachments/assets/1b08eb86-bc36-42da-8270-c27f2e92dc1e)


```
SELECT
p.first_name
FROM 
PATIENTS p
INNER JOIN
SURGERIES s ON p.patient_id=s.patient_id
WHERE
s.surgery_date='2024-01-15';

```

**Output:**

![4](https://github.com/user-attachments/assets/82508f4c-b7c2-4748-a6ae-7c521cef0118)


**Question 5**
---

![5](https://github.com/user-attachments/assets/a98d54db-1ac4-42cb-aa7d-3cf123344304)


```
SELECT
c.cust_name,
s.commission
FROM 
Customer c
LEFT JOIN
Salesman s ON c.salesman_id=s.salesman_id;

```

**Output:**

![5](https://github.com/user-attachments/assets/b66d17ce-8183-4d91-b9ee-1d0ae27686f6)


**Question 6**
---

![6](https://github.com/user-attachments/assets/8aa8eb91-fa6d-4185-89fa-0746dc9f88e0)


```
SELECT
p.first_name as "patient_name",
d.specialization as "Doctor_speciali"
FROM 
PATIENTS p
INNER JOIN
DOCTORS d ON p.doctor_id=d.doctor_id
WHERE
p.admission_date BETWEEN  '2024-01-01' and '2024-01-31';

```

**Output:**

![6](https://github.com/user-attachments/assets/a83172f8-57d3-4503-9f21-61779edc111f)


**Question 7**
---

![7](https://github.com/user-attachments/assets/315a1d28-e602-48c2-be3d-73ac5e3cf4c7)


```
SELECT
o.ord_no,
o.purch_amt,
c.cust_name, 
c.city
FROM
customer c
JOIN
orders o ON c.salesman_id=o.salesman_id
WHERE
o.purch_amt BETWEEN 500 AND 2000
and c.city!='London';

```

**Output:**

![7](https://github.com/user-attachments/assets/661d6e2f-7ae7-44a3-94d7-ca16056c5cc2)



**Question 8**
---

![8](https://github.com/user-attachments/assets/bbe8b6a7-8acc-4a39-9120-e5744e5987fc)


```
SELECT
c.cust_name AS 'Customer Name',
c.city,
s.name AS 'Salesman',
s.city,
s.commission
FROM customer c
JOIN
salesman s ON c.salesman_id=s.salesman_id
WHERE
s.city<>c.city
AND s.commission>0.12;


```

**Output:**

![8](https://github.com/user-attachments/assets/224d9531-79e1-47f4-921c-20d272009a31)



**Question 9**
---

![9](https://github.com/user-attachments/assets/c169dffb-998c-49df-b976-4d96f63e5bd9)


```
SELECT
o.ord_no,
o.purch_amt,
o.ord_date,
c.cust_name,
c.city AS 'customer_city',
c.grade,
s.name AS 'salesman_name',
s.city AS 'salesman_city',
s.commission
FROM 
orders o
JOIN
customer c ON o.customer_id=c.customer_id
JOIN
salesman s ON c.salesman_id=s.salesman_id;

```

**Output:**

![9](https://github.com/user-attachments/assets/4512edc6-69e4-4786-b353-49841fa4f285)



**Question 10**
---

![10](https://github.com/user-attachments/assets/bd58dfd9-4fc6-48cc-b76b-aed95cf06556)


```
SELECT 
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM 
    salesman s
JOIN 
    customer c ON s.city = c.city


```

**Output:**

![10](https://github.com/user-attachments/assets/cabb1947-0ddd-4bbd-b5ad-e3c5dc900e51)



### Screenshot of Module 3 SEB Completion Grade:



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
