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

**Question 1**
--
<img width="1272" height="476" alt="image" src="https://github.com/user-attachments/assets/7471e97d-294f-4544-a2aa-014e71081784" />


```
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT ,
    FOREIGN KEY (icom_id)
        REFERENCES company(com_id)
        ON UPDATE CASCADE
        ON DELETE CASCADE
);

```

**Output:**

<img width="994" height="333" alt="image" src="https://github.com/user-attachments/assets/0aeec616-96a4-4be9-9232-ac2cb3d27920" />


**Question 2**
---
<img width="1232" height="432" alt="image" src="https://github.com/user-attachments/assets/bd26ba36-7d0f-42f3-a50d-01ebf3c0f87b" />


```
CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT NOT NULL UNIQUE,
    Price REAL CHECK (Price > 0),
    StockQuantity INTEGER CHECK (StockQuantity >= 0)
);
```

**Output:**

<img width="1248" height="357" alt="image" src="https://github.com/user-attachments/assets/135ee2a3-5902-432e-a694-67981760c38c" />


**Question 3**
---
<img width="1074" height="338" alt="image" src="https://github.com/user-attachments/assets/1f0f6443-ba41-4c32-89a7-a9d22824ecfe" />


```
ALTER TABLE employee ADD COLUMN designation varchar(50);
```

**Output:**

<img width="1257" height="371" alt="image" src="https://github.com/user-attachments/assets/2eae33b0-04ed-4701-823f-f39398ddb47f" />


**Question 4**
---
<img width="999" height="414" alt="image" src="https://github.com/user-attachments/assets/64b3cddd-bb65-443d-90c9-5720cea6cd24" />


```
<img width="999" height="414" alt="image" src="https://github.com/user-attachments/assets/afec1327-b64c-4887-bbe5-dbc9ed7062d6" />

```

**Output:**

<img width="1253" height="465" alt="image" src="https://github.com/user-attachments/assets/2a7e60f4-d9a1-4933-a169-ffd79a737f0c" />


**Question 5**
---
<img width="1191" height="268" alt="image" src="https://github.com/user-attachments/assets/19925096-e79b-429f-9bef-fce20316c556" />


```
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary) VALUES (001, 'Sarah Parker', 'Manager', 'HR', 60000);
```

**Output:**

<img width="1248" height="275" alt="image" src="https://github.com/user-attachments/assets/ec771cc6-56f1-4429-8e9d-6a88ebb99a03" />


**Question 6**
---

<img width="1231" height="394" alt="image" src="https://github.com/user-attachments/assets/9a2d9333-9842-4bba-8fb6-86ec51c745d5" />


```
<img width="1231" height="394" alt="image" src="https://github.com/user-attachments/assets/215d1eeb-d3b9-452f-a30e-2ffb0f17f884" />


```

**Output:**

<img width="776" height="286" alt="image" src="https://github.com/user-attachments/assets/7fe3acb0-b0c9-47c6-9a5b-d6fb8d859f7a" />


**Question 7**
---
<img width="1232" height="386" alt="image" src="https://github.com/user-attachments/assets/b7003999-f2c1-467c-9dd8-b2b8c658ceae" />


```
CREATE TABLE Department (
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT NOT NULL UNIQUE,
    Location TEXT
);
```

**Output:**

<img width="1179" height="242" alt="image" src="https://github.com/user-attachments/assets/3924c281-6aa4-4de4-a9ed-fed4051d6374" />

**Question 8**
---
<img width="1218" height="621" alt="image" src="https://github.com/user-attachments/assets/f121caeb-77b0-4b6f-be78-9ad61a735366" />


```
ALTER TABLE customer
ADD COLUMN discount DECIMAL(5,2);
```

**Output:**

<img width="1246" height="454" alt="image" src="https://github.com/user-attachments/assets/9f10fb1c-90dd-403c-a820-66ada758d991" />


**Question 9**
---
<img width="2457" height="486" alt="image" src="https://github.com/user-attachments/assets/725a01a9-8919-4a9d-ba2e-e3a33a933e3c" />


```
CREATE TABLE orders (ord_id TEXT LENGTH check(length(ord_id)=4) NOT NULL,item_id TEXT NOT NULL ,ord_date DATE ,ord_qty INTEGER,cost INTEGER, PRIMARY KEY(item_id , ord_date));

```

**Output:**

<img width="2394" height="621" alt="image" src="https://github.com/user-attachments/assets/3e52be56-6379-43ec-a16b-f90fa2260c05" />

**Question 10**
---
<img width="2448" height="381" alt="image" src="https://github.com/user-attachments/assets/43a6c073-b131-4122-9d35-3b849fb22ed2" />


```
CREATE table Invoices(InvoiceID INT,InvoiceDate DATE,Amount REAL check(Amount>0),DueDate DATE check(DueDate>InvoiceDate),OrderID INT, foreign key (OrderID) REFERENCES Orders(OrderID));

```

**Output:**
<img width="2406" height="534" alt="image" src="https://github.com/user-attachments/assets/8aa5f5f3-a989-4d44-8d10-6516435080ba" />


### MARKS
<img width="1516" height="385" alt="image" src="https://github.com/user-attachments/assets/a8d80845-f516-4cea-b93d-8b3bf0cb09e8" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
