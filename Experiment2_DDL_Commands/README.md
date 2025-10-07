Experiment 2: DDL Commands
AIM
To study and implement DDL commands and different types of constraints.

THEORY
1. CREATE
Used to create a new relation (table).

Syntax:

CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
2. ALTER
Used to add, modify, drop, or rename fields in an existing relation. (a) ADD

ALTER TABLE std ADD (Address CHAR(10));
(b) MODIFY

ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
(c) DROP

ALTER TABLE relation_name DROP COLUMN field_name;
(d) RENAME

ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
3. DROP TABLE
Used to permanently delete the structure and data of a table.

DROP TABLE relation_name;
4. RENAME
Used to rename an existing database object.

RENAME TABLE old_relation_name TO new_relation_name;
CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).

1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
2. UNIQUE
Ensures that values in a column are unique. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
3. CHECK
Specifies a condition that each row must satisfy. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
4. PRIMARY KEY
Used to uniquely identify each record in a table. Properties: Must contain unique values. Cannot be null. Should contain minimal fields. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
5. FOREIGN KEY
Used to reference the primary key of another table. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:

CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
Question 1
Screenshot 2025-04-29 094759

--
INSERT INTO Employee(EmployeeID,Name,Position)
values(5,           'George Clark',  'Consultant');

INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
values(7,           'Noah Davis',    'Manager',     'HR',          60000);

INSERT INTO Employee(EmployeeID,Name,Position,Department)
values(8,           'Ava Miller',    'Consultant',  'IT');
Output: Screenshot 2025-04-29 124245

Question 2
--image

-- 
CREATE TABLE Attendance (  
    AttendanceID INTEGER PRIMARY KEY,  
    EmployeeID INTEGER,  
    AttendanceDate DATE,  
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),  
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)  
);
Output:

image

Question 3
--image

--
ALTER TABLE Employees
ADD COLUMN Date_of_joining Date;

ALTER TABLE Employees
RENAME COLUMN job_title To Designation;

Output:

image

Question 4
-- image

--
 CREATE TABLE jobs (  
    job_id INTEGER PRIMARY KEY,  
    job_title TEXT NOT NULL DEFAULT '',  
    min_salary INTEGER NOT NULL DEFAULT 8000,  
    max_salary INTEGER DEFAULT NULL  
);
Output: image

Question 5
-- image

--
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
Output: image

Question 6
--image

--
select *from Out_of_print_books
union all
select *from Books
Output: image

Question 7
--image

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
Output: image

Question 8
-- image

--
ALTER TABLE employee
ADD COLUMN designation varchar(50);
Output: image

Question 9
-- image

--
INSERT INTO Products (ProductID, Name, Category)  
VALUES (104, 'Tablet', 'Electronics');
Output:

image

Question 10
--image

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
Output: image

RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
