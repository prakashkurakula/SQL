# SQL
# SQL – DDL and DML Operations

## 📌 Table of Contents

1. Introduction to SQL
2. Types of SQL Commands
3. DDL (Data Definition Language)
   - CREATE
   - ALTER
   - DROP
   - TRUNCATE
   - RENAME
4. DML (Data Manipulation Language)
   - INSERT
   - UPDATE
   - DELETE
5. Difference Between DDL and DML
6. Real-Time Scenario-Based Examples
7. Important SQL Interview Questions
8. Best Practices
9. Conclusion

---

# 1. Introduction to SQL

**SQL (Structured Query Language)** is a standard programming language used to communicate with relational databases.

SQL allows users to create databases, create tables, insert records, modify existing records, retrieve data, and delete records.

### Why do we use SQL?

- To store and manage data.
- To create and maintain database structures.
- To insert new records into tables.
- To update existing information.
- To delete unwanted records.
- To retrieve required information from databases.

### Example

Consider an Employee Management System.

An organization maintains employee information such as:

- Employee ID
- Employee Name
- Department
- Salary
- Joining Date

SQL helps the organization create employee tables and manage employee records.

---

# 2. Types of SQL Commands

SQL commands are mainly divided into five categories.

| SQL Category | Full Form | Purpose |
|---|---|---|
| DDL | Data Definition Language | Defines database structure |
| DML | Data Manipulation Language | Modifies table records |
| DQL | Data Query Language | Retrieves data |
| DCL | Data Control Language | Controls user permissions |
| TCL | Transaction Control Language | Manages transactions |

### Example Commands

| Category | Commands |
|---|---|
| DDL | CREATE, ALTER, DROP, TRUNCATE, RENAME |
| DML | INSERT, UPDATE, DELETE |
| DQL | SELECT |
| DCL | GRANT, REVOKE |
| TCL | COMMIT, ROLLBACK, SAVEPOINT |

This README mainly focuses on **DDL and DML operations**.

---

# 3. DDL – Data Definition Language

## What is DDL?

DDL stands for **Data Definition Language**.

DDL commands are used to define, create, and modify the structure of database objects such as databases and tables.

DDL mainly works with the database schema rather than individual records.

### Main DDL Commands

1. CREATE
2. ALTER
3. DROP
4. TRUNCATE
5. RENAME

---

## 3.1 CREATE Command

### Definition

The CREATE command is used to create new database objects such as databases and tables.

We can create a database, table, view, and other supported database objects using CREATE.

### Syntax – Creating a Database

```sql
CREATE DATABASE database_name;
```

### Example

```sql
CREATE DATABASE company_db;
```

**Explanation:**

- CREATE: Creates a new database.
- DATABASE: Specifies that we are creating a database.
- company_db: Name of the database.

### Syntax – Creating a Table

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype
);
```

### Scenario-Based Example

**Scenario:** A company wants to maintain employee information. First, we need to create an employee table.

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    employee_name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10,2),
    joining_date DATE
);
```

**Explanation:**

| Column | Data Type | Purpose |
|---|---|---|
| employee_id | INT | Stores employee ID |
| employee_name | VARCHAR(100) | Stores employee name |
| department | VARCHAR(50) | Stores department |
| salary | DECIMAL(10,2) | Stores employee salary |
| joining_date | DATE | Stores joining date |

**Important Points:**

- CREATE creates a new database object.
- PRIMARY KEY uniquely identifies each record.
- VARCHAR stores variable-length text.
- INT stores integer values.
- DECIMAL stores numeric values with decimal places.
- DATE stores date values.

---

## 3.2 ALTER Command

### Definition

The ALTER command is used to modify the existing structure of a table.

Using ALTER, we can:

1. Add a new column.
2. Modify an existing column.
3. Rename a column.
4. Drop an existing column.

### A. ADD – Adding a New Column

**Syntax:**

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

**Scenario:**

The company wants to add an email column to the existing employee table.

```sql
ALTER TABLE employees
ADD email VARCHAR(100);
```

**Explanation:**

- ALTER TABLE: Modifies the existing table.
- employees: Name of the table.
- ADD: Adds a new column.
- email: New column name.
- VARCHAR(100): Data type.

### B. MODIFY – Modifying an Existing Column

**Syntax:**

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name new_datatype;
```

**Scenario:**

The company wants to increase the employee name column size from 100 to 150 characters.

```sql
ALTER TABLE employees
MODIFY COLUMN employee_name VARCHAR(150);
```

**Explanation:**

MODIFY changes the definition of an existing column, such as its data type or size.

### C. CHANGE – Renaming or Modifying a Column

**Syntax:**

```sql
ALTER TABLE table_name
CHANGE old_column_name new_column_name datatype;
```

**Scenario:**

The company wants to rename the employee_name column to full_name.

```sql
ALTER TABLE employees
CHANGE employee_name full_name VARCHAR(150);
```

**Explanation:**

CHANGE can rename a column and modify its definition.

Note: In MySQL, CHANGE requires the new column definition.

### D. DROP COLUMN – Removing a Column

**Syntax:**

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

**Scenario:**

The company no longer requires the email column.

```sql
ALTER TABLE employees
DROP COLUMN email;
```

**Explanation:**

DROP COLUMN permanently removes the specified column and its stored values from the table.

**Important Points:**

- ADD adds a new column.
- MODIFY changes an existing column definition.
- CHANGE renames and/or modifies a column.
- DROP COLUMN removes an existing column.
- ALTER changes table structure, not individual records.

---

## 3.3 DROP Command

### Definition

The DROP command is used to permanently remove an existing database object.

It can remove databases and tables.

### Syntax – Dropping a Table

```sql
DROP TABLE table_name;
```

### Scenario-Based Example

**Scenario:** The company decides to completely remove the old employee table because it is no longer required.

```sql
DROP TABLE employees;
```

**Explanation:**

- DROP: Removes an existing object.
- TABLE: Specifies the object type.
- employees: Name of the table.

### Dropping a Database

**Syntax:**

```sql
DROP DATABASE database_name;
```

**Example:**

```sql
DROP DATABASE company_db;
```

**Important Points:**

- DROP removes the complete table.
- Both table structure and stored records are removed.
- The operation is destructive.
- Use DROP carefully because recovering data may not be possible without a backup.

---

## 3.4 TRUNCATE Command

### Definition

The TRUNCATE command is used to remove all records from an existing table without removing its structure.

After executing TRUNCATE, the table remains available but contains no records.

### Syntax

```sql
TRUNCATE TABLE table_name;
```

### Scenario-Based Example

**Scenario:** A company has completed its annual employee data migration. It wants to remove all records from a temporary employee table while keeping the table structure.

```sql
TRUNCATE TABLE employees;
```

**Explanation:**

- TRUNCATE removes all rows.
- Table structure remains unchanged.
- It does not support a WHERE condition.
- In MySQL, it is a DDL operation and generally causes an implicit commit.
- AUTO_INCREMENT counters are reset in MySQL.

**Important Points:**

TRUNCATE is useful when we want to remove all records quickly while retaining the table structure.

---

## 3.5 RENAME Command

### Definition

The RENAME command is used to change the name of an existing table.

### Syntax

```sql
RENAME TABLE old_table_name
TO new_table_name;
```

### Scenario-Based Example

**Scenario:** The company wants to rename the employees table to staff_details.

```sql
RENAME TABLE employees
TO staff_details;
```

**Explanation:**

- RENAME TABLE: Renames an existing table.
- employees: Existing table name.
- staff_details: New table name.

**Important Points:**

- Only the table name changes.
- Table structure remains the same.
- Existing records remain unchanged.

---

# 4. DML – Data Manipulation Language

## What is DML?

DML stands for **Data Manipulation Language**.

DML commands are used to manipulate and manage the records stored inside database tables.

DML mainly works with the data present in a table.

### Main DML Commands

1. INSERT
2. UPDATE
3. DELETE

---

## 4.1 INSERT Command

### Definition

The INSERT command is used to add new records into an existing table.

We can insert a single record or multiple records into a table.

### A. Inserting a Single Record

**Syntax:**

```sql
INSERT INTO table_name
(column1, column2, column3)
VALUES
(value1, value2, value3);
```

### Scenario-Based Example

**Scenario:** A new employee joins the company. We need to insert the employee's details into the employees table.

```sql
INSERT INTO employees
(employee_id, employee_name, department, salary, joining_date)
VALUES
(101, 'Prakash', 'IT', 35000.00, '2026-11-12');
```

**Explanation:**

- INSERT INTO: Specifies the table where data should be inserted.
- employees: Table name.
- employee_id, employee_name: Column names.
- VALUES: Specifies the values to insert.
- 101, 'Prakash': Employee ID and employee name.

### B. Inserting Multiple Records

**Syntax:**

```sql
INSERT INTO table_name
(column1, column2, column3)
VALUES
(value1, value2, value3),
(value4, value5, value6),
(value7, value8, value9);
```

**Scenario:**

The HR department wants to add three new employees at the same time.

```sql
INSERT INTO employees
(employee_id, employee_name, department, salary, joining_date)
VALUES
(102, 'Rahul', 'HR', 30000.00, '2026-11-10'),
(103, 'Suresh', 'Finance', 40000.00, '2026-11-11'),
(104, 'Anjali', 'IT', 45000.00, '2026-11-12');
```

### C. Inserting Values Without Specifying Column Names

**Syntax:**

```sql
INSERT INTO table_name
VALUES (value1, value2, value3, value4, value5);
```

**Example:**

```sql
INSERT INTO employees
VALUES (105, 'Kiran', 'Sales', 32000.00, '2026-11-12');
```

**Important Points:**

- Values must match the column order.
- The number of values must match the number of columns unless defaults or auto-generated values are handled appropriately.
- Text values should be enclosed in single quotes.
- Specifying column names is recommended.

---

## 4.2 UPDATE Command

### Definition

The UPDATE command is used to modify existing records in a table.

We can update one column or multiple columns in a record.

### Syntax

```sql
UPDATE table_name
SET column_name = new_value
WHERE condition;
```

### A. Updating a Single Column

**Scenario:**

An employee named Prakash receives a salary increment. His salary changes from 35,000 to 45,000.

```sql
UPDATE employees
SET salary = 45000
WHERE employee_id = 101;
```

**Explanation:**

- UPDATE: Specifies the table to modify.
- employees: Table name.
- SET: Specifies the column and new value.
- salary = 45000: New salary.
- WHERE employee_id = 101: Identifies the employee to update.

### B. Updating Multiple Columns

**Scenario:**

An employee gets promoted from the IT department to the Manager position, and the salary is increased.

```sql
UPDATE employees
SET department = 'Management',
    salary = 60000
