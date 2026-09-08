# Experiment 4: Aggregate Functions, Group By and Having Clause

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
--
<img width="1158" height="516" alt="image" src="https://github.com/user-attachments/assets/98f221aa-0788-42d9-8daa-757b8fb4b26a" />


```sql
select PatientID ,count(Medications) as AvgMedications from MedicalRecords group by PatientID;
```

**Output:**

<img width="727" height="705" alt="image" src="https://github.com/user-attachments/assets/9e8097a7-b298-4793-b79b-b2d775337fa5" />


**Question 2**
---
<img width="993" height="687" alt="image" src="https://github.com/user-attachments/assets/b0fed660-cea5-46fd-9bf3-1624d3185dc8" />


```sql
select InsuranceCompany,Avg(EndDate-StartDate) as AvgCoverageDurationDays from Insurance group by InsuranceCompany;
```

**Output:**

<img width="1005" height="757" alt="image" src="https://github.com/user-attachments/assets/94495a07-3802-41ac-a247-1838bdc73d21" />


**Question 3**
---
<img width="1107" height="614" alt="image" src="https://github.com/user-attachments/assets/65bdfdc5-e6ba-4c36-b83d-c1c4da888d5c" />


```sql
select Specialty,COUNT(DoctorID) as TotalDocto from Doctors group by Specialty;
```

**Output:**

<img width="811" height="766" alt="image" src="https://github.com/user-attachments/assets/b9076893-9c59-4fa5-b3be-926624f9a820" />


**Question 4**
---
<img width="1045" height="526" alt="image" src="https://github.com/user-attachments/assets/513cc937-f26c-4f32-8462-aeb33adb9571" />


```sql
select COUNT(  distinct salesman_id) as COUNT from orders;
```

**Output:**

<img width="620" height="410" alt="image" src="https://github.com/user-attachments/assets/e50402ad-4caf-4dfe-93ea-2f6b8e40e8b7" />


**Question 5**
---
<img width="798" height="511" alt="image" src="https://github.com/user-attachments/assets/6675987f-6969-492a-a6d2-47ca48a5f853" />


```sql
SELECT MIN(purch_amt) as MINIMUM FROM orders;
```

**Output:**

<img width="505" height="429" alt="image" src="https://github.com/user-attachments/assets/2e5966ce-334c-4d5d-8e47-be7b814f7f77" />


**Question 6**
---

<img width="749" height="535" alt="image" src="https://github.com/user-attachments/assets/6a78075e-5573-47ac-8eb3-a2d7705faddf" />


```sql
select avg(income) as Average_Salary from employee;
```

**Output:**


<img width="637" height="416" alt="image" src="https://github.com/user-attachments/assets/2ac73a37-0d18-4b94-85a1-758fcd7ad42a" />


**Question 7**
---

<img width="896" height="486" alt="image" src="https://github.com/user-attachments/assets/78ae7227-89ad-4db3-9f14-55af248866f8" />

```sql
select name,max(income) from employee where city='California' order by max(income) desc;
```

**Output:**


<img width="765" height="454" alt="image" src="https://github.com/user-attachments/assets/417a2ca8-68f9-423f-a8bb-e7f2d44adb0d" />


**Question 8**
---

<img width="1242" height="628" alt="image" src="https://github.com/user-attachments/assets/d399c9dc-8ee7-47b9-b731-c7e554e34d76" />


```sql
select city,sum(income)  as Income from employee group by city having sum(income)>200000;
```

**Output:**


<img width="861" height="637" alt="image" src="https://github.com/user-attachments/assets/9d62488a-d835-42aa-88ee-f85fd79e8c3e" />

**Question 9**
---

<img width="1271" height="613" alt="image" src="https://github.com/user-attachments/assets/ff437a41-edec-4d8a-b079-894138800460" />

```sql
select age-age%5 as age_group ,MAX(salary) from customer1 group by age-age%5 having MAX(salary)>8000;
```

**Output:**


<img width="737" height="508" alt="image" src="https://github.com/user-attachments/assets/a11fb448-579f-4566-91cd-8ae31556e1a5" />


**Question 10**
---

<img width="1228" height="515" alt="image" src="https://github.com/user-attachments/assets/f67e6b86-8dc6-4338-b5e5-ee3322efc6ba" />


```sql
select category_id,AVG(Price) from products group by category_id having AVG(Price) between 10 and 15;
```

**Output:**


<img width="760" height="470" alt="image" src="https://github.com/user-attachments/assets/7189ee1b-06e6-46f2-8a37-367635660663" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
