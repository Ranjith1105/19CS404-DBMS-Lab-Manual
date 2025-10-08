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
-- ![Screenshot 2025-04-29 121653](https://github.com/user-attachments/assets/53b5f3b9-c9b6-4e2b-a010-2876d7e71d58)
-- ![Screenshot 2025-04-29 121523](https://github.com/user-attachments/assets/6218b66c-b292-4f15-9f78-d07da1e45385)



```sql
-- INSERT INTO Customers(CustomerID  ,Name,             Address,         Email)
SELECT CustomerID  ,Name             ,Address         ,Email FROM Old_customers;
```
```sql
-- INSERT INTO Customers(CustomerID ,Name,Address, City     ,   ZipCode)VALUES (301, "Michael Jordan",  "123 Maple St",  "Chicago",  60616);
```
**Output:**

![Screenshot 2025-04-29 121659](https://github.com/user-attachments/assets/8cb31551-6831-454d-b418-edd48d7eb67f)
![Screenshot 2025-04-29 121536](https://github.com/user-attachments/assets/c63a44bb-a3d1-41fb-bac6-878256b773b3)


**Question 2**
---
-- ![Screenshot 2025-04-29 123037](https://github.com/user-attachments/assets/1f0eb809-77c1-44ef-afa2-8421dcb11740)


```sql
-- UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id =4;
```

**Output:**

![Screenshot 2025-04-29 123046](https://github.com/user-attachments/assets/fac16b56-8a39-4f79-85ce-bbb4c7e859c6)


**Question 3**
---
--![Screenshot 2025-04-29 123317](https://github.com/user-attachments/assets/777ae485-23f4-4483-8715-29b910b9a718)


```sql
-- DELETE FROM surgeries
WHERE  surgery_id =3;
```

**Output:**
![Screenshot 2025-04-29 123327](https://github.com/user-attachments/assets/ed8e9b00-3bf7-4fff-8b31-4e8298e55694)


**Question 4**
---
-- ![Screenshot 2025-04-29 123951](https://github.com/user-attachments/assets/fbbc9c48-b733-4c6e-881c-da2102440159)


```sql
-- SELECT customer_id, cust_name, city, grade, salesman_id
FROM  customer
WHERE  grade >100;
```

**Output:**

![Screenshot 2025-04-29 124001](https://github.com/user-attachments/assets/57d14ec4-855c-4b61-8374-1114b9dec239)


**Question 5**
---
-- ![Screenshot 2025-04-29 134956](https://github.com/user-attachments/assets/2e173acd-15a6-4d60-b8b9-c4b039481a65)


```sql
-- SELECT ename,hiredate,DATE(hiredate ,'+100 Days') AS DateAfter100Days
FROM emp;
```

**Output:**
![Screenshot 2025-04-29 135004](https://github.com/user-attachments/assets/5a348d18-aeeb-4137-9a5a-e08c5c24223c)



**Question 6**
---
-- ![Screenshot 2025-04-29 135215](https://github.com/user-attachments/assets/88829371-d33e-4cd0-a174-a0926e8eabb6)


```sql
-- SELECT id,ROUND(decimal,3) AS  rounded_value
FROM Calculations;
```

**Output:**

![Screenshot 2025-04-29 135222](https://github.com/user-attachments/assets/5f5b5228-2fed-4803-87d2-9897b3db8567)


**Question 7**
---
-- ![Screenshot 2025-04-29 135350](https://github.com/user-attachments/assets/1e205fbe-54c1-4a8a-a2af-1a9123217ee9)


```sql
-- DELETE FROM Customer
WHERE LENGTH(CUST_NAME) =6;
```

**Output:**

![Screenshot 2025-04-29 135415](https://github.com/user-attachments/assets/2a0b7aa7-d093-4b51-99e0-c95da4a2114d)


**Question 8**
---
-- ![Screenshot 2025-04-29 135607](https://github.com/user-attachments/assets/576f2b96-fb2f-41c3-a9d9-6de324daedaf)


```sql
-- UPDATE Employees 
SET salary = 8000
WHERE employee_id =105 AND salary < 5000;
```

**Output:**
![Screenshot 2025-04-29 135613](https://github.com/user-attachments/assets/28d12da8-8149-4782-8582-03b0f1ed09d9)



**Question 9**
---
--![Screenshot 2025-04-29 135759](https://github.com/user-attachments/assets/d6e7d168-f8bb-4156-9070-fee806976f26)


```sql
-- SELECT id, value1, 
        CASE 
           WHEN  value1 >50 THEN 'High'
           ELSE 'Low'
        END AS  value_category
FROM Calculations;

```

**Output:**
![Screenshot 2025-04-29 135803](https://github.com/user-attachments/assets/9ae7a5e9-2bfd-48f3-a187-40c6d38e38c8)



**Question 10**
---
-- ![Screenshot 2025-04-29 135949](https://github.com/user-attachments/assets/fe30c891-ce3e-47c4-9f5d-35b8ea958056)


```sql
-- SELECT 
    product_id, 
    original_price, 
    discount_percentage,
    original_price *discount_percentage AS discount_amount
FROM 
    products
WHERE  
    original_price * discount_percentage >50;
```

**Output:**

![Screenshot 2025-04-29 135954](https://github.com/user-attachments/assets/30bfdccc-5cf0-49cd-82fd-353e4e03c637)



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
