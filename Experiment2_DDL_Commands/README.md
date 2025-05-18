# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

### QUESTION 1:

![1](https://github.com/user-attachments/assets/156372eb-fe29-4d26-8026-5f9017ce30e3)


### PROGRAM:

```
CREATE TABLE Orders (
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID)
);

```

### OUTPUT:

![1](https://github.com/user-attachments/assets/41e51d3c-5ded-44a0-89ea-70cb21eb6c36)


### QUESTION 2:

![2](https://github.com/user-attachments/assets/435c0b6d-aadf-449f-a3db-d7da018ecdcf)


### PROGRAM:

```
CREATE TABLE Products (
ProductID INTEGER PRIMARY KEY,
ProductName TEXT NOT NULL,
Price REAL CHECK(Price>0),
Stock INTEGER CHECK(Stock>=0)
);

```

### OUTPUT:

![2](https://github.com/user-attachments/assets/96277173-0dd1-4522-8565-929708ceb8b1)


### QUESTION 3:

![3](https://github.com/user-attachments/assets/e69816ae-01a4-4778-b7a7-162fa7a46c64)


### PROGRAM:

```
CREATE TABLE ProjectAssignments (
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID)
FOREIGN KEY(ProjectID) REFERENCES Projects(ProjectID)
);

```

### OUTPUT:

![3](https://github.com/user-attachments/assets/d093b431-739f-43e7-b722-f6f5d1d92705)


### QUESTION 4:

![4](https://github.com/user-attachments/assets/61e4e279-dfd7-43c3-a02d-35c6af8ca67f)


### PROGRAM:

```
CREATE TABLE Products (
ProductID INTEGER PRIMARY KEY,
ProductName TEXT UNIQUE NOT NULL,
Price REAL CHECK(Price>0),
StockQuantity INTEGER CHECK(StockQuantity>=0)
);

```

### OUTPUT:

![4](https://github.com/user-attachments/assets/661f6c0f-1213-4447-8daa-78fe5fdf5955)


### QUESTION 5:

![5](https://github.com/user-attachments/assets/722cb13b-b985-4dc4-9dea-66cccc54110d)


### PROGRAM:

```
ALTER TABLE Companies
RENAME COLUMN name TO first_name;
ALTER TABLE Companies
ADD COLUMN mobilenumber number;
ALTER TABLE Companies
ADD COLUMN DOB Date;
ALTER TABLE Companies
ADD COLUMN State varchar(30);

```

### OUTPUT:

![5](https://github.com/user-attachments/assets/50ac8969-e8eb-4740-ae8a-5ec37a699cd0)


### QUESTION 6:

![6](https://github.com/user-attachments/assets/b6aab97e-62d7-426a-a00f-69f34244dca6)


### PROGRAM:

```
INSERT INTO  Customers
(CustomerID, Name, Address) VALUES (306,'Diana Prince','Themyscira');

INSERT INTO  Customers
(CustomerID, Name, Address, City, ZipCode) VALUES (307,'Bruce Wayne','Wayne Mano','Gotham',10007);

INSERT INTO  Customers
(CustomerID, Name, Address, ZipCode) VALUES (308,'Peter Parker','Queens',11375);

```

### OUTPUT:

![6](https://github.com/user-attachments/assets/d87f049b-f732-47f3-a3f3-f0f8a24480ac)


### QUESTION 7:

![7](https://github.com/user-attachments/assets/e50ff71a-9e05-4a50-b5df-4870a9da2fb8)


### PROGRAM:

```
INSERT INTO Student_details(Rollno,Name,Gender,Subject,MARKS)
VALUES('201','David Lee','M','Physics','92');

```

### OUTPUT:

![7](https://github.com/user-attachments/assets/c828568d-46d4-4706-af4b-c7f27d7e0ac3)


### QUESTION 8:

![8](https://github.com/user-attachments/assets/8d9f8149-64b4-4bbc-b0a5-236ce625c915)


### PROGRAM:

```
ALTER TABLE Companies
ADD COLUMN designation varchar(50);

ALTER TABLE Companies
ADD COLUMN net_salary number;

```

### OUTPUT:

![8](https://github.com/user-attachments/assets/dd098afc-72d1-45e7-bb53-21c89626b88a)


### QUESTION 9:

![9](https://github.com/user-attachments/assets/23f31396-f6e0-47ad-a223-f986ce24f033)


### PROGRAM:

```
CREATE TABLE Events (
EventID INTEGER,
EventName TEXT,
EventDate DATE
);

```

### OUTPUT:

![9](https://github.com/user-attachments/assets/279facbd-2684-4bb4-bc3e-8d5c9f5e7109)


### QUESTION 10:

![10](https://github.com/user-attachments/assets/8e881927-9a89-42b6-aead-dfc4d4a62f13)


### PROGRAM:

```
SELECT * FROM  Former_employees
UNION ALL
SELECT * FROM  Employee

```

### OUTPUT:

![10](https://github.com/user-attachments/assets/9ab05989-c5a3-4a49-bb66-b2795cd79416)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
