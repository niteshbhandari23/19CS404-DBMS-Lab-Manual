# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

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
--
<img width="1190" height="679" alt="image" src="https://github.com/user-attachments/assets/488fa45a-d1fa-4472-a80d-22f465623dc7" />


```
update Employees set hire_date='2024-01-24' where department_id=50;
```

**Output:**

<img width="776" height="309" alt="image" src="https://github.com/user-attachments/assets/9ef633c1-4339-42eb-9f6f-548cb78991fb" />


**Question 2**
---
<img width="1236" height="632" alt="image" src="https://github.com/user-attachments/assets/ac57c275-bc8e-4419-b5f2-ec7293007950" />


```
update Employees set salary=salary*2 where job_id like '%MAN';
```

**Output:**

<img width="1197" height="406" alt="image" src="https://github.com/user-attachments/assets/0c162d27-6618-42da-928e-3bb008b881e6" />

**Question 3**
---

<img width="1248" height="519" alt="image" src="https://github.com/user-attachments/assets/39c98b21-4b2d-4165-ae43-e5728747d72f" />


```
delete from Customer where GRADE%2=1;
```

**Output:**

<img width="1295" height="527" alt="image" src="https://github.com/user-attachments/assets/3663e129-db4d-417a-8bf8-ce9a63868b40" />


**Question 4**
---
<img width="1285" height="612" alt="image" src="https://github.com/user-attachments/assets/9ba060e6-b3be-411f-b99e-567ee4e645e2" />


```
delete from Customer where CUST_NAME like  'Holmes%' or CUST_NAME like '%Holmes' or CUST_NAME LIKE '%holmes%';
```

**Output:**

<img width="1304" height="656" alt="image" src="https://github.com/user-attachments/assets/621e495e-60c1-4271-a52a-80bd6d7a7114" />


**Question 5**
---
<img width="873" height="571" alt="image" src="https://github.com/user-attachments/assets/8f0dd13e-6d98-4aac-b0a2-7bcd995d6184" />


```
delete from Doctors where last_name IS NULL;
```

**Output:**

<img width="1074" height="725" alt="image" src="https://github.com/user-attachments/assets/d89384d7-8d59-45f5-869f-53f61e7f6879" />


**Question 6**
---
<img width="1280" height="376" alt="image" src="https://github.com/user-attachments/assets/6e4f16bb-420f-448d-8cb7-f356f4564e25" />


```
delete from customer where AGENT_CODE ='A003' OR AGENT_CODE='A008';
```

**Output:**

<img width="959" height="760" alt="image" src="https://github.com/user-attachments/assets/172ebea6-2199-4af6-b312-2bc978634afc" />

**Question 7**
---
<img width="1205" height="631" alt="image" src="https://github.com/user-attachments/assets/ce779a55-2306-4dd6-bd6a-e7426ddd3675" />


```
select * from salesman where name like 'N__l%';
```

**Output:**

<img width="1160" height="418" alt="image" src="https://github.com/user-attachments/assets/32410683-519c-45a4-b874-20d3c9727070" />


**Question 8**
---
<img width="1136" height="560" alt="image" src="https://github.com/user-attachments/assets/11fc86bc-b433-4080-a007-e81899acf339" />


```
select * from emp where ename like '__R_%';
```

**Output:**

<img width="1277" height="465" alt="image" src="https://github.com/user-attachments/assets/b117226f-f027-416d-b3f1-d2400f6254a6" />


**Question 9**
---
<img width="1001" height="701" alt="image" src="https://github.com/user-attachments/assets/dd1d5ffb-3b0e-45d9-b34d-430dcd3a5c9b" />

```
INSERT INTO Customers (ID, NAME, AGE, ADDRESS, SALARY)
VALUES
(1, 'Ramesh', 32, 'Ahmedabad', 2000),
(2, 'Khilan', 25, 'Delhi', 1500),
(3, 'Kaushik', 23, 'Kota', 2000);
```

**Output:**

<img width="1255" height="395" alt="image" src="https://github.com/user-attachments/assets/1995e776-141a-44ea-b6d1-0d1a808bbde1" />


**Question 10**
---
<img width="863" height="379" alt="image" src="https://github.com/user-attachments/assets/590798ec-3662-44cb-83e9-d00748dab262" />


```
INSERT INTO Employee (EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary
FROM Former_employees;
```

**Output:**

<img width="980" height="282" alt="image" src="https://github.com/user-attachments/assets/527e1263-5dc3-4ffc-8074-ef0953423ca7" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