WHERE employee_id = 101;
```

**Explanation:**

We can update multiple columns in a single UPDATE statement by separating the assignments with commas.

### C. Updating Records Based on a Condition

**Scenario:**

The company wants to increase the salary of all employees in the IT department by 10%.

```sql
UPDATE employees
SET salary = salary * 1.10
WHERE department = 'IT';
```

**Explanation:**

- salary * 1.10 increases salary by 10%.
- WHERE department = 'IT' selects only IT employees.

### D. Updating All Records

**Scenario:**

The company wants to increase everyone's salary by 5%.

```sql
UPDATE employees
SET salary = salary * 1.05;
```

**Important Points:**

- UPDATE modifies existing records.
- SET specifies the new values.
- WHERE identifies the records to update.
- Without WHERE, all records in the table will be updated.
- Always check the WHERE condition before executing UPDATE.

---

## 4.3 DELETE Command

### Definition

The DELETE command is used to remove existing records from a table.

We can delete a particular record, multiple records, or all records.

### A. Deleting a Single Record

**Syntax:**

```sql
DELETE FROM table_name
WHERE condition;
```

**Scenario:**

An employee leaves the company. The HR department wants to remove that employee's record.

```sql
DELETE FROM employees
WHERE employee_id = 104;
```

**Explanation:**

- DELETE FROM: Specifies the table from which records should be deleted.
- employees: Table name.
- WHERE: Identifies the record to delete.
- employee_id = 104: Deletes the employee with ID 104.

### B. Deleting Multiple Records

**Scenario:**

The company wants to delete all employees belonging to the Sales department.

```sql
DELETE FROM employees
WHERE department = 'Sales';
```

**Explanation:**

All records matching the specified department condition will be deleted.

### C. Deleting All Records

**Scenario:**

The company wants to remove all employee records but keep the table structure.

```sql
DELETE FROM employees;
```

**Important Points:**

- DELETE removes records from a table.
- DELETE supports WHERE conditions.
- Without WHERE, all records will be deleted.
- Table structure remains unchanged.
- In MySQL, DELETE is a DML operation and can be rolled back when executed within a transaction before COMMIT.

---

# 5. Difference Between DDL and DML

| Feature | DDL | DML |
|---|---|---|
| Full Form | Data Definition Language | Data Manipulation Language |
| Purpose | Defines table structure | Manipulates table records |
| Works With | Schema | Data |
| Commands | CREATE, ALTER, DROP, TRUNCATE, RENAME | INSERT, UPDATE, DELETE |
| WHERE Condition | Generally not used | Used with UPDATE and DELETE |
| Transaction | Many DDL statements cause implicit commits in MySQL | Supports transaction control |
| Example | CREATE TABLE | INSERT INTO |

### Simple Real-Time Example

**DDL Example:**

```sql
CREATE TABLE students (
    student_id INT,
    student_name VARCHAR(100),
    marks INT
);
```

This query creates a new table structure.

**DML Example:**

```sql
INSERT INTO students
VALUES (1, 'Prakash', 90);
```

This query inserts a new record into the existing table.

**Remember:**

- DDL = Structure of the table.
- DML = Records inside the table.

---

# 6. Real-Time Scenario-Based Examples

Let's understand DDL and DML through a Student Management System.

### Scenario 1: Create a Student Database

```sql
CREATE DATABASE student_db;
```

### Scenario 2: Select the Database

```sql
USE student_db;
```

### Scenario 3: Create a Student Table

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(100),
    course VARCHAR(50),
    marks INT,
    city VARCHAR(50)
);
```

### Scenario 4: Insert Student Records

```sql
INSERT INTO students
(student_id, student_name, course, marks, city)
VALUES
(1, 'Prakash', 'SQL', 90, 'Hyderabad'),
(2, 'Rahul', 'Python', 85, 'Bangalore'),
(3, 'Anjali', 'Power BI', 95, 'Chennai'),
(4, 'Suresh', 'SQL', 75, 'Hyderabad');
```

### Scenario 5: Add a New Column

The college wants to store students' email addresses.

```sql
ALTER TABLE students
ADD email VARCHAR(100);
```

### Scenario 6: Update Student Marks

Prakash's marks are updated from 90 to 95.

```sql
UPDATE students
SET marks = 95
WHERE student_id = 1;
```

### Scenario 7: Update Student Course

