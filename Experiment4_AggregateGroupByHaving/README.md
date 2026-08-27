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
<img width="572" height="497" alt="image" src="https://github.com/user-attachments/assets/bdf22931-c82d-483e-958e-350878203fa8" />


```sql
SELECT DoctorID, COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY DoctorID;
```

**Output:**

<img width="745" height="630" alt="image" src="https://github.com/user-attachments/assets/35ef34b0-79cc-4abc-8aa0-5694032f18d5" />



**Question 2**
---
<img width="626" height="537" alt="image" src="https://github.com/user-attachments/assets/b88c640c-9171-4d00-9c5a-d3a59711596e" />


```sql
SELECT DATE(AppointmentDateTime) AS AppointmentDate,
       COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime)
ORDER BY AppointmentDate;
```

**Output:**

<img width="760" height="577" alt="image" src="https://github.com/user-attachments/assets/ccaedeff-438b-4515-b958-026e2d9a1d1c" />


**Question 3**

<img width="778" height="517" alt="image" src="https://github.com/user-attachments/assets/e77f1bef-8d68-46be-b9d3-4efa2dfce034" />

```sql
SELECT Medication, AVG(CAST(REPLACE(Dosage, ' mg', '') AS REAL)) AS AvgDosage
FROM Prescriptions
GROUP BY Medication
ORDER BY Medication;
```

**Output:**

<img width="825" height="647" alt="image" src="https://github.com/user-attachments/assets/a300e8d7-3e77-486d-b628-b49136e1c0f6" />


**Question 4**
---
<img width="650" height="366" alt="image" src="https://github.com/user-attachments/assets/92a74017-248c-45cb-a51f-757c00f20798" />

```sql
SELECT name, email, LENGTH(email) AS min_email_length
FROM customer
ORDER BY LENGTH(email)
LIMIT 1;
```

**Output:**

<img width="947" height="438" alt="image" src="https://github.com/user-attachments/assets/cf7551c6-5293-4bb8-af30-c430bd844d93" />

**Question 5**
---
<img width="725" height="365" alt="image" src="https://github.com/user-attachments/assets/b1542ce1-a912-4074-832a-109be06b3ffa" />

```sql
SELECT AVG(LENGTH(email)) AS avg_email_length
FROM customer;
```

**Output:**

<img width="627" height="345" alt="image" src="https://github.com/user-attachments/assets/1217ecdc-4cd7-47e3-ae5c-c2d8e7f7c3b8" />

**Question 6**
---
<img width="788" height="396" alt="image" src="https://github.com/user-attachments/assets/7670e8b5-be64-4b28-8025-c492d0830d5b" />


```sql
SELECT COUNT(*) AS COUNT
FROM employee
WHERE age > 32;
```

**Output:**
<img width="622" height="333" alt="image" src="https://github.com/user-attachments/assets/34f5a9e0-c072-44a0-9782-6c6db59326c0" />



**Question 7**
---

<img width="672" height="417" alt="image" src="https://github.com/user-attachments/assets/a73a3f90-ccf9-4429-90e6-4f54c0048dbe" />

```sql
SELECT name, max(income)
FROM employee
WHERE city = 'California';
```

**Output:**
<img width="712" height="320" alt="image" src="https://github.com/user-attachments/assets/deea94a3-83fb-49ad-818f-54a1d6b4c86b" />



**Question 8**
---
<img width="725" height="395" alt="image" src="https://github.com/user-attachments/assets/db9d7366-85ca-4862-b93b-a69e57611c8f" />


```sql
SELECT PatientID, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID
HAVING COUNT(*) > 3;
```

**Output:**

<img width="753" height="322" alt="image" src="https://github.com/user-attachments/assets/ed0d3292-65a3-4e76-bb67-2e9b87b25c1c" />


**Question 9**
---
<img width="762" height="417" alt="image" src="https://github.com/user-attachments/assets/ccf46dd0-1d7c-43a3-aa1c-f922261bbc4b" />

```sql
SELECT age, MIN(income) AS Income
FROM employee
GROUP BY age
HAVING MIN(income) < 1000000;
```

**Output:**
<img width="570" height="407" alt="image" src="https://github.com/user-attachments/assets/673ed9ed-98c4-47da-a8b7-41f377445738" />



**Question 10**
---
<img width="750" height="403" alt="image" src="https://github.com/user-attachments/assets/dc22e9f5-66ed-4731-8b6d-e874586880cd" />


```sql
SELECT age, AVG(income)
FROM employee
GROUP BY age
HAVING AVG(income) BETWEEN 300000 AND 500000;
```

**Output:**

<img width="822" height="365" alt="image" src="https://github.com/user-attachments/assets/b186c557-b33d-493d-af9c-bb41dbf46fa4" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
