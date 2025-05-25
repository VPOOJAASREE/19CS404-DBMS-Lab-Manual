# Experiment 4: Aggregate Functions, Group By and Having Clause

```
NAME: V. POOJAA SREE
REG.NO.: 212223040147

```
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
---
![1](https://github.com/user-attachments/assets/89b5aca7-9b26-42ab-b554-2032ac459ad9)


```
SELECT
Medication,
COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Medication;

```

**Output:**

![1](https://github.com/user-attachments/assets/9eafe79f-3b5e-45ae-a88f-e10b6ed778b1)


**Question 2**
---
![2](https://github.com/user-attachments/assets/8fa718be-f956-4096-b4e6-7c4af3308bde)


```
SELECT
DoctorID,
COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID;

```

**Output:**

![2](https://github.com/user-attachments/assets/f4433226-ed7b-401b-a801-59386f216110)


**Question 3**
---
![3](https://github.com/user-attachments/assets/199531f8-6fc3-42c4-890e-004144e9ad0a)


```
SELECT
strftime('%Y-%m', Date) AS Month,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY Month;

```

**Output:**

![3](https://github.com/user-attachments/assets/2674b5c6-4e30-4d8b-b111-c0f36e44d7f6)


**Question 4**
---
![4](https://github.com/user-attachments/assets/2aec1ec3-dc47-48a4-beea-fd0c7e97e451)


```
SELECT
COUNT(*) AS unique_cities
FROM customer;

```

**Output:**

![4](https://github.com/user-attachments/assets/441f8f28-7815-4f09-854f-449edff7425b)


**Question 5**
---
![5](https://github.com/user-attachments/assets/7efca30c-e532-4b20-b731-95354d8e84fd)


```
SELECT
name AS fruit_name,
MIN(inventory) AS lowest_quantity
FROM fruits;

```

**Output:**

![5](https://github.com/user-attachments/assets/cea55957-abe5-4da9-9274-24082a6d0a9f)


**Question 6**
---
![6](https://github.com/user-attachments/assets/f070b66f-8ccc-4f96-9e29-f9c7df6f9f23)


```
SELECT
COUNT(city) AS COUNT
FROM customer
WHERE city != 'Noida';

```

**Output:**

![6](https://github.com/user-attachments/assets/d3693276-afa3-49e3-bdfb-cbdb0641f64e)


**Question 7**
---
![7](https://github.com/user-attachments/assets/087dc543-6a78-499a-af33-24750c23234d)


```
SELECT
COUNT(DISTINCT customer_id) AS COUNT
FROM customer;

```

**Output:**

![7](https://github.com/user-attachments/assets/6b8ddb7d-7485-4b2c-8e0b-23afab77f4d4)


**Question 8**
---
![8](https://github.com/user-attachments/assets/b1849f48-4db7-46dd-a6be-e39a4c960e28)


```

SELECT
occupation,
AVG(workhour) AS 'AVG(workhour)'
FROM employee1
GROUP BY occupation
HAVING AVG(workhour)>=10
AND AVG(workhour)<=12;

```

**Output:**

![8](https://github.com/user-attachments/assets/6745f32e-d811-4812-b619-4950c58521c8)


**Question 9**
---
![9](https://github.com/user-attachments/assets/9f956be2-fd70-4f0d-8e5b-3f43f170411b)


```
SELECT
(age/5)*5 AS 'age_group',
MAX(salary) AS 'MAX(salary)'
FROM customer1
GROUP BY age_group
HAVING MAX(salary)>8000;

```

**Output:**

![9](https://github.com/user-attachments/assets/7bab986f-0864-41b5-9234-1ae429d0b74a)


**Question 10**
---
![10](https://github.com/user-attachments/assets/bd114d13-0781-4c5b-91f3-18ba1d0b2c58)


```
SELECT
(age/5)*5 AS 'age_group',
MIN(salary) AS 'MIN(salary)'
FROM customer1
GROUP BY age_group
HAVING MIN(salary) < 2000;

```

**Output:**

![10](https://github.com/user-attachments/assets/66c819b5-36e9-4adb-b5f8-f087cc022b0b)


### Screenshot of Module 3 SEB Completion Grade:

![seb 3](https://github.com/user-attachments/assets/93bd54a4-a6ed-46aa-8f6e-84f129de8dc9)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
