# Experiment 6: Joins

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
--
<img width="1284" height="776" alt="image" src="https://github.com/user-attachments/assets/01a9825a-4065-47c9-add4-8421299da49d" />

```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM orders o
JOIN customer c
ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;

```

**Output:**

<img width="1356" height="603" alt="image" src="https://github.com/user-attachments/assets/6ed7a3f6-3b46-48a1-aae3-31e91f1aad64" />


**Question 2**
---
<img width="1216" height="810" alt="image" src="https://github.com/user-attachments/assets/dc863de4-a758-444e-8b24-e45f0d18f9b9" />


```sql
SELECT 
    p.first_name,
    s.surgery_id,
    s.patient_id,
    s.surgeon_id,
    s.surgery_date
FROM patients p
INNER JOIN surgeries s
ON p.patient_id = s.patient_id
WHERE p.first_name = 'Alice';

```

**Output:**

<img width="1355" height="533" alt="image" src="https://github.com/user-attachments/assets/0dfdde7c-90d6-408b-be3f-9b94fa8269c2" />


**Question 3**
---
<img width="1325" height="581" alt="image" src="https://github.com/user-attachments/assets/a4f0beeb-0272-4dce-8b2f-43c5853024a9" />


```sql
SELECT 
    s.name AS salesman_name,
    c.cust_name AS customer_name
FROM salesman s
LEFT JOIN customer c
ON s.salesman_id = c.salesman_id;

```

**Output:**

<img width="1116" height="616" alt="image" src="https://github.com/user-attachments/assets/9da64969-fbc6-4926-bf6e-c625148149e9" />

**Question 4**
---
<img width="1301" height="715" alt="image" src="https://github.com/user-attachments/assets/4e111b9b-d1a1-4f89-88cc-79c06fd5cb06" />


```sql
SELECT 
    p.first_name AS patient_name
FROM patients p
INNER JOIN test_results t
ON p.patient_id = t.patient_id
WHERE t.test_name = 'Blood Pressure';

```

**Output:**

<img width="601" height="513" alt="image" src="https://github.com/user-attachments/assets/700172ac-98d3-43ee-9b37-2bbf9d50c99d" />

**Question 5**
---
<img width="1259" height="452" alt="image" src="https://github.com/user-attachments/assets/ce9b462c-e7b0-4c47-ba41-d833d4b64a96" />


```sql
SELECT 
    c.cust_name
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
WHERE o.purch_amt < 100;

```

**Output:**

<img width="824" height="596" alt="image" src="https://github.com/user-attachments/assets/103d0a38-d315-4de4-be39-2f8cbeca20e8" />

**Question 6**
---
<img width="1281" height="738" alt="image" src="https://github.com/user-attachments/assets/a8e42999-b8a7-48cd-8ebc-7b401acffe60" />


```sql
SELECT 
    p.*
FROM patients p
INNER JOIN test_results t
ON p.patient_id = t.patient_id
WHERE (t.test_name = 'Blood Test' OR t.test_name = 'Blood Pressure')
AND t.result NOT LIKE '%Normal%';

```

**Output:**

<img width="1365" height="508" alt="image" src="https://github.com/user-attachments/assets/1458c898-5100-4d94-9c1c-83e539483dee" />


**Question 7**
---
<img width="1330" height="855" alt="image" src="https://github.com/user-attachments/assets/9dda7fd1-2b2b-4832-9695-cdbd91c180f1" />


```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM orders o
JOIN customer c 
    ON o.customer_id = c.customer_id
JOIN salesman s 
    ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1372" height="771" alt="image" src="https://github.com/user-attachments/assets/14d3cf86-4433-487b-9a88-4ca5144b20da" />

**Question 8**
---
<img width="1264" height="656" alt="image" src="https://github.com/user-attachments/assets/f009ee77-79ef-485a-a374-cbbd50875551" />


```sql
SELECT 
    c.cust_name AS 'Customer Name',
    c.city AS city,
    s.name AS Salesman,
    s.commission
FROM customer c
JOIN salesman s
ON c.salesman_id = s.salesman_id;

```

**Output:**

<img width="1331" height="620" alt="image" src="https://github.com/user-attachments/assets/93e24a83-83ef-4c9f-8d3f-af05f530a6a2" />


**Question 9**
---
<img width="1279" height="636" alt="image" src="https://github.com/user-attachments/assets/f4dfab13-dad7-4538-a146-dde36acec510" />

```sql
SELECT c.cust_name, c.city, c.grade, s.name AS Salesman, s.city AS city
FROM customer c
JOIN salesman s
ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;


```

**Output:**

<img width="1354" height="594" alt="image" src="https://github.com/user-attachments/assets/87c16a6b-7002-47c8-b45b-4b2acd3571fe" />


**Question 10**
---

<img width="1301" height="656" alt="image" src="https://github.com/user-attachments/assets/600f2aa3-7164-441b-9b6e-579b907ca9ae" />


```sql
SELECT c.cust_name as 'Customer Name', c.city as city, s.name AS Salesman, s.commission
FROM customer c
JOIN salesman s
ON c.salesman_id = s.salesman_id;

```

**Output:**

<img width="1323" height="614" alt="image" src="https://github.com/user-attachments/assets/a69a1e8d-ce75-4be1-a4f8-bdf4e14550f7" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
