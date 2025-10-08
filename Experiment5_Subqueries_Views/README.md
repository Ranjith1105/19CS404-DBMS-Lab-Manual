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
-- ![Screenshot 2025-04-29 140920](https://github.com/user-attachments/assets/e9bb55a0-ef1c-49e5-9d77-9c147822d3f3)


```sql
-- SELECT * 
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**
![Screenshot 2025-04-29 140926](https://github.com/user-attachments/assets/82dfbc89-4071-41b5-9b0c-8b6b5dbd7ebd)



**Question 2**
---
-- ![Screenshot 2025-04-29 141038](https://github.com/user-attachments/assets/93d0cd11-d5c2-4f23-b08b-4a9dcbef4e7d)


```sql
-- SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM ORDERS o
JOIN SALESMAN s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```

**Output:**
![Screenshot 2025-04-29 141048](https://github.com/user-attachments/assets/96d7ce09-5ca6-49cd-8b21-0bceb8072347)



**Question 3**
---
-- ![Screenshot 2025-04-29 141156](https://github.com/user-attachments/assets/8cb24975-fdd1-4a13-a21a-0cf8680b04e0)

```sql
-- SELECT g.student_name, g.grade
FROM GRADES g
WHERE g.grade = (
    SELECT MAX(g2.grade)
    FROM GRADES g2
    WHERE g2.subject = g.subject
);
```

**Output:**
![Screenshot 2025-04-29 141202](https://github.com/user-attachments/assets/7b5b84f8-edda-4741-b13d-2b51ac4dfcb6)



**Question 4**
---
-- ![Screenshot 2025-04-29 141354](https://github.com/user-attachments/assets/9ff0825e-9c67-4ffe-9e92-3f661c3ded5d)


```sql
-- SELECT name
FROM customer
WHERE phone IN (
    SELECT phone
    FROM customer
    GROUP BY phone
    HAVING COUNT(*) = 1
);

```

**Output:**

![Screenshot 2025-04-29 141359](https://github.com/user-attachments/assets/6df18253-6313-414f-a52a-e7c6230b5561)


**Question 5**
---
--![Screenshot 2025-04-29 141459](https://github.com/user-attachments/assets/1dc4420f-645f-40c7-a3ba-1c851cf9cb00)


```sql
-- SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;

```

**Output:**

![Screenshot 2025-04-29 141505](https://github.com/user-attachments/assets/fe0157d8-3868-4632-b0c6-7bf311a43356)


**Question 6**
---
-- ![Screenshot 2025-04-29 141556](https://github.com/user-attachments/assets/7cb63ea6-499d-4ed3-bfc8-934ede81615b)


```sql
-- SELECT s.salesman_id, s.name
FROM salesman s
JOIN customer c ON s.salesman_id = c.salesman_id
GROUP BY s.salesman_id, s.name
HAVING COUNT(c.customer_id) > 1;

```

**Output:**
![Screenshot 2025-04-29 141604](https://github.com/user-attachments/assets/16a84145-3969-4bde-9551-162d462d16f2)



**Question 7**
---
-- ![Screenshot 2025-04-29 141644](https://github.com/user-attachments/assets/ff9b5962-abb0-47c6-bda0-1ac6f4e4120a)


```sql
-- SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE purch_amt > (
    SELECT AVG(purch_amt)
    FROM orders
    WHERE ord_date = '2012-10-10'
);
```

**Output:**
![Screenshot 2025-04-29 141651](https://github.com/user-attachments/assets/ecb2e288-2a9c-461e-9d1b-da1eb324bb58)



**Question 8**
---
-- ![Screenshot 2025-04-29 141746](https://github.com/user-attachments/assets/96314594-cec5-4bff-96ac-2fcdc0cbd80d)


```sql
-- SELECT *
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (SELECT MAX(id) FROM customer)
);

```

**Output:**

![Screenshot 2025-04-29 141758](https://github.com/user-attachments/assets/5e0d0b67-1a11-433a-aa99-6840a129c9c4)


**Question 9**
---
-- ![Screenshot 2025-04-29 141841](https://github.com/user-attachments/assets/84a903d4-efa6-46ff-9adb-e3ab75e99d54)


```sql
--SELECT *
FROM CUSTOMERS
WHERE AGE < 30;

```

**Output:**

![Screenshot 2025-04-29 141850](https://github.com/user-attachments/assets/cdd36191-66d0-48ff-8b73-b9e4541d5d86)


**Question 10**
---
-- ![Screenshot 2025-04-29 151446](https://github.com/user-attachments/assets/79dfb804-513e-4811-8595-3421250804bf)


```sql
-- select medication_id, medication_name, dosage from Medications
where dosage=(select max(dosage) from Medications)
```

**Output:**

![Screenshot 2025-04-29 151451](https://github.com/user-attachments/assets/e1d4d9ed-731c-4bc3-80b3-124471823ece)



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
