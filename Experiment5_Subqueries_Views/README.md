# Experiment 5: Subqueries and Views

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
--
<img width="1291" height="563" alt="image" src="https://github.com/user-attachments/assets/3c11cbca-5904-4e0a-977e-8987ed326b6a" />


```sql
SELECT ord_no, purch_amt, ord_date, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM salesman
    WHERE commission = (
        SELECT MAX(commission)
        FROM salesman
    )
);

```

**Output:**

<img width="1143" height="514" alt="image" src="https://github.com/user-attachments/assets/ff0becd2-237d-472f-a635-a91b5649078c" />


**Question 2**
---
<img width="1257" height="685" alt="image" src="https://github.com/user-attachments/assets/80a104fc-7519-427e-9bcf-55abf1efe4b8" />


```sql
select * from Employee where age<(select avg(age) from Employee where income>250000);
```

**Output:**

<img width="1336" height="607" alt="image" src="https://github.com/user-attachments/assets/85ecdcb6-2857-4bf5-8d41-9d1fe95a364a" />


**Question 3**
---
<img width="1253" height="557" alt="image" src="https://github.com/user-attachments/assets/978f7307-53b9-4592-9e1a-97f017ae5d3d" />


```sql
select * from orders where salesman_id in(select salesman_id from salesman where name='Paul Adam');
```

**Output:**

<img width="1377" height="503" alt="image" src="https://github.com/user-attachments/assets/2203322a-1062-49a1-9f4d-201ace5f28fc" />


**Question 4**
---
<img width="1171" height="704" alt="image" src="https://github.com/user-attachments/assets/03fca626-d35e-4eb2-98e9-e2748e438242" />


```sql
select commission from salesman where salesman_id in(select salesman_id from customer where city='Paris');
```

**Output:**

<img width="765" height="464" alt="image" src="https://github.com/user-attachments/assets/e86ebfed-c591-4b7b-9e0e-a9eb40b9fc8c" />


**Question 5**
---
<img width="1306" height="695" alt="image" src="https://github.com/user-attachments/assets/fde5ea8e-9802-4dbd-a835-018b45b4defa" />


```sql
select student_name,grade from GRADES t where grade in(select min(grade) from GRADES S where t.subject=S.subject);
```

**Output:**

<img width="923" height="561" alt="image" src="https://github.com/user-attachments/assets/757dabb5-ea07-4ec2-9e2e-44a62faba0c5" />


**Question 6**
---
<img width="1295" height="497" alt="image" src="https://github.com/user-attachments/assets/7ce3ab3c-6106-49a4-a5fb-bb804e22a0b6" />

```
SELECT department_id, department_name
FROM departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM departments
);

```

**Output:**

<img width="824" height="519" alt="image" src="https://github.com/user-attachments/assets/55984e53-7e18-49b2-95ef-c8cb538d1649" />


**Question 7**
---
<img width="1210" height="828" alt="image" src="https://github.com/user-attachments/assets/f8ea11f8-d608-4896-87a1-17206a432385" />

```sql
select * from CUSTOMERS where age <30;
```

**Output:**

<img width="1282" height="692" alt="image" src="https://github.com/user-attachments/assets/a7db686e-f6a8-415d-888c-d6a54c7ad2e4" />


**Question 8**
---
<img width="1127" height="782" alt="image" src="https://github.com/user-attachments/assets/215d389d-6005-4f2a-8968-bbae7e4a2b7d" />


```sql
select * from CUSTOMERS where salary>1500;
```

**Output:**

<img width="1372" height="702" alt="image" src="https://github.com/user-attachments/assets/97e2e8ad-4c0e-4ed7-b2f1-7b47f50c4e4c" />


**Question 9**
---
<img width="1128" height="579" alt="image" src="https://github.com/user-attachments/assets/0e00ed7e-c7d3-40d7-a98d-c75f0c5d7718" />


```sql
select medication_id,medication_name,dosage from Medications where dosage=(select max(dosage) from Medications);
```

**Output:**

<img width="989" height="511" alt="image" src="https://github.com/user-attachments/assets/d92abc8a-6b7f-4401-90a0-e4b620d8ab30" />


**Question 10**
---
<img width="1269" height="667" alt="image" src="https://github.com/user-attachments/assets/4d64ad1b-8272-4864-93c2-6cfe70aa871e" />


```sql
select * from ORDERS where purch_amt>(select avg(purch_amt)  from ORDERS where ord_date='2012-10-10');
```

**Output:**

<img width="1358" height="597" alt="image" src="https://github.com/user-attachments/assets/9879a5cf-921c-45c8-9032-f3e9c2839b6b" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
