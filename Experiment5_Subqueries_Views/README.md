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

**Question 1**
---


```


```

**Output:**




**Question 2**
---



```


```

**Output:**



**Question 3**
---



```


```

**Output:**




**Question 4**
---



```


```

**Output:**



**Question 5**
---



```

```

**Output:**



**Question 6**
---



```

```

**Output:**



**Question 7**
---


```


```

**Output:**




**Question 8**
---



```


```

**Output:**




**Question 9**
---



```


```

**Output:**




**Question 10**
---



```


```

**Output:**




### Screenshot of Module 3 SEB Completion Grade:



```
## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