Rahul changes his course from Python to SQL.

```sql
UPDATE students
SET course = 'SQL'
WHERE student_id = 2;
```

### Scenario 8: Delete a Student Record

The college wants to remove student ID 4.

```sql
DELETE FROM students
WHERE student_id = 4;
```

### Scenario 9: Remove All Student Records

The college wants to clear the student table but retain its structure.

```sql
TRUNCATE TABLE students;
```

### Scenario 10: Remove the Student Table

The college no longer requires the student table.

```sql
DROP TABLE students;
```

---

# 7. Important SQL Interview Questions

### Q1. What is DDL?

DDL stands for Data Definition Language. It is used to create and modify database structures such as tables and databases.

### Q2. What is DML?

DML stands for Data Manipulation Language. It is used to insert, update, and delete records in database tables.

### Q3. What is the difference between DELETE and TRUNCATE?

**DELETE:**
- Removes selected records using WHERE.
- Can delete all records if WHERE is omitted.
- Supports transaction rollback when used within a suitable transaction.

**TRUNCATE:**
- Removes all records from a table.
- Does not support WHERE.
- Resets AUTO_INCREMENT in MySQL.
- Causes an implicit commit in MySQL.

### Q4. What is the difference between DROP and TRUNCATE?

**DROP:**
Removes the complete table, including its structure and data.

**TRUNCATE:**
Removes all records but retains the table structure.

### Q5. What happens if we execute UPDATE without WHERE?

All records in the specified table will be updated.

### Q6. What happens if we execute DELETE without WHERE?

All records in the specified table will be deleted, but the table structure remains.

### Q7. Can we add a column to an existing table?

Yes. We can use ALTER TABLE with ADD.

```sql
ALTER TABLE employees
ADD age INT;
```

### Q8. Can we rename an existing table?

Yes. We can use RENAME TABLE.

```sql
RENAME TABLE employees TO staff;
```

### Q9. Which command is used to remove a particular record?

DELETE with a WHERE condition.

```sql
DELETE FROM employees
WHERE employee_id = 101;
```

### Q10. Can we roll back DDL commands in MySQL?

Most MySQL DDL statements cause an implicit commit, so they cannot normally be rolled back using ROLLBACK.

DML statements can be rolled back when executed within an appropriate transaction before COMMIT.

---

# 8. Best Practices

1. Always use WHERE conditions carefully with UPDATE and DELETE.
2. Take database backups before executing destructive operations.
3. Use meaningful database and table names.
4. Specify column names when using INSERT.
5. Choose appropriate data types for each column.
6. Use PRIMARY KEY to uniquely identify records.
7. Verify records before executing UPDATE or DELETE.
8. Use transactions when performing important data modifications.
9. Avoid executing DROP and TRUNCATE commands on production databases without proper authorization.
10. Test queries in a development environment before using them in production.

---

# 9. Conclusion

DDL and DML are two important categories of SQL commands used in relational database management.

**DDL (Data Definition Language)** is responsible for creating and modifying database structures.

**DML (Data Manipulation Language)** is responsible for inserting, updating, and deleting records.

Understanding these commands is essential for database development, data analytics, SQL interviews, and real-time projects.

### Quick Revision

| Command | Purpose |
|---|---|
| CREATE | Creates a new database or table |
| ALTER | Modifies an existing table structure |
| DROP | Removes a database or table |
| TRUNCATE | Removes all records but keeps table structure |
| RENAME | Changes the table name |
| INSERT | Adds new records |
| UPDATE | Modifies existing records |
| DELETE | Removes existing records |

**Happy Learning! 🚀**

*Practice SQL every day to improve your database skills.*

#SQL

# 📘 SQL – DQL Operations (Data Query Language)
## Complete Guide to SQL JOIN Operations

