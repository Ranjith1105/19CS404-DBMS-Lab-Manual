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
-- ![Screenshot 2025-04-29 130929](https://github.com/user-attachments/assets/36ff204e-3f8b-416d-82fe-eb1d8f89b143)


```sql
-- select date(AppointmentDateTime) as AppointmentDate, count(*) as  TotalAppointments

from Appointments
group by AppointmentDate;
```

**Output:**
![Screenshot 2025-04-29 131010](https://github.com/user-attachments/assets/47d1740e-89ab-4a74-b978-2dd156b5452a)


**Question 2**
---
-- ![Screenshot 2025-04-29 131505](https://github.com/user-attachments/assets/458094fb-3ec1-464b-a0b1-0e599bf83844)


```sql
-- select name,email,length(email) as  min_email_length
from customer
order by length(email)
limit 1;
```

**Output:**
![Screenshot 2025-04-29 131514](https://github.com/user-attachments/assets/7ff52baa-ed62-4bbd-8ecd-103d7fc949f4)


**Question 3**
---
--![Screenshot 2025-04-29 131558](https://github.com/user-attachments/assets/d054f243-ab5a-49e1-bdd9-071c29ff5199)


```sql
-- select avg(length(email)) as avg_email_length
from customer
order by length(email)
limit 1;
```

**Output:**
![Screenshot 2025-04-29 131605](https://github.com/user-attachments/assets/c279b3db-a9e8-4dcf-b38a-cd467996b4f9)


**Question 4**
---
-- ![Screenshot 2025-04-29 131915](https://github.com/user-attachments/assets/08bb463d-4280-40ab-9aa0-44359d76ce0a)


```sql
-- select sum(purch_amt) as TOTAL
from orders

```

**Output:**

![Screenshot 2025-04-29 131922](https://github.com/user-attachments/assets/2eaa2a23-41eb-4ebe-874d-f3cb8da408dc)

**Question 5**
---
-- ![Screenshot 2025-04-29 132020](https://github.com/user-attachments/assets/dac02082-7b58-437f-b882-6a4a8577855e)


```sql
-- select jdate,MIN(workhour)
from employee1
group by jdate
having MIN(workhour) <10 ;
```

**Output:**

![Screenshot 2025-04-29 132028](https://github.com/user-attachments/assets/7fb2af83-d2fc-4b63-afdc-155a15b9ed1f)


**Question 6**
---
-- ![Screenshot 2025-04-29 132154](https://github.com/user-attachments/assets/60415fd3-634c-495a-8976-6e0c69331fc7)


```sql
-- select max(purch_amt) as MAXIMUM
from orders
order by purch_amt;
```

**Output:**

![Screenshot 2025-04-29 132200](https://github.com/user-attachments/assets/7856ad29-281c-46cd-b4cf-9b0317ccaaa3)


**Question 7**
---
--![Screenshot 2025-04-29 132439](https://github.com/user-attachments/assets/69505d3d-ec33-4ddb-ad2a-bc32a6897b2d)


```sql
-- select address,AVG(salary)
from customer1
group by address
having avg(salary) > 5000
```

**Output:**

![Screenshot 2025-04-29 132444](https://github.com/user-attachments/assets/2b6c1fe5-e596-478e-9bf8-6815e4b0244c)


**Question 8**
---
-- ![Screenshot 2025-04-29 132528](https://github.com/user-attachments/assets/338964ef-b49c-4a0c-8da4-e748cfac32a8)


```sql
-- select category_id,count(product_name)
from products
group by category_id
having min(category_id) <3
```

**Output:**

![Screenshot 2025-04-29 132540](https://github.com/user-attachments/assets/10b3464b-e56c-47a0-97e5-9c196fbbfc27)


**Question 9**
---
-- ![Screenshot 2025-04-29 132654](https://github.com/user-attachments/assets/475ab1a2-c99e-491c-8eaf-59d85ffe746d)


```sql
-- select sum(inventory) as total
from fruits
where unit ='LB'
```

**Output:**

![Screenshot 2025-04-29 132659](https://github.com/user-attachments/assets/6a62558f-388d-4e8c-ba0b-8b2802c8642d)


**Question 10**
---
-- ![Screenshot 2025-04-29 133000](https://github.com/user-attachments/assets/31812179-ff28-4a67-ae56-1348dbb07d93)


```sql
-- select count(distinct salesman_id) as COUNT
from orders

```

**Output:**

![Screenshot 2025-04-29 133004](https://github.com/user-attachments/assets/a87afd7f-b9d4-45fa-a6ea-86cd136bd9fd)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
