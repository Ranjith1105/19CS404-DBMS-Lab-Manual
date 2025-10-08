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
![Screenshot 2025-04-29 094759](https://github.com/user-attachments/assets/1ff73ec5-f6a1-4e70-9010-161c6f3772f6)



```sql
--
INSERT INTO Employee(EmployeeID,Name,Position)
values(5,           'George Clark',  'Consultant');

INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
values(7,           'Noah Davis',    'Manager',     'HR',          60000);

INSERT INTO Employee(EmployeeID,Name,Position,Department)
values(8,           'Ava Miller',    'Consultant',  'IT');
```

**Output:**
![Screenshot 2025-04-29 124245](https://github.com/user-attachments/assets/89435e54-9c59-4711-bc20-d0f6f9f6e311)




**Question 2**
---
--![image](https://github.com/user-attachments/assets/ca0a9da9-7501-4266-ba08-645feed50fd9)

```sql
-- 
CREATE TABLE Attendance (  
    AttendanceID INTEGER PRIMARY KEY,  
    EmployeeID INTEGER,  
    AttendanceDate DATE,  
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),  
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)  
);
```

**Output:**

![image](https://github.com/user-attachments/assets/c39daf8f-3430-4210-a8ff-d01b24a63277)


**Question 3**
---
--![image](https://github.com/user-attachments/assets/dae1d226-9026-4d29-9254-7de0910c737f)


```sql
--
ALTER TABLE Employees
ADD COLUMN Date_of_joining Date;

ALTER TABLE Employees
RENAME COLUMN job_title To Designation;


```

**Output:**

![image](https://github.com/user-attachments/assets/34ffec3a-d6f4-4db9-a215-4b0e07cf2498)


**Question 4**
---
-- ![image](https://github.com/user-attachments/assets/5269cf0c-35ef-423a-8f4d-e23d598326c0)

```sql
--
 CREATE TABLE jobs (  
    job_id INTEGER PRIMARY KEY,  
    job_title TEXT NOT NULL DEFAULT '',  
    min_salary INTEGER NOT NULL DEFAULT 8000,  
    max_salary INTEGER DEFAULT NULL  
);
```

**Output:**
![image](https://github.com/user-attachments/assets/6ac5521f-2c29-4742-8243-8b4e41797c86)


**Question 5**
---
-- ![image](https://github.com/user-attachments/assets/df2640c1-2236-4197-a730-8d3801cdb17b)


```sql
--
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**
![image](https://github.com/user-attachments/assets/455829b4-4134-45de-b480-5692c256072d)


**Question 6**
---
--![image](https://github.com/user-attachments/assets/9e2758a1-6ee5-4c45-8061-abac41022770)


```sql
--
select *from Out_of_print_books
union all
select *from Books
```

**Output:**
![image](https://github.com/user-attachments/assets/151cdda8-17c8-4153-9df3-34567f3eaa0f)


**Question 7**
---
--![image](https://github.com/user-attachments/assets/c8c69844-81cf-4cf9-8eba-a0b0d0bb6701)


```sql
--
CREATE TABLE item (  
    item_id TEXT PRIMARY KEY,  
    item_desc TEXT NOT NULL,  
    rate INTEGER NOT NULL,  
    icom_id TEXT CHECK(4),  
    FOREIGN KEY (icom_id) REFERENCES company(com_id)  
    ON UPDATE CASCADE  
    ON DELETE CASCADE  
);
```

**Output:**
![image](https://github.com/user-attachments/assets/4880a2ef-a33b-4cc3-b31c-216f255b2b67)


**Question 8**
---
-- ![image](https://github.com/user-attachments/assets/7096c7b2-8067-45fb-95ce-c61bec119446)


```sql
--
ALTER TABLE employee
ADD COLUMN designation varchar(50);
```

**Output:**
![image](https://github.com/user-attachments/assets/0f2267dc-bc94-49e4-84e3-2a143335f3cf)


**Question 9**
---
-- ![image](https://github.com/user-attachments/assets/06d2e58d-4853-4ba5-9d54-f03e0c410af6)


```sql
--
INSERT INTO Products (ProductID, Name, Category)  
VALUES (104, 'Tablet', 'Electronics');
```

**Output:**

![image](https://github.com/user-attachments/assets/439c6599-0b13-49c7-95a4-3d53ecfde7bc)


**Question 10**
---
--![image](https://github.com/user-attachments/assets/9424a09d-c763-4283-85b1-287761ae025d)


```sql
--
CREATE TABLE Employees(
EmployeeID INTEGER primary key,
FirstName INTEGER NOT NULL,
LastName INTEGER NOT NULL,
Email VARCHAR(50) unique,
Salary CHECK (Salary>0),
DepartmentID INTEGER,
foreign key(DepartmentID) references Departments(DepartmentID)
);
```

**Output:**
![image](https://github.com/user-attachments/assets/8631abbc-db12-4fe7-bbf9-06bffaa06c5a)




## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