![SQL](https://img.shields.io/badge/SQL-Database-blue)
![Topic](https://img.shields.io/badge/Topic-DQL-green)
![Language](https://img.shields.io/badge/Language-SQL-orange)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Intermediate-brightgreen)

---

## 📌 1. Introduction to DQL

**DQL (Data Query Language)** is a category of SQL used to retrieve data from database tables.

It helps users fetch, filter, combine, and analyze information stored in databases.

The primary DQL command is:

- `SELECT`

One of the most important concepts in DQL is **JOIN**.

A JOIN is used to combine records from two or more tables based on a related column.

### Why do we use JOIN operations?

- To retrieve data from multiple tables.
- To establish relationships between tables.
- To combine related records.
- To identify matching and non-matching records.
- To analyze data from different departments.
- To generate business reports.

---

## 📌 2. Database and Table Creation

For this practical exercise, we use two tables:

1. EMPLOYEE_DETAILS
2. STUDENT_DETAILS

### Step 1: Select Database

```sql
USE AMEZON;
```

**Explanation:**

The `USE` statement selects the database in which SQL operations will be performed.

### Step 2: Create Employee Details Table

```sql
CREATE TABLE EMPLOYEE_DETAILS
(
    EMPID INT,
    EMPNAME CHAR(10),
    EMP_AGE INT,
    EMP_SALARY MONEY
);
```

**Explanation:**

| Column | Data Type | Description |
|---|---|---|
| EMPID | INT | Employee ID |
| EMPNAME | CHAR(10) | Employee name |
| EMP_AGE | INT | Employee age |
| EMP_SALARY | MONEY | Employee salary |

### Step 3: Create Student Details Table

```sql
CREATE TABLE STUDENT_DETAILS
(
    SUTID INT,
    STUNAME CHAR(10),
    STU_AGE INT,
    STU_STAIPEND MONEY
);
```

**Explanation:**

| Column | Data Type | Description |
|---|---|---|
| SUTID | INT | Student ID |
| STUNAME | CHAR(10) | Student name |
| STU_AGE | INT | Student age |
| STU_STAIPEND | MONEY | Student stipend |

---

## 📌 3. Insert Records into Tables

### Insert Employee Records

```sql
INSERT INTO EMPLOYEE_DETAILS
VALUES
(1, 'JHON', 21, 1200),
(2, 'STEVE', 25, 1500),
(3, 'BRAD', 30, 2000),
(4, 'HASSAN', 22, 3200),
(5, 'PETER', 35, 4200),
(6, 'WALTER', 29, 5000);
```

### Insert Student Records

```sql
INSERT INTO STUDENT_DETAILS
VALUES
(11, 'SAI', 22, 2000),
(12, 'VAMSHI', 25, 2500),
(13, 'MURARI', 30, 3000),
(1, 'JHON', 21, 1200),
(3, 'BRAD', 30, 2000),
(15, 'PRAKASH', 21, 4000);
```

### Step 4: Display Records

```sql
SELECT * FROM EMPLOYEE_DETAILS;

SELECT * FROM STUDENT_DETAILS;
```

**EMPLOYEE_DETAILS**

| EMPID | EMPNAME | EMP_AGE | EMP_SALARY |
|---|---|---|---|
| 1 | JHON | 21 | 1200 |
| 2 | STEVE | 25 | 1500 |
| 3 | BRAD | 30 | 2000 |
| 4 | HASSAN | 22 | 3200 |
| 5 | PETER | 35 | 4200 |
| 6 | WALTER | 29 | 5000 |

**STUDENT_DETAILS**

| SUTID | STUNAME | STU_AGE | STU_STAIPEND |
|---|---|---|---|
| 11 | SAI | 22 | 2000 |
| 12 | VAMSHI | 25 | 2500 |
| 13 | MURARI | 30 | 3000 |
| 1 | JHON | 21 | 1200 |
| 3 | BRAD | 30 | 2000 |
| 15 | PRAKASH | 21 | 4000 |

---

# 📌 4. Types of SQL JOIN Operations

The following JOIN operations are covered in this project:

1. INNER JOIN
2. LEFT OUTER JOIN
3. RIGHT OUTER JOIN
4. FULL OUTER JOIN
5. CROSS JOIN
6. EQUI JOIN
7. NON-EQUI JOIN

---

## 4.1 INNER JOIN

### Theory

INNER JOIN retrieves only the matching records from both tables based on a specified condition.

If a record does not have a matching value in the other table, it will not appear in the result.

**Syntax:**

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```

### SQL Query

```sql
SELECT *
FROM EMPLOYEE_DETAILS
INNER JOIN STUDENT_DETAILS
ON EMPLOYEE_DETAILS.EMPID = STUDENT_DETAILS.SUTID;
```

### Explanation

1. `SELECT *` retrieves all columns from both tables.
2. `FROM EMPLOYEE_DETAILS` specifies the first table.
3. `INNER JOIN STUDENT_DETAILS` combines the second table.
4. `ON` specifies the matching condition.
5. `EMPID = SUTID` matches employee IDs with student IDs.

### Expected Output

| EMPID | EMPNAME | EMP_AGE | EMP_SALARY | SUTID | STUNAME | STU_AGE | STU_STAIPEND |
|---|---|---|---|---|---|---|---|
| 1 | JHON | 21 | 1200 | 1 | JHON | 21 | 1200 |
| 3 | BRAD | 30 | 2000 | 3 | BRAD | 30 | 2000 |

**Result:** 2 matching records.

### Real-Time Scenario

Imagine a company maintains employee details and student internship details in separate tables.

The management wants to identify people whose IDs exist in both tables.

INNER JOIN retrieves only those matching records.

### Important Point

INNER JOIN returns only matching records from both tables.

---

## 4.2 LEFT OUTER JOIN

### Theory

LEFT OUTER JOIN returns all records from the left table and only matching records from the right table.

If a matching record does not exist in the right table, SQL returns NULL for the right table's columns.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT OUTER JOIN table2
ON table1.column_name = table2.column_name;
```

### SQL Query

```sql
SELECT *
FROM EMPLOYEE_DETAILS
LEFT OUTER JOIN STUDENT_DETAILS
ON EMPLOYEE_DETAILS.EMPID = STUDENT_DETAILS.SUTID;
```

### Expected Output

| EMPID | EMPNAME | SUTID | STUNAME |
|---|---|---|---|
| 1 | JHON | 1 | JHON |
| 2 | STEVE | NULL | NULL |
| 3 | BRAD | 3 | BRAD |
| 4 | HASSAN | NULL | NULL |
| 5 | PETER | NULL | NULL |
| 6 | WALTER | NULL | NULL |

*Other columns from the original tables are omitted here for readability.*

### Explanation

- All six employee records are displayed.
- JHON and BRAD have matching student records.
- The remaining employees have no matching student IDs.
- Therefore, student columns contain NULL for those employees.

### Real-Time Scenario

An HR department wants to display all employees, including employees who have not registered for an internal training program.

LEFT JOIN is useful because it keeps every employee record, even when no matching training record exists.

### Important Point

LEFT JOIN = All records from the left table + matching records from the right table.

---

## 4.3 RIGHT OUTER JOIN

### Theory

RIGHT OUTER JOIN returns all records from the right table and only matching records from the left table.

If no matching record exists in the left table, the left table columns contain NULL.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT OUTER JOIN table2
ON table1.column_name = table2.column_name;
```

### SQL Query

```sql
SELECT *
FROM EMPLOYEE_DETAILS
RIGHT OUTER JOIN STUDENT_DETAILS
ON EMPLOYEE_DETAILS.EMPID = STUDENT_DETAILS.SUTID;
```

### Expected Output

| EMPID | EMPNAME | SUTID | STUNAME |
|---|---|---|---|
| NULL | NULL | 11 | SAI |
| NULL | NULL | 12 | VAMSHI |
| NULL | NULL | 13 | MURARI |
| 1 | JHON | 1 | JHON |
| 3 | BRAD | 3 | BRAD |
| NULL | NULL | 15 | PRAKASH |

### Explanation

- All six student records are displayed.
- JHON and BRAD have matching employee records.
- SAI, VAMSHI, MURARI, and PRAKASH do not have matching employee IDs.
- Therefore, employee columns contain NULL for those records.

### Real-Time Scenario

A college wants to display all students, including students who have not yet been assigned an employee mentor.

RIGHT JOIN ensures that every student record appears in the result.

### Important Point

RIGHT JOIN = All records from the right table + matching records from the left table.

---

## 4.4 FULL OUTER JOIN

### Theory

FULL OUTER JOIN retrieves all records from both tables.

It includes:

- Matching records from both tables.
- Non-matching records from the left table.
- Non-matching records from the right table.

When a matching record does not exist, the corresponding columns contain NULL.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name;
```

### SQL Query

```sql
SELECT *
FROM EMPLOYEE_DETAILS
FULL OUTER JOIN STUDENT_DETAILS
ON EMPLOYEE_DETAILS.EMPID = STUDENT_DETAILS.SUTID;
```

### Expected Output

| EMPID | EMPNAME | SUTID | STUNAME |
|---|---|---|---|
| 1 | JHON | 1 | JHON |
| 2 | STEVE | NULL | NULL |
| 3 | BRAD | 3 | BRAD |
| 4 | HASSAN | NULL | NULL |
| 5 | PETER | NULL | NULL |
| 6 | WALTER | NULL | NULL |
| NULL | NULL | 11 | SAI |
| NULL | NULL | 12 | VAMSHI |
| NULL | NULL | 13 | MURARI |
| NULL | NULL | 15 | PRAKASH |

### Explanation

- Two records match between the tables.
- Four employee records have no matching student record.
- Four student records have no matching employee record.
- All ten records are included.

### Real-Time Scenario

A company wants to compare employee and student databases and identify all records, including matching and non-matching information.

FULL OUTER JOIN is useful for comparing two complete datasets.

### Important Point

FULL OUTER JOIN = All records from both tables, whether matching or not.

---

## 4.5 CROSS JOIN

### Theory

CROSS JOIN returns the Cartesian product of two tables.

It combines every record from the first table with every record from the second table.

There is no ON condition in CROSS JOIN.

**Syntax:**

```sql
SELECT *
FROM table1
CROSS JOIN table2;
```

### SQL Query

```sql
SELECT *
FROM EMPLOYEE_DETAILS
CROSS JOIN STUDENT_DETAILS;
```

### Expected Output Information

The employee table contains 6 records.

The student table contains 6 records.

Therefore:

```text
Total Records = 6 × 6

Total Records = 36
```

### Explanation

Each employee record is combined with every student record.

For example:

| EMPNAME | STUNAME |
|---|---|
| JHON | SAI |
| JHON | VAMSHI |
| JHON | MURARI |
| JHON | JHON |
| JHON | BRAD |
| JHON | PRAKASH |
| STEVE | SAI |
| STEVE | VAMSHI |

The combinations continue until all 36 records are generated.

### Real-Time Scenario

An organization wants to generate every possible combination of employees and available training courses.

CROSS JOIN can generate these combinations.

### Important Point

CROSS JOIN = Number of rows in Table 1 × Number of rows in Table 2.

---

## 4.6 EQUI JOIN

### Theory

EQUI JOIN is used to retrieve records from two tables by applying an equality condition between columns.

It uses the `=` operator to compare related column values.

EQUI JOIN is commonly written using the traditional comma-separated table syntax with a WHERE condition.

**Syntax:**

```sql
SELECT columns
FROM table1, table2
WHERE table1.column_name = table2.column_name;
```

### SQL Query

```sql
SELECT *
FROM EMPLOYEE_DETAILS, STUDENT_DETAILS
WHERE EMPLOYEE_DETAILS.EMPID = STUDENT_DETAILS.SUTID;
```

### Expected Output

| EMPID | EMPNAME | SUTID | STUNAME |
|---|---|---|---|
| 1 | JHON | 1 | JHON |
| 3 | BRAD | 3 | BRAD |

### Explanation

1. Both tables are specified using the FROM clause.
2. The WHERE clause compares EMPID and SUTID.
3. The equality operator identifies matching values.
4. Only matching records are returned.

### Real-Time Scenario

A company wants to retrieve employees whose IDs match student registration IDs.

EQUI JOIN helps retrieve matching records using an equality condition.

### Important Point

EQUI JOIN uses the equality operator (=).

**Note:** This query produces the same matching rows as an INNER JOIN with the same equality condition.

---

## 4.7 NON-EQUI JOIN

### Theory

NON-EQUI JOIN combines records from two tables using comparison operators other than the equality operator.

It can use operators such as:

- Greater than (>)
- Less than (<)
- Greater than or equal to (>=)
- Less than or equal to (<=)
- BETWEEN

Unlike EQUI JOIN, it does not require equal values between the joining columns.

**Syntax:**

```sql
SELECT columns
FROM table1, table2
WHERE table1.column_name operator table2.column_name;
```

### SQL Query

```sql
SELECT *
FROM EMPLOYEE_DETAILS, STUDENT_DETAILS
WHERE EMPLOYEE_DETAILS.EMPID > STUDENT_DETAILS.SUTID;
```

### Explanation

The query compares employee IDs with student IDs.

It returns records where:

```text
EMPID > SUTID
```

For example:

- Employee ID 2 is greater than Student ID 1.
- Employee ID 3 is greater than Student ID 1.
- Employee ID 4 is greater than Student ID 1 and 3.
- Employee ID 5 is greater than Student ID 1 and 3.
- Employee ID 6 is greater than Student ID 1 and 3.

### Expected Output Information

The query returns 8 combinations.

| EMPID | EMPNAME | SUTID | STUNAME |
|---|---|---|---|
| 2 | STEVE | 1 | JHON |
| 3 | BRAD | 1 | JHON |
| 4 | HASSAN | 1 | JHON |
| 5 | PETER | 1 | JHON |
| 6 | WALTER | 1 | JHON |
| 4 | HASSAN | 3 | BRAD |
| 5 | PETER | 3 | BRAD |
| 6 | WALTER | 3 | BRAD |

### Real-Time Scenario

Suppose a company wants to compare employee salary ranges with predefined salary grades.

A NON-EQUI JOIN can be used to match salary values against ranges using greater-than, less-than, or BETWEEN conditions.

### Important Point

NON-EQUI JOIN uses comparison operators other than equality (=).

---

# 📌 5. Difference Between All JOIN Operations

| JOIN Type | Description | Matching Records | Non-Matching Records |
|---|---|---|---|
| INNER JOIN | Returns matching records | Yes | No |
| LEFT JOIN | All left records and matching right records | Yes | Left table retained |
| RIGHT JOIN | All right records and matching left records | Yes | Right table retained |
| FULL OUTER JOIN | All records from both tables | Yes | Yes |
| CROSS JOIN | Cartesian product | No matching condition required | All combinations |
| EQUI JOIN | Joins using equality | Yes | No |
| NON-EQUI JOIN | Joins using inequality/comparison | Based on comparison | Depends on condition |

---

# 📌 6. Important Differences Between JOIN Operations

### INNER JOIN vs LEFT JOIN

| INNER JOIN | LEFT JOIN |
|---|---|
| Returns only matching records | Returns all left table records |
| Excludes unmatched left records | Includes unmatched left records |
| Excludes unmatched right records | Includes matching right records |
| Uses ON condition | Uses ON condition |

### LEFT JOIN vs RIGHT JOIN

| LEFT JOIN | RIGHT JOIN |
|---|---|
| Preserves all left table records | Preserves all right table records |
| Unmatched right values become NULL | Unmatched left values become NULL |

### INNER JOIN vs FULL OUTER JOIN

| INNER JOIN | FULL OUTER JOIN |
|---|---|
| Only matching records | Matching and non-matching records |
| Excludes unmatched rows | Includes unmatched rows |
| Smaller result in this example | Returns all 10 records |

### EQUI JOIN vs NON-EQUI JOIN

| EQUI JOIN | NON-EQUI JOIN |
|---|---|
| Uses equality (=) | Uses comparison operators |
| Matches equal values | Matches based on a comparison condition |
| Example: EMPID = SUTID | Example: EMPID > SUTID |

---

# 📌 7. Important SQL JOIN Interview Questions

### Q1. What is a JOIN in SQL?

A JOIN is used to combine records from two or more tables based on a related column.

### Q2. How many types of JOIN operations are commonly used?

The commonly discussed types include:

1. INNER JOIN
2. LEFT JOIN
3. RIGHT JOIN
4. FULL OUTER JOIN
5. CROSS JOIN
6. SELF JOIN

EQUI JOIN and NON-EQUI JOIN describe joining conditions.

### Q3. What is the difference between INNER JOIN and OUTER JOIN?

INNER JOIN returns only matching records, whereas OUTER JOIN can also return non-matching records from one or both tables.

### Q4. What is a Cartesian product?

A Cartesian product combines every record from the first table with every record from the second table.

### Q5. Which JOIN returns all records from both tables?

FULL OUTER JOIN.

### Q6. Which JOIN returns all records from the left table?

LEFT OUTER JOIN.

### Q7. Which JOIN returns all records from the right table?

RIGHT OUTER JOIN.

### Q8. What is the difference between EQUI JOIN and NON-EQUI JOIN?

EQUI JOIN uses the equality operator, whereas NON-EQUI JOIN uses comparison operators such as >, <, >=, <=, or BETWEEN.

### Q9. Can we join two tables without a common column?

Yes. CROSS JOIN does not require a common column. Other JOIN operations can also use suitable conditions between columns.

### Q10. What is the difference between JOIN and UNION?

JOIN combines columns from related tables into one result, whereas UNION combines rows from SELECT query results.

---

# 📌 8. Practical SQL JOIN Exercises

Use the EMPLOYEE_DETAILS and STUDENT_DETAILS tables to solve the following questions.

### Beginner Level

1. Display all employee records using SELECT.
2. Display all student records using SELECT.
3. Retrieve matching records using INNER JOIN.
4. Retrieve all employee records using LEFT JOIN.
5. Retrieve all student records using RIGHT JOIN.

### Intermediate Level

6. Display all matching and non-matching records using FULL OUTER JOIN.
7. Generate all possible combinations using CROSS JOIN.
8. Retrieve matching IDs using EQUI JOIN.
9. Retrieve records where EMPID is greater than SUTID using NON-EQUI JOIN.
10. Display only employee names and student names using INNER JOIN.

### Advanced Level

11. Find employees who do not have matching student records.
12. Find students who do not have matching employee records.
13. Find records that match in both tables.
14. Compare the results of INNER JOIN and FULL OUTER JOIN.
15. Calculate the number of records returned by each JOIN operation.

---

# 📌 9. Important Practical Notes

1. SQL JOIN operations are useful for retrieving related information from multiple tables.
2. The ON clause specifies the joining condition in explicit JOIN syntax.
3. The WHERE clause can be used for filtering records and for writing traditional EQUI JOIN and NON-EQUI JOIN queries.
4. NULL values appear when an outer JOIN has no matching record on one side.
5. CROSS JOIN generates a Cartesian product.
6. EQUI JOIN uses an equality condition.
7. NON-EQUI JOIN uses a comparison condition.
8. INNER JOIN and EQUI JOIN can produce the same results when they use the same equality condition.
9. JOIN results can contain duplicate-looking rows if the joining columns have multiple matching records.
10. Always check the joining columns and their relationships before writing a JOIN query.

---

# 📌 10. Conclusion

DQL is an important part of SQL because it allows users to retrieve and analyze information stored in databases.

JOIN operations are especially important when working with multiple related tables.

By understanding INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN, CROSS JOIN, EQUI JOIN, and NON-EQUI JOIN, developers and data analysts can retrieve meaningful information from different datasets.

These concepts are widely used in:

- SQL Development
- Data Analysis
- Database Management
- Business Intelligence
- Data Engineering
- Reporting and Data Visualization

**Learning SQL JOIN operations is an essential step toward becoming a SQL Developer or Data Analyst.**

---

# 📚 11. Learning Resources

- [Microsoft SQL Server Documentation](https://learn.microsoft.com/en-us/sql/)
- [W3Schools SQL JOIN Tutorial](https://www.w3schools.com/sql/sql_join.asp)
- [SQLBolt Interactive Lessons](https://sqlbolt.com/)
- [HackerRank SQL Practice](https://www.hackerrank.com/domains/sql)
- [LeetCode Database Problems](https://leetcode.com/problemset/database/)

---

⭐ If you find this SQL JOIN guide useful, consider giving this repository a star!

**Author:** Prakash

**Technology:** SQL Server

**Topic:** DQL – Data Query Language

**Subtopic:** SQL JOIN Operations

#SQL

# MySQL – AUTO_INCREMENT and SET Operations

## 📌 Table of Contents

1. Introduction
2. AUTO_INCREMENT
   - Definition
   - Purpose
   - Syntax
   - Rules and Characteristics
   - Practical Examples
   - Scenario-Based Examples
   - Resetting AUTO_INCREMENT
   - Advantages
3. SET Operations
   - Definition
   - Purpose
   - Types of SET Operations
   - UNION
   - UNION ALL
   - INTERSECT
   - EXCEPT
   - Syntax and Examples
   - Scenario-Based Examples
4. Difference Between AUTO_INCREMENT and SET Operations
5. Interview Questions
6. Conclusion

---

# 1. Introduction

MySQL provides different features to manage database records efficiently.

Two useful concepts are:

- **AUTO_INCREMENT:** Automatically generates unique numeric values for a column when new records are inserted.
- **SET Operations:** Combine or compare the results of multiple SELECT queries.

These concepts help developers manage primary keys and retrieve data from multiple queries.

---

# 2. AUTO_INCREMENT

## 2.1 What is AUTO_INCREMENT?

AUTO_INCREMENT is a MySQL attribute used to automatically generate sequential numeric values for a column whenever a new record is inserted.

It is commonly used with the PRIMARY KEY column to uniquely identify each record in a table.

Instead of manually entering ID values, MySQL automatically generates them.

### Example:

Consider an Employee table:

| Employee_ID | Employee_Name | Salary |
|---|---|---|
| 1 | Ravi | 25000 |
| 2 | Kumar | 30000 |
| 3 | Prakash | 35000 |
| 4 | Arun | 28000 |

Here, Employee_ID is automatically generated by MySQL.

## 2.2 Why do we use AUTO_INCREMENT?

1. Automatically generates unique numeric identifiers.
2. Reduces manual data entry.
3. Avoids duplicate ID values when used with PRIMARY KEY.
4. Makes record identification easier.
5. Useful for employee IDs, customer IDs, product IDs, and order IDs.

## 2.3 Syntax of AUTO_INCREMENT

```sql
CREATE TABLE table_name (
    column_name INT AUTO_INCREMENT PRIMARY KEY,
    column2 datatype,
    column3 datatype
);
```

### Explanation:

- `CREATE TABLE`: Creates a new table.
- `column_name`: Name of the auto-increment column.
- `INT`: Specifies the integer datatype.
- `AUTO_INCREMENT`: Automatically generates the next numeric value.
- `PRIMARY KEY`: Ensures that the column contains unique, non-NULL values.

## 2.4 Practical Example – Creating an Employee Table

```sql
CREATE TABLE Employee (
    Employee_ID INT AUTO_INCREMENT PRIMARY KEY,
    Employee_Name VARCHAR(50),
    Department VARCHAR(30),
    Salary INT
);
```

### Inserting Records

```sql
INSERT INTO Employee
(Employee_Name, Department, Salary)
VALUES
('Ravi', 'IT', 25000),
('Kumar', 'HR', 30000),
('Prakash', 'Finance', 35000),
('Arun', 'IT', 28000);
```

### Displaying Records

```sql
SELECT * FROM Employee;
```

### Output

| Employee_ID | Employee_Name | Department | Salary |
|---|---|---|---|
| 1 | Ravi | IT | 25000 |
| 2 | Kumar | HR | 30000 |
| 3 | Prakash | Finance | 35000 |
| 4 | Arun | IT | 28000 |

**Observation:** We did not insert Employee_ID values manually. MySQL generated them automatically.

---

## 2.5 Inserting Data with AUTO_INCREMENT

There are different ways to insert records into an AUTO_INCREMENT table.

### Method 1: Insert without specifying the ID

```sql
INSERT INTO Employee
(Employee_Name, Department, Salary)
VALUES
('Suresh', 'Marketing', 32000);
```

MySQL automatically generates the Employee_ID.

### Method 2: Insert multiple records

```sql
INSERT INTO Employee
(Employee_Name, Department, Salary)
VALUES
('Raj', 'IT', 40000),
('Anil', 'HR', 35000),
('Manoj', 'Finance', 45000);
```

MySQL generates a separate ID for each inserted row.

### Method 3: Insert an explicit ID

```sql
INSERT INTO Employee
(Employee_ID, Employee_Name, Department, Salary)
VALUES
(10, 'Vijay', 'IT', 50000);
```

**Explanation:** MySQL allows an explicit ID to be inserted. If the inserted value is greater than the current AUTO_INCREMENT value, the next generated value will normally be greater than that value.

---

## 2.6 AUTO_INCREMENT Rules and Characteristics

1. AUTO_INCREMENT is generally used with integer columns.
2. A table can have only one AUTO_INCREMENT column.
3. The AUTO_INCREMENT column must be indexed.
4. It is commonly combined with PRIMARY KEY.
5. MySQL automatically generates values when the column is omitted or assigned NULL.
6. AUTO_INCREMENT values are not guaranteed to be consecutive.
7. Deleted IDs are generally not reused automatically.
8. You can specify a starting value while creating a table.

### Example – Starting AUTO_INCREMENT from 100

```sql
CREATE TABLE Products (
    Product_ID INT AUTO_INCREMENT PRIMARY KEY,
    Product_Name VARCHAR(50),
    Price INT
) AUTO_INCREMENT = 100;
```

### Insert Data

```sql
INSERT INTO Products (Product_Name, Price)
VALUES ('Laptop', 50000);
```

### Output

| Product_ID | Product_Name | Price |
|---|---|---|
| 100 | Laptop | 50000 |

---

## 2.7 How to Change AUTO_INCREMENT Value

You can change the next AUTO_INCREMENT value using ALTER TABLE.

### Syntax

```sql
ALTER TABLE table_name
AUTO_INCREMENT = value;
```

### Example

```sql
ALTER TABLE Employee
AUTO_INCREMENT = 50;
```

**Explanation:** If the next available AUTO_INCREMENT value is lower than 50, MySQL will use 50 for the next generated value. MySQL does not lower the counter below the value required by existing rows.

---

## 2.8 How to Check AUTO_INCREMENT Value

```sql
SHOW TABLE STATUS LIKE 'Employee';
```

This command displays table information, including the next AUTO_INCREMENT value in the `Auto_increment` field.

You can also use:

```sql
SELECT AUTO_INCREMENT
FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_SCHEMA = DATABASE()
AND TABLE_NAME = 'Employee';
```

---

## 2.9 Resetting AUTO_INCREMENT

You can reset the next AUTO_INCREMENT value after deleting records.

### Example 1: Using ALTER TABLE

```sql
ALTER TABLE Employee
AUTO_INCREMENT = 1;
```

**Note:** If records already exist, MySQL will not generate an ID lower than the value required by the existing maximum ID.

### Example 2: Using TRUNCATE

```sql
TRUNCATE TABLE Employee;
```

TRUNCATE removes all records and resets the AUTO_INCREMENT counter to its initial value.

**Important:** TRUNCATE is a DDL statement in MySQL and cannot generally be rolled back like a regular transactional DELETE.

---

## 2.10 Scenario-Based Examples of AUTO_INCREMENT

### Scenario 1: Employee Management System

**Requirement:** A company wants to assign a unique employee ID automatically whenever a new employee joins.

```sql
CREATE TABLE Employees (
    Emp_ID INT AUTO_INCREMENT PRIMARY KEY,
    Emp_Name VARCHAR(50),
    Department VARCHAR(30),
    Salary INT
);
```

Insert:

```sql
INSERT INTO Employees
(Emp_Name, Department, Salary)
VALUES
('Ramesh', 'IT', 30000),
('Suresh', 'HR', 25000),
('Prakash', 'Finance', 40000);
```

**Result:** Employee IDs are generated automatically.

### Scenario 2: Online Shopping System

**Requirement:** An e-commerce company wants to generate a unique order ID for every customer order.

```sql
CREATE TABLE Orders (
    Order_ID INT AUTO_INCREMENT PRIMARY KEY,
    Customer_Name VARCHAR(50),
    Product_Name VARCHAR(50),
    Amount INT
);
```

Insert:

```sql
INSERT INTO Orders
(Customer_Name, Product_Name, Amount)
VALUES
('Ravi', 'Laptop', 55000),
('Kumar', 'Mobile', 20000);
```

**Result:** Every order receives a unique automatically generated Order_ID.

### Scenario 3: Student Management System

**Requirement:** A college wants to generate student registration numbers automatically.

```sql
CREATE TABLE Students (
    Student_ID INT AUTO_INCREMENT PRIMARY KEY,
    Student_Name VARCHAR(50),
    Course VARCHAR(30)
);
```

Insert:

```sql
INSERT INTO Students
(Student_Name, Course)
VALUES
('Arun', 'CSE'),
('Ravi', 'ECE'),
('Kiran', 'IT');
```

**Result:** Every student receives an automatically generated ID.

---

# 3. SET OPERATIONS

## 3.1 What are SET Operations?

SET Operations are used to combine or compare the results of two or more SELECT statements.

They help retrieve data from multiple queries and produce a single result set.

SET operations are useful when data is stored in different tables but needs to be combined or compared.

### Types of SET Operations

1. UNION
2. UNION ALL
3. INTERSECT
4. EXCEPT

**Note:** MySQL supports UNION and UNION ALL directly. INTERSECT and EXCEPT are supported in MySQL 8.0.31 and later versions.

---

# 4. UNION

## 4.1 What is UNION?

UNION combines the results of two or more SELECT statements and removes duplicate records.

It returns only distinct rows in the final result.

### Syntax

```sql
SELECT column_name FROM table1
UNION
SELECT column_name FROM table2;
```

### Example

Consider two tables:

**Table 1 – Students**

| Student_Name |
|---|
| Ravi |
| Kumar |
| Prakash |

**Table 2 – Employees**

| Employee_Name |
|---|
| Ravi |
| Arun |
| Suresh |

### Query

```sql
SELECT Student_Name AS Name
FROM Students

UNION

SELECT Employee_Name AS Name
FROM Employees;
```

### Output

| Name |
|---|
| Arun |
| Kumar |
| Prakash |
| Ravi |
| Suresh |

**Explanation:** Ravi appears in both tables, but UNION returns it only once.

### Important Points

1. UNION removes duplicate rows.
2. Both SELECT statements must return the same number of columns.
3. Corresponding columns must have compatible data types.
4. Column names in the final output are generally taken from the first SELECT statement.
5. ORDER BY is applied to the combined result and is normally placed at the end.

---

# 5. UNION ALL

## 5.1 What is UNION ALL?

UNION ALL combines the results of two or more SELECT statements without removing duplicate records.

It returns all rows, including duplicates.

### Syntax

```sql
SELECT column_name FROM table1
UNION ALL
SELECT column_name FROM table2;
```

### Example

```sql
SELECT Student_Name AS Name
FROM Students

UNION ALL

SELECT Employee_Name AS Name
FROM Employees;
```

### Output

| Name |
|---|
| Ravi |
| Kumar |
| Prakash |
| Ravi |
| Arun |
| Suresh |

**Explanation:** Ravi appears twice because UNION ALL does not remove duplicate records.

### Important Points

1. UNION ALL includes duplicate records.
2. It is generally faster than UNION because it does not perform duplicate elimination.
3. Both SELECT statements must return the same number of columns.
4. Corresponding columns must have compatible data types.

---

# 6. INTERSECT

## 6.1 What is INTERSECT?

INTERSECT returns only the common records that exist in the result sets of both SELECT statements.

It is used to identify matching data between two tables or query results.

### Syntax

```sql
SELECT column_name FROM table1
INTERSECT
SELECT column_name FROM table2;
```

### Example

```sql
SELECT Student_Name AS Name
FROM Students

INTERSECT

SELECT Employee_Name AS Name
FROM Employees;
```

### Output

| Name |
|---|
| Ravi |

**Explanation:** Ravi exists in both Students and Employees tables, so INTERSECT returns Ravi.

### Important Points

1. Returns only common records.
2. Removes duplicate rows from the result.
3. Both SELECT statements must return the same number of columns.
4. Corresponding columns must have compatible data types.
5. Supported in MySQL 8.0.31 and later.

### Alternative for Older MySQL Versions

You can use INNER JOIN or EXISTS to identify common records.

```sql
SELECT DISTINCT s.Student_Name
FROM Students s
INNER JOIN Employees e
ON s.Student_Name = e.Employee_Name;
```

---

# 7. EXCEPT

## 7.1 What is EXCEPT?

EXCEPT returns records from the first SELECT statement that do not exist in the result of the second SELECT statement.

It is used to identify records that are available in one table but missing from another.

### Syntax

```sql
SELECT column_name FROM table1
EXCEPT
SELECT column_name FROM table2;
```

### Example

```sql
SELECT Student_Name AS Name
FROM Students

EXCEPT

SELECT Employee_Name AS Name
FROM Employees;
```

### Output

| Name |
|---|
| Kumar |
| Prakash |

**Explanation:** Kumar and Prakash exist in the Students table but do not exist in the Employees table.

### Important Points

1. Returns records from the first query only.
2. Excludes matching records from the second query.
3. Removes duplicate rows from the result.
4. Both SELECT statements must return the same number of columns.
5. Supported in MySQL 8.0.31 and later.

### Alternative for Older MySQL Versions

```sql
SELECT DISTINCT s.Student_Name
FROM Students s
WHERE NOT EXISTS (
    SELECT 1
    FROM Employees e
    WHERE e.Employee_Name = s.Student_Name
);
```

---

# 8. Difference Between UNION, UNION ALL, INTERSECT, and EXCEPT

| Operation | Description | Duplicate Handling |
|---|---|---|
| UNION | Combines results | Removes duplicates |
| UNION ALL | Combines results | Keeps duplicates |
| INTERSECT | Returns common records | Removes duplicates |
| EXCEPT | Returns records from first query that are absent in second | Removes duplicates |

### Simple Example

Table A:

| Value |
|---|
| 10 |
| 20 |
| 30 |

Table B:

| Value |
|---|
| 20 |
| 30 |
| 40 |

| Operation | Result |
|---|---|
| UNION | 10, 20, 30, 40 |
| UNION ALL | 10, 20, 30, 20, 30, 40 |
| INTERSECT | 20, 30 |
| EXCEPT (A EXCEPT B) | 10 |

---

# 9. Scenario-Based Examples of SET Operations

## Scenario 1: Student and Employee Database

**Requirement:** An organization wants to identify all people who are registered as either students or employees.

```sql
SELECT Student_Name AS Person_Name
FROM Students

UNION

SELECT Employee_Name AS Person_Name
FROM Employees;
```

**Operation Used:** UNION

**Reason:** Combines both tables and removes duplicate names.

## Scenario 2: Customer Purchase Analysis

**Requirement:** A company wants to find all customers who purchased products from either its online store or offline store, including repeated customer names.

```sql
SELECT Customer_Name
FROM Online_Sales

UNION ALL

SELECT Customer_Name
FROM Offline_Sales;
```

**Operation Used:** UNION ALL

**Reason:** Includes every matching row without removing duplicates.

## Scenario 3: Common Customers

**Requirement:** A company wants to identify customers who purchased products from both online and offline stores.

```sql
SELECT Customer_Name
FROM Online_Sales

INTERSECT

SELECT Customer_Name
FROM Offline_Sales;
```

**Operation Used:** INTERSECT

**Reason:** Returns customers who appear in both result sets.

## Scenario 4: Inactive Customers

**Requirement:** A company wants to identify customers who purchased products from the online store but never purchased from the offline store.

```sql
SELECT Customer_Name
FROM Online_Sales

EXCEPT

SELECT Customer_Name
FROM Offline_Sales;
```

**Operation Used:** EXCEPT

**Reason:** Returns customers who exist in the first result but not in the second.

---

# 10. Important Rules for SET Operations

1. Every SELECT statement must return the same number of columns.
2. Corresponding columns must have compatible data types.
3. Column order must match between SELECT statements.
4. UNION removes duplicates.
5. UNION ALL keeps duplicates.
6. INTERSECT returns common records.
7. EXCEPT returns records available only in the first result.
8. ORDER BY should be placed at the end of the combined query.
9. Individual SELECT statements can use WHERE conditions.
10. Use parentheses when grouping complex set operations to make the intended order clear.

### Example – Using ORDER BY with UNION

```sql
SELECT Student_Name AS Name
FROM Students

UNION

SELECT Employee_Name AS Name
FROM Employees

ORDER BY Name ASC;
```

### Example – Using WHERE with UNION

```sql
SELECT Employee_Name AS Name
FROM Employees
WHERE Department = 'IT'

UNION

SELECT Student_Name AS Name
FROM Students
WHERE Course = 'CSE';
```

---

# 11. AUTO_INCREMENT vs SET Operations

| AUTO_INCREMENT | SET Operations |
|---|---|
| Automatically generates numeric values | Combines or compares query results |
| Used during table creation and record insertion | Used with SELECT statements |
| Helps create unique identifiers | Helps retrieve related data |
| Commonly used with PRIMARY KEY | Uses UNION, UNION ALL, INTERSECT, EXCEPT |
| Used in table structure and data management | Used in querying and data analysis |

---

# 12. SQL Interview Questions and Answers

### Q1. What is AUTO_INCREMENT in MySQL?

**Answer:** AUTO_INCREMENT is an attribute that automatically generates sequential numeric values for a column when a new record is inserted.

### Q2. Can we use AUTO_INCREMENT without PRIMARY KEY?

**Answer:** Yes. MySQL allows AUTO_INCREMENT on a column with an appropriate index, such as a UNIQUE index. However, it is commonly used with PRIMARY KEY.

### Q3. Can a table have multiple AUTO_INCREMENT columns?

**Answer:** No. A MySQL table can have only one AUTO_INCREMENT column.

### Q4. What happens if we delete a record with AUTO_INCREMENT?

**Answer:** MySQL generally does not reuse the deleted ID automatically. The next generated value continues according to the AUTO_INCREMENT counter.

### Q5. What is the difference between UNION and UNION ALL?

**Answer:** UNION removes duplicate records, whereas UNION ALL includes duplicate records.

### Q6. What is INTERSECT?

**Answer:** INTERSECT returns common records from two SELECT statements.

### Q7. What is EXCEPT?

**Answer:** EXCEPT returns records from the first SELECT statement that are not present in the second SELECT statement.

### Q8. Does MySQL support INTERSECT and EXCEPT?

**Answer:** Yes. MySQL supports both from version 8.0.31 onwards.

### Q9. Which is faster: UNION or UNION ALL?

**Answer:** UNION ALL is generally faster because it does not need to remove duplicate records.

### Q10. Can we use ORDER BY with UNION?

**Answer:** Yes. ORDER BY can be used at the end of the combined query to sort the final result.

---

# 13. Practical SQL Syntax Cheat Sheet

| Operation | Syntax |
|---|---|
| AUTO_INCREMENT | `column_name INT AUTO_INCREMENT PRIMARY KEY` |
| Set Starting Value | `CREATE TABLE ... AUTO_INCREMENT = 100` |
| Alter AUTO_INCREMENT | `ALTER TABLE table_name AUTO_INCREMENT = 100` |
| Check AUTO_INCREMENT | `SHOW TABLE STATUS LIKE 'table_name'` |
| UNION | `SELECT ... UNION SELECT ...` |
| UNION ALL | `SELECT ... UNION ALL SELECT ...` |
| INTERSECT | `SELECT ... INTERSECT SELECT ...` |
| EXCEPT | `SELECT ... EXCEPT SELECT ...` |

---

# 14. Conclusion

AUTO_INCREMENT and SET Operations are important concepts in MySQL.

**AUTO_INCREMENT** simplifies database management by automatically generating numeric identifiers for records.

**SET Operations** help combine and compare the results of multiple SELECT statements.

Understanding these concepts is useful for:

- Database management.
- Real-time SQL projects.
- Data analysis.
- SQL interviews.
- Software development.

Learning these concepts with practical examples helps build strong SQL fundamentals.

---

**Technologies Used:** MySQL  
**Topics Covered:** AUTO_INCREMENT, UNION, UNION ALL, INTERSECT, EXCEPT  
**Level:** Beginner to Intermediate
