# SQL Complete Technical Interview Preparation

A beginner-friendly guide to SQL topics, with definitions, syntax,
examples, and interview points.

> **Database note:** Examples use broadly supported SQL. Some syntax
> differs between PostgreSQL, MySQL, SQL Server, and SQLite.
> PostgreSQL-specific notes are labelled where useful.

## Table of Contents

1.  [SQL Fundamentals](#1-sql-fundamentals)
2.  [SQL Command Categories](#2-sql-command-categories)
3.  [Filtering and Sorting](#3-filtering-and-sorting)
4.  [SQL Functions](#4-sql-functions)
5.  [Aggregate Functions, GROUP BY, and
    HAVING](#5-aggregate-functions-group-by-and-having)
6.  [Joins](#6-joins)
7.  [Subqueries](#7-subqueries)
8.  [Common Table Expressions (CTEs)](#8-common-table-expressions-ctes)
9.  [Database Normalization](#9-database-normalization)
10. [Keys and Constraints](#10-keys-and-constraints)
11. [Transactions and ACID](#11-transactions-and-acid)
12. [Indexes and Views](#12-indexes-and-views)
13. [Window Functions](#13-window-functions)
14. [Database Design and
    Relationships](#14-database-design-and-relationships)
15. [Stored Procedures, Functions, and
    Triggers](#15-stored-procedures-functions-and-triggers)
16. [Query Execution and
    Optimization](#16-query-execution-and-optimization)
17. [Common Interview Comparisons](#17-common-interview-comparisons)
18. [Practice Questions](#18-practice-questions)

------------------------------------------------------------------------

## 1. SQL Fundamentals

### What is SQL?

**SQL (Structured Query Language)** is a language used to communicate
with relational databases. We use it to create tables, insert data, read
data, update records, delete records, and control access.

Example:

``` sql
SELECT name, age
FROM students;
```

This query returns the `name` and `age` columns from the `students`
table.

### What is a database?

A database is an organized collection of data that can be stored,
accessed, and managed electronically.

Examples include a college database, banking database, and shopping
website database.

### DBMS and RDBMS

-   **DBMS (Database Management System):** Software used to store and
    manage data.
-   **RDBMS (Relational Database Management System):** A type of DBMS
    that stores data in related tables, usually using keys.

Examples of relational database systems include PostgreSQL, MySQL,
Oracle Database, and Microsoft SQL Server.

### SQL, MySQL, and PostgreSQL

-   **SQL** is the language.
-   **MySQL** is a relational database management system.
-   **PostgreSQL** is an open-source relational database management
    system.

### Tables, rows, and columns

A table stores related data.

    student_id name     age
  ------------ ------ -----
             1 Ravi      20
             2 Sita      21

-   **Table:** `students`
-   **Row / record:** One student's complete information.
-   **Column / field:** One attribute, such as `name` or `age`.

### Common SQL data types

  Data type           Purpose                                 Example
  ------------------- --------------------------------------- -------------------------
  `INT` / `INTEGER`   Whole numbers                           `25`
  `DECIMAL(p,s)`      Exact decimal values                    `1250.50`
  `NUMERIC(p,s)`      Exact numeric values                    `99.99`
  `VARCHAR(n)`        Variable-length text                    `'Siva'`
  `CHAR(n)`           Fixed-length text                       `'A'`
  `TEXT`              Longer text (database support varies)   `'Description'`
  `DATE`              Calendar date                           `'2026-11-12'`
  `TIME`              Time of day                             `'10:30:00'`
  `TIMESTAMP`         Date and time                           `'2026-11-12 10:30:00'`
  `BOOLEAN`           True/false value                        `TRUE`

### NULL

`NULL` represents a missing or unknown value. It is not the same as zero
or an empty string.

Use `IS NULL` or `IS NOT NULL` to test it:

``` sql
SELECT *
FROM students
WHERE phone_number IS NULL;
```

------------------------------------------------------------------------

## 2. SQL Command Categories

SQL commands are commonly grouped into five categories.

### DDL -- Data Definition Language

DDL defines or changes database structures.

-   `CREATE` -- creates a database object.
-   `ALTER` -- changes an existing object's structure.
-   `DROP` -- removes an object.
-   `TRUNCATE` -- removes all rows from a table while keeping its
    structure.

Examples:

``` sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

ALTER TABLE students
ADD email VARCHAR(150);

TRUNCATE TABLE students;

DROP TABLE students;
```

**Remember:** `TRUNCATE` keeps the table; `DROP` removes the table
itself. Transaction and identity-reset behaviour can vary by database.

### DML -- Data Manipulation Language

DML changes table data.

``` sql
INSERT INTO students (student_id, name, age)
VALUES (1, 'Siva', 22);

UPDATE students
SET age = 23
WHERE student_id = 1;

DELETE FROM students
WHERE student_id = 1;
```

Always use a suitable `WHERE` condition with `UPDATE` and `DELETE` when
you intend to affect only selected rows.

### DQL -- Data Query Language

`SELECT` retrieves data.

``` sql
SELECT name, age
FROM students;
```

### DCL -- Data Control Language

DCL manages database permissions.

-   `GRANT` gives privileges.
-   `REVOKE` removes privileges.

Example (exact privileges and syntax depend on the database):

``` sql
GRANT SELECT ON students TO analyst;
REVOKE SELECT ON students FROM analyst;
```

### TCL -- Transaction Control Language

TCL manages transactions.

-   `BEGIN` / `START TRANSACTION` -- starts a transaction.
-   `COMMIT` -- saves the transaction.
-   `ROLLBACK` -- cancels uncommitted changes.
-   `SAVEPOINT` -- creates a point to which a transaction can roll back.

``` sql
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 500
WHERE account_id = 2;

COMMIT;
```

------------------------------------------------------------------------

## 3. Filtering and Sorting

Assume a table named `employees`.

### SELECT

Selects columns from a table.

``` sql
SELECT name, salary
FROM employees;
```

Use `*` to select all columns:

``` sql
SELECT *
FROM employees;
```

### WHERE

Filters rows using a condition.

``` sql
SELECT *
FROM employees
WHERE salary > 30000;
```

### AND, OR, and NOT

``` sql
SELECT *
FROM employees
WHERE department = 'IT' AND salary > 30000;

SELECT *
FROM employees
WHERE department = 'IT' OR department = 'HR';

SELECT *
FROM employees
WHERE NOT department = 'Sales';
```

Use parentheses when mixing `AND` and `OR` to make the intended logic
clear.

### IN

Checks whether a value matches any value in a list.

``` sql
SELECT *
FROM employees
WHERE department IN ('IT', 'HR', 'Sales');
```

### BETWEEN

Checks an inclusive range.

``` sql
SELECT *
FROM employees
WHERE salary BETWEEN 20000 AND 50000;
```

The endpoints are included.

### LIKE

Matches a text pattern.

  Pattern    Meaning
  ---------- -----------------------
  `'A%'`     Starts with A
  `'%a'`     Ends with a
  `'%an%'`   Contains an
  `'_a%'`    Second character is a

``` sql
SELECT *
FROM employees
WHERE name LIKE 'S%';
```

`%` matches zero or more characters; `_` matches exactly one character.
Case sensitivity depends on the database and collation.

### IS NULL

``` sql
SELECT *
FROM employees
WHERE manager_id IS NULL;
```

Do not write `manager_id = NULL`; ordinary equality comparisons with
`NULL` do not work as expected.

### DISTINCT

Returns unique combinations of selected column values.

``` sql
SELECT DISTINCT department
FROM employees;
```

### ORDER BY

Sorts the result.

``` sql
SELECT *
FROM employees
ORDER BY salary DESC;
```

-   `ASC` -- ascending (default in most systems).
-   `DESC` -- descending.

You can sort by multiple columns:

``` sql
SELECT *
FROM employees
ORDER BY department ASC, salary DESC;
```

### LIMIT and OFFSET

Returns a limited number of rows and can skip earlier rows. Common in
PostgreSQL and MySQL:

``` sql
SELECT *
FROM employees
ORDER BY employee_id
LIMIT 10 OFFSET 20;
```

This returns up to 10 rows after skipping 20. SQL Server commonly uses
`OFFSET ... FETCH`; syntax differs by database. Use `ORDER BY` for
predictable pagination.

------------------------------------------------------------------------

## 4. SQL Functions

Functions accept values and return a result. Function names and exact
behaviour can differ between database systems.

### Aggregate functions

Aggregate functions calculate a result from multiple rows.

  Function    Meaning
  ----------- --------------------------------
  `COUNT()`   Counts rows or non-NULL values
  `SUM()`     Adds numeric values
  `AVG()`     Calculates an average
  `MIN()`     Finds the smallest value
  `MAX()`     Finds the largest value

``` sql
SELECT
    COUNT(*) AS employee_count,
    SUM(salary) AS total_salary,
    AVG(salary) AS average_salary,
    MIN(salary) AS minimum_salary,
    MAX(salary) AS maximum_salary
FROM employees;
```

`COUNT(*)` counts rows. `COUNT(column)` counts only non-NULL values in
that column. Most aggregate functions ignore NULL values.

### String functions

``` sql
SELECT UPPER(name) FROM employees;
SELECT LOWER(name) FROM employees;
SELECT LENGTH(name) FROM employees;
SELECT TRIM(name) FROM employees;
SELECT CONCAT(first_name, ' ', last_name) FROM employees;
SELECT SUBSTRING(name FROM 1 FOR 3) FROM employees; -- PostgreSQL syntax
SELECT REPLACE(name, 'a', 'A') FROM employees;
```

Some systems use `LEN()` instead of `LENGTH()`, and substring syntax
varies.

### Numeric functions

``` sql
SELECT ROUND(123.456, 2); -- 123.46
SELECT ABS(-25);           -- 25
SELECT CEIL(10.2);         -- 11
SELECT FLOOR(10.8);        -- 10
```

### Date and time functions

Date functions are database-specific. PostgreSQL examples:

``` sql
SELECT CURRENT_DATE;
SELECT CURRENT_TIMESTAMP;
SELECT EXTRACT(YEAR FROM DATE '2026-11-12');
SELECT DATE_PART('month', TIMESTAMP '2026-11-12 10:30:00');
```

`EXTRACT` and `DATE_PART` can retrieve parts such as year, month, day,
hour, and epoch. In PostgreSQL, subtracting timestamps produces an
interval; extracting epoch from an interval returns seconds.

### CASE expression

`CASE` adds conditional logic to a query.

``` sql
SELECT
    name,
    salary,
    CASE
        WHEN salary >= 50000 THEN 'High'
        WHEN salary >= 30000 THEN 'Medium'
        ELSE 'Low'
    END AS salary_level
FROM employees;
```

------------------------------------------------------------------------

## 5. Aggregate Functions, GROUP BY, and HAVING

### GROUP BY

`GROUP BY` combines rows with the same value into groups. It is commonly
used with aggregate functions.

``` sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```

This returns one result row per department.

### HAVING

`HAVING` filters groups after grouping.

``` sql
SELECT department, AVG(salary) AS average_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 40000;
```

### WHERE vs HAVING

  -----------------------------------------------------------------------
  WHERE                               HAVING
  ----------------------------------- -----------------------------------
  Filters individual rows             Filters groups

  Applied before grouping             Applied after grouping

  Usually does not use aggregate      Commonly uses aggregate conditions
  conditions                          
  -----------------------------------------------------------------------

You can use both:

``` sql
SELECT department, AVG(salary) AS average_salary
FROM employees
WHERE salary > 20000
GROUP BY department
HAVING AVG(salary) > 40000;
```

------------------------------------------------------------------------

## 6. Joins

A JOIN combines related rows from two or more tables.

Assume these tables:

**employees**

    employee_id name     department_id
  ------------- ------ ---------------
              1 Ravi                10
              2 Sita                20
              3 Arun              NULL

**departments**

    department_id department_name
  --------------- -----------------
               10 IT
               20 HR
               30 Sales

### INNER JOIN

Returns only rows that match in both tables.

``` sql
SELECT e.name, d.department_name
FROM employees AS e
INNER JOIN departments AS d
    ON e.department_id = d.department_id;
```

Ravi and Sita are returned. Arun has no matching department.

### LEFT JOIN (LEFT OUTER JOIN)

Returns every row from the left table and matching rows from the right
table. Unmatched right-side columns contain NULL.

``` sql
SELECT e.name, d.department_name
FROM employees AS e
LEFT JOIN departments AS d
    ON e.department_id = d.department_id;
```

Arun is included with a NULL department name.

### RIGHT JOIN (RIGHT OUTER JOIN)

Returns every row from the right table and matching rows from the left
table.

``` sql
SELECT e.name, d.department_name
FROM employees AS e
RIGHT JOIN departments AS d
    ON e.department_id = d.department_id;
```

The Sales department is included even though it has no employee.

### FULL OUTER JOIN

Returns matched rows and unmatched rows from both tables. Missing-side
columns are NULL.

``` sql
SELECT e.name, d.department_name
FROM employees AS e
FULL OUTER JOIN departments AS d
    ON e.department_id = d.department_id;
```

Not every database supports `FULL OUTER JOIN` directly.

### CROSS JOIN

Returns every possible combination of rows (Cartesian product).

``` sql
SELECT e.name, d.department_name
FROM employees AS e
CROSS JOIN departments AS d;
```

If there are 3 employees and 3 departments, the result has 9
combinations.

### SELF JOIN

A table is joined to itself. Useful for employee-manager relationships.

``` sql
SELECT
    e.name AS employee,
    m.name AS manager
FROM employees AS e
LEFT JOIN employees AS m
    ON e.manager_id = m.employee_id;
```

### Multiple-table JOIN

You can join more than two tables by adding more JOIN clauses:

``` sql
SELECT e.name, d.department_name, l.city
FROM employees AS e
JOIN departments AS d
    ON e.department_id = d.department_id
JOIN locations AS l
    ON d.location_id = l.location_id;
```

### UNION vs JOIN

-   `JOIN` combines columns from related rows, side by side.
-   `UNION` combines the result rows of compatible SELECT statements,
    one result set after another.
-   `UNION` removes duplicate rows; `UNION ALL` keeps duplicates.

``` sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
```

Both SELECT statements must return the same number of columns with
compatible data types.

------------------------------------------------------------------------

## 7. Subqueries

A subquery is a query placed inside another SQL query. It is also called
an inner query or nested query.

### Single-row subquery

Returns one row/value.

``` sql
SELECT name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

This finds employees earning more than the company average.

### Multiple-row subquery

Returns multiple values. Use operators such as `IN`, `ANY`, or `ALL` as
appropriate.

``` sql
SELECT name
FROM employees
WHERE department_id IN (
    SELECT department_id
    FROM departments
    WHERE location_id = 5
);
```

### Correlated subquery

A correlated subquery refers to a column from the outer query. It is
logically evaluated in relation to each outer row, though the optimizer
may transform its execution.

``` sql
SELECT e.name, e.salary, e.department_id
FROM employees AS e
WHERE e.salary > (
    SELECT AVG(e2.salary)
    FROM employees AS e2
    WHERE e2.department_id = e.department_id
);
```

This finds employees earning more than their own department's average.

### EXISTS

Checks whether a subquery returns at least one row.

``` sql
SELECT d.department_name
FROM departments AS d
WHERE EXISTS (
    SELECT 1
    FROM employees AS e
    WHERE e.department_id = d.department_id
);
```

### NOT EXISTS

Checks that no matching row exists.

``` sql
SELECT d.department_name
FROM departments AS d
WHERE NOT EXISTS (
    SELECT 1
    FROM employees AS e
    WHERE e.department_id = d.department_id
);
```

### ANY and ALL

-   `> ANY (subquery)` means greater than at least one value returned.
-   `> ALL (subquery)` means greater than every value returned.

``` sql
SELECT name
FROM employees
WHERE salary > ANY (
    SELECT salary FROM employees WHERE department_id = 10
);
```

Be careful with NULL values and empty subquery results; SQL's
three-valued logic can affect comparisons.

------------------------------------------------------------------------

## 8. Common Table Expressions (CTEs)

A CTE is a named temporary result set defined using `WITH`. It exists
for one SQL statement and can make complex queries easier to read.

``` sql
WITH department_averages AS (
    SELECT department_id, AVG(salary) AS average_salary
    FROM employees
    GROUP BY department_id
)
SELECT *
FROM department_averages
WHERE average_salary > 40000;
```

### Multiple CTEs

``` sql
WITH department_averages AS (
    SELECT department_id, AVG(salary) AS average_salary
    FROM employees
    GROUP BY department_id
),
high_salary_departments AS (
    SELECT department_id
    FROM department_averages
    WHERE average_salary > 40000
)
SELECT *
FROM employees
WHERE department_id IN (
    SELECT department_id FROM high_salary_departments
);
```

### Recursive CTE

A recursive CTE refers to itself. It is useful for hierarchical data
such as employee reporting structures or category trees.

``` sql
WITH RECURSIVE employee_hierarchy AS (
    -- Anchor: start with the top-level employee
    SELECT employee_id, name, manager_id, 1 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    -- Recursive step: find employees reporting to the previous level
    SELECT e.employee_id, e.name, e.manager_id, h.level + 1
    FROM employees AS e
    JOIN employee_hierarchy AS h
        ON e.manager_id = h.employee_id
)
SELECT *
FROM employee_hierarchy;
```

The exact recursive syntax differs across database systems. Make sure
the data has no unintended cycles, or recursion may not finish.

------------------------------------------------------------------------

## 9. Database Normalization

### What is normalization?

**Normalization** is the process of organizing data into well-structured
related tables to reduce unnecessary duplication and prevent data
anomalies.

Main goals:

-   Reduce data redundancy (repeated data).
-   Improve data consistency.
-   Protect data integrity.
-   Make insert, update, and delete operations safer.

### Example: unnormalized data

Imagine one table stores student details and several course details in a
single row:

    student_id student_name   courses
  ------------ -------------- -------------
             1 Ravi           SQL, Python
             2 Sita           Java, SQL

The `courses` column contains multiple values. This makes searching and
updating individual courses difficult.

### 1NF -- First Normal Form

A table is in **First Normal Form (1NF)** when:

1.  Each cell contains one atomic value (one value for that column's
    intended meaning).
2.  There are no repeating groups or multi-value columns.
3.  Rows can be uniquely identified.

Convert the earlier table into one course per row:

    student_id student_name   course
  ------------ -------------- --------
             1 Ravi           SQL
             1 Ravi           Python
             2 Sita           Java
             2 Sita           SQL

Now each cell contains a single value. A suitable key could be the
combination `(student_id, course)`.

### 2NF -- Second Normal Form

A table is in **Second Normal Form (2NF)** when:

1.  It is already in 1NF.
2.  Every non-key attribute depends on the whole candidate key, not just
    part of a composite candidate key.

This rule matters especially when a table has a composite key.

Consider:

**student_courses**

    student_id   course_id student_name   course_name   grade
  ------------ ----------- -------------- ------------- -------
             1         101 Ravi           SQL           A
             1         102 Ravi           Python        B
             2         101 Sita           SQL           A

Assume `(student_id, course_id)` is the composite key.

Dependencies: - `student_id` determines `student_name`. - `course_id`
determines `course_name`. - `(student_id, course_id)` determines
`grade`.

`student_name` and `course_name` depend on only part of the composite
key. These are **partial dependencies**, so the table is not in 2NF.

Split it into tables:

**students**

    student_id student_name
  ------------ --------------
             1 Ravi
             2 Sita

**courses**

    course_id course_name
  ----------- -------------
          101 SQL
          102 Python

**student_courses**

    student_id   course_id grade
  ------------ ----------- -------
             1         101 A
             1         102 B
             2         101 A

Now each non-key attribute in these tables depends on the whole key.

### 3NF -- Third Normal Form

A table is in **Third Normal Form (3NF)** when:

1.  It is already in 2NF.
2.  Non-key attributes do not depend transitively on a candidate key.

A **transitive dependency** occurs when a key determines a non-key
attribute, and that non-key attribute determines another non-key
attribute.

Example:

    employee_id employee_name     department_id department_name
  ------------- --------------- --------------- -----------------
              1 Ravi                         10 IT
              2 Sita                         20 HR
              3 Arun                         10 IT

Dependencies: - `employee_id` determines `department_id`. -
`department_id` determines `department_name`. - Therefore,
`department_name` depends transitively on `employee_id`.

Split the table:

**employees**

    employee_id employee_name     department_id
  ------------- --------------- ---------------
              1 Ravi                         10
              2 Sita                         20
              3 Arun                         10

**departments**

    department_id department_name
  --------------- -----------------
               10 IT
               20 HR

Now department information is stored once in the departments table.

A formal definition: for every non-trivial functional dependency
`X → A`, either `X` is a superkey or `A` is a prime attribute.

### BCNF -- Boyce-Codd Normal Form

BCNF is a stronger version of 3NF.

A table is in **BCNF** when, for every non-trivial functional dependency
`X → Y`, `X` must be a superkey.

In simple words: every determinant must be a candidate key or superkey.

BCNF handles certain dependency situations that 3NF can still allow. A
BCNF decomposition should ideally be lossless, but it may not preserve
every functional dependency.

### 4NF -- Fourth Normal Form

A table is in **4NF** when:

1.  It is in BCNF.
2.  It has no non-trivial multivalued dependency unless the determinant
    is a superkey.

A multivalued dependency happens when two independent multi-valued facts
are stored together.

Example: a teacher can have multiple subjects and multiple hobbies, and
subjects are independent of hobbies. Storing every subject-hobby
combination creates unnecessary combinations.

Split the facts into separate tables:

-   `teacher_subjects(teacher_id, subject)`
-   `teacher_hobbies(teacher_id, hobby)`

### 5NF -- Fifth Normal Form

A table is in **5NF** (also called Project-Join Normal Form) when every
non-trivial join dependency is implied by its candidate keys.

In simple terms, it removes certain join-related redundancies that
cannot be handled by 4NF alone. It is mainly relevant to complex data
relationships and is less common in everyday application design.

### Functional dependency

A functional dependency `X → Y` means that the value of X uniquely
determines the value of Y.

Example:

`student_id → student_name`

If each student ID identifies one student, knowing the ID tells us the
student's name.

### Data anomalies

Poor table design can cause three common anomalies.

-   **Insertion anomaly:** You cannot insert one fact without inserting
    an unrelated fact.
-   **Update anomaly:** The same fact is repeated in multiple rows, so
    changing only some copies creates inconsistent data.
-   **Deletion anomaly:** Deleting one row accidentally removes another
    fact you wanted to keep.

### Normalization vs denormalization

  -----------------------------------------------------------------------
  Normalization                       Denormalization
  ----------------------------------- -----------------------------------
  Splits data into related tables     Intentionally combines or
                                      duplicates data

  Reduces redundancy                  May increase redundancy

  Helps maintain consistency          Can make some reads simpler or
                                      faster

  Often needs joins to retrieve       May reduce the number of joins
  related data                        

  Common in transactional systems     Sometimes used in reporting and
                                      analytics
  -----------------------------------------------------------------------

**Important:** Denormalization is a deliberate design choice, not simply
poor database design. It should be based on measured performance needs
and managed carefully to keep duplicated values consistent.

### Advantages of normalization

-   Less duplicate data.
-   Fewer update inconsistencies.
-   Better data integrity.
-   Clearer relationships between entities.
-   Easier maintenance of well-designed data.

### Possible trade-offs

-   More tables and relationships.
-   Queries may require more joins.
-   Some reporting queries may become more complex.
-   Poorly planned decomposition can make application logic harder.

### Quick normalization summary

  -----------------------------------------------------------------------
  Normal form                         Main rule
  ----------------------------------- -----------------------------------
  1NF                                 Each cell contains one atomic
                                      value; no repeating groups

  2NF                                 1NF + no partial dependency of
                                      non-key attributes on a candidate
                                      key

  3NF                                 2NF + no transitive dependency of
                                      non-key attributes on a key

  BCNF                                Every determinant in a non-trivial
                                      functional dependency is a superkey

  4NF                                 BCNF + no improper non-trivial
                                      multivalued dependencies

  5NF                                 No non-trivial join dependencies
                                      except those implied by candidate
                                      keys
  -----------------------------------------------------------------------

**Interview focus:** Understand 1NF, 2NF, 3NF, BCNF, functional
dependency, partial dependency, transitive dependency, and the three
anomalies. Be able to explain each using a small table.

------------------------------------------------------------------------

## 10. Keys and Constraints

### What is a key?

A key is a column or set of columns used to identify rows or establish
relationships between tables.

### Types of keys

-   **Super key:** Any column set that uniquely identifies a row. It may
    contain extra columns.
-   **Candidate key:** A minimal super key; no column can be removed
    while keeping uniqueness.
-   **Primary key:** The candidate key selected as the main row
    identifier. It must be unique and NOT NULL.
-   **Alternate key:** A candidate key that was not selected as the
    primary key.
-   **Foreign key:** A column or set of columns that references a
    candidate/primary key in another or the same table.
-   **Composite key:** A key made from more than one column.
-   **Natural key:** A key based on meaningful real-world data, such as
    a carefully chosen registration number.
-   **Surrogate key:** An artificial identifier, such as an
    auto-generated integer.

### Constraints

Constraints enforce rules on table data.

#### PRIMARY KEY

Uniquely identifies each row and does not allow NULL values.

``` sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);
```

#### FOREIGN KEY

Maintains referential integrity between related tables.

``` sql
CREATE TABLE departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(100)
);

CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    department_id INT,
    FOREIGN KEY (department_id)
        REFERENCES departments(department_id)
);
```

#### UNIQUE

Prevents duplicate values in the constrained column or column
combination. NULL handling can vary by database.

``` sql
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    email VARCHAR(150) UNIQUE
);
```

#### NOT NULL

Requires a value.

``` sql
name VARCHAR(100) NOT NULL
```

#### CHECK

Requires a condition to be true for inserted or updated values.

``` sql
age INT CHECK (age >= 18)
```

#### DEFAULT

Supplies a value when an insert does not provide one for that column.

``` sql
status VARCHAR(20) DEFAULT 'active'
```

### Primary key vs UNIQUE

  -----------------------------------------------------------------------
  Primary key                         UNIQUE constraint
  ----------------------------------- -----------------------------------
  Main identifier for rows            Enforces uniqueness

  Cannot contain NULL                 NULL behaviour varies by database

  One primary-key constraint per      Multiple UNIQUE constraints can
  table                               exist
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 11. Transactions and ACID

### What is a transaction?

A transaction is a group of database operations treated as one logical
unit of work.

Example: transferring money between two accounts requires both the debit
and credit to succeed together.

``` sql
BEGIN;

UPDATE accounts
SET balance = balance - 1000
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE account_id = 2;

COMMIT;
```

If something goes wrong before commit, use `ROLLBACK` to cancel the
uncommitted changes.

### ACID properties

ACID describes four important transaction properties.

1.  **Atomicity:** All operations in the transaction happen, or none do.
2.  **Consistency:** A committed transaction leaves the database
    satisfying its defined rules and constraints.
3.  **Isolation:** Concurrent transactions are controlled so they do not
    interfere in unacceptable ways.
4.  **Durability:** Once committed, changes survive failures according
    to the database's durability guarantees.

### COMMIT

Makes the transaction's changes permanent.

### ROLLBACK

Cancels changes made in the current uncommitted transaction.

### SAVEPOINT

Creates a named point inside a transaction.

``` sql
BEGIN;

UPDATE accounts
SET balance = balance - 100
WHERE account_id = 1;

SAVEPOINT after_debit;

UPDATE accounts
SET balance = balance + 100
WHERE account_id = 2;

ROLLBACK TO SAVEPOINT after_debit;

COMMIT;
```

This example rolls back work after the savepoint, but keeps work before
it. Exact transaction syntax varies by database.

### Isolation levels

Common SQL isolation levels:

-   **Read Uncommitted:** May allow dirty reads in systems that support
    it.
-   **Read Committed:** A query sees only committed data; repeated reads
    may return different results.
-   **Repeatable Read:** Provides stronger consistency for rows read
    during a transaction; exact phantom behaviour varies by database.
-   **Serializable:** Strongest standard isolation level; transactions
    behave as if run one at a time, though the database may require
    retries.

Common concurrency problems:

-   **Dirty read:** Reading another transaction's uncommitted change.
-   **Non-repeatable read:** Reading the same row twice and seeing
    different committed values.
-   **Phantom read:** Repeating a range query and seeing new or removed
    matching rows.

Database implementations differ. PostgreSQL, for example, does not
implement Read Uncommitted as a distinct behaviour from Read Committed.

------------------------------------------------------------------------

## 12. Indexes and Views

### What is an index?

An index is a data structure that helps the database find rows more
efficiently. It is similar to an index in a book.

Without a suitable index, the database may need to scan many or all
rows. With an index, it may be able to locate matching rows faster.

``` sql
CREATE INDEX idx_employees_department
ON employees(department_id);
```

### Types and concepts of indexes

-   **Single-column index:** Built on one column.
-   **Composite index:** Built on multiple columns.
-   **Unique index:** Prevents duplicate indexed key values.
-   **Partial / filtered index:** Indexes only rows that satisfy a
    condition (support varies).
-   **Clustered index:** In systems that support this concept, controls
    or closely relates to the physical organization of table data.
-   **Non-clustered index:** A separate index structure that points to
    table rows.

Index terminology and implementation differ across database systems.
PostgreSQL uses several index types (such as B-tree, Hash, GiST, GIN,
and BRIN) and does not use SQL Server's clustered/non-clustered index
model in exactly the same way.

### Composite index

``` sql
CREATE INDEX idx_department_salary
ON employees(department_id, salary);
```

The order of columns matters. This index is generally most useful for
queries that filter or sort using the leading column, or a suitable
leftmost prefix.

### Advantages of indexes

-   Can speed up filtering, joins, and sorting.
-   Can help enforce uniqueness.
-   Can reduce the amount of data that must be examined.

### Disadvantages of indexes

-   Use additional storage.
-   Can slow down inserts, updates, and deletes because indexes must
    also be maintained.
-   Too many or unsuitable indexes can hurt performance.

### What is a view?

A view is a named query that can be used like a virtual table. A normal
view stores the query definition, not a separate copy of the result
data.

``` sql
CREATE VIEW it_employees AS
SELECT employee_id, name, salary
FROM employees
WHERE department_id = 10;
```

Query the view:

``` sql
SELECT *
FROM it_employees;
```

Remove it:

``` sql
DROP VIEW it_employees;
```

Whether a view can be updated depends on the database and the view
definition.

### Materialized view

A materialized view stores the result of a query physically. It must be
refreshed to reflect changes in the underlying data, according to the
database's refresh mechanism.

------------------------------------------------------------------------

## 13. Window Functions

A window function calculates a value across a set of related rows while
keeping each original row in the result. Unlike ordinary grouping, it
does not collapse all rows into one row per group.

### OVER()

`OVER()` defines the window used by the function.

``` sql
SELECT
    name,
    salary,
    AVG(salary) OVER () AS company_average
FROM employees;
```

Every employee row remains in the result, with the overall average
added.

### PARTITION BY

Divides rows into groups for the window calculation.

``` sql
SELECT
    name,
    department_id,
    salary,
    AVG(salary) OVER (
        PARTITION BY department_id
    ) AS department_average
FROM employees;
```

Each employee is compared with the average for their department.

### ORDER BY inside OVER

Defines the order used by ranking or other order-sensitive window
functions.

### ROW_NUMBER()

Gives each row a unique sequential number within its window.

``` sql
SELECT
    name,
    department_id,
    salary,
    ROW_NUMBER() OVER (
        PARTITION BY department_id
        ORDER BY salary DESC
    ) AS row_num
FROM employees;
```

### RANK()

Gives equal values the same rank and leaves gaps after ties.

Example for scores `100, 90, 90, 80`: ranks are `1, 2, 2, 4`.

### DENSE_RANK()

Gives equal values the same rank but does not leave gaps.

For scores `100, 90, 90, 80`: ranks are `1, 2, 2, 3`.

### LEAD()

Reads a value from a following row in the window order.

``` sql
SELECT
    employee_id,
    salary,
    LEAD(salary) OVER (ORDER BY employee_id) AS next_salary
FROM employees;
```

### LAG()

Reads a value from a preceding row in the window order.

``` sql
SELECT
    employee_id,
    salary,
    LAG(salary) OVER (ORDER BY employee_id) AS previous_salary
FROM employees;
```

### Window functions vs GROUP BY

  -----------------------------------------------------------------------
  Window function                     GROUP BY
  ----------------------------------- -----------------------------------
  Keeps individual rows               Combines rows into groups

  Uses `OVER()`                       Uses `GROUP BY`

  Can show row details alongside      Usually returns group-level results
  calculations                        
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 14. Database Design and Relationships

### What is database design?

Database design is the process of deciding how data should be stored,
divided into tables, connected, and protected using keys and
constraints.

### One-to-One relationship

One row in table A is related to at most one row in table B, and vice
versa.

Example: one person has one passport record.

### One-to-Many relationship

One row in table A can relate to many rows in table B.

Example: one department has many employees. The foreign key is usually
stored on the many side.

### Many-to-Many relationship

Many rows in table A can relate to many rows in table B.

Example: students can enroll in many courses, and each course can have
many students.

Use a junction (bridge) table:

``` sql
CREATE TABLE student_courses (
    student_id INT,
    course_id INT,
    enrollment_date DATE,
    PRIMARY KEY (student_id, course_id),
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

### ER diagram

An Entity-Relationship (ER) diagram visually shows entities (tables),
their attributes, and relationships.

Common components: - Entity: a real-world object represented by a
table. - Attribute: a property represented by a column. - Relationship:
an association between entities. - Cardinality: how many rows can be
related (one-to-one, one-to-many, many-to-many).

------------------------------------------------------------------------

## 15. Stored Procedures, Functions, and Triggers

These features are supported differently across databases.

### Stored procedure

A stored procedure is a named set of database instructions saved in the
database. It can accept parameters and perform operations. Syntax and
capabilities vary significantly.

### SQL function

A database function returns a value or a table, depending on the
database and function definition. Functions are often used inside SQL
expressions.

### Trigger

A trigger is database logic that runs automatically in response to an
event, such as an insert, update, or delete.

Common trigger timings/events include: - BEFORE INSERT - AFTER INSERT -
BEFORE UPDATE - AFTER UPDATE - BEFORE DELETE - AFTER DELETE

Use triggers carefully: hidden automatic behaviour can make systems
harder to debug.

------------------------------------------------------------------------

## 16. Query Execution and Optimization

### Logical order of SQL query processing

A useful simplified logical order is:

1.  `FROM` and `JOIN`
2.  `WHERE`
3.  `GROUP BY`
4.  `HAVING`
5.  `SELECT`
6.  `DISTINCT`
7.  `ORDER BY`
8.  `LIMIT` / `OFFSET` (or the database's equivalent)

This explains why a SELECT alias generally cannot be used in `WHERE`:
the WHERE stage is logically processed before SELECT. Actual database
execution may be optimized and reordered by the query planner.

### What is query optimization?

Query optimization is the process of choosing an efficient way to
execute a SQL query.

Ways to improve queries:

-   Select only the columns you need instead of always using `SELECT *`.
-   Add indexes based on real query patterns and execution plans.
-   Use appropriate join and filter conditions.
-   Avoid unnecessary repeated calculations.
-   Check data types and avoid unnecessary conversions on indexed
    columns.
-   Use pagination carefully for large results.
-   Measure performance before and after changing a query.

### EXPLAIN

Shows the database's planned execution strategy.

PostgreSQL example:

``` sql
EXPLAIN
SELECT *
FROM employees
WHERE department_id = 10;
```

### EXPLAIN ANALYZE

In PostgreSQL, `EXPLAIN ANALYZE` executes the query and reports actual
timing and row counts along with the plan.

``` sql
EXPLAIN ANALYZE
SELECT *
FROM employees
WHERE department_id = 10;
```

Use care: because it runs the query, an `EXPLAIN ANALYZE` on an INSERT,
UPDATE, or DELETE can actually modify data unless run in a transaction
that is rolled back.

### Full table scan

A full table scan reads the table's rows to find matching data. It is
not always bad: for small tables or queries returning a large part of a
table, it may be the most efficient plan.

------------------------------------------------------------------------

## 17. Common Interview Comparisons

### DELETE vs TRUNCATE vs DROP

  -----------------------------------------------------------------------
  DELETE                  TRUNCATE                DROP
  ----------------------- ----------------------- -----------------------
  Removes selected rows   Removes all rows        Removes the table
  or all rows                                     object

  Supports `WHERE`        No `WHERE`              No `WHERE`

  Table structure remains Table structure remains Table structure is
                                                  removed

  Often logs row-level    Often uses a more       Removes the object
  changes, depending on   efficient bulk          
  engine                  operation               

  Transaction behaviour   Transaction behaviour   Transaction behaviour
  varies by database      varies by database      varies by database
  -----------------------------------------------------------------------

### WHERE vs HAVING

-   `WHERE` filters rows before grouping.
-   `HAVING` filters groups after grouping.

### UNION vs UNION ALL

-   `UNION` removes duplicate result rows.
-   `UNION ALL` keeps duplicates and is usually less work.

### CHAR vs VARCHAR

-   `CHAR(n)` is fixed-length character storage (padding behaviour
    depends on the database).
-   `VARCHAR(n)` stores variable-length text up to the specified limit.

### Primary key vs Foreign key

-   Primary key identifies a row in its own table.
-   Foreign key references a key in another or the same table to
    maintain a relationship.

### INNER JOIN vs LEFT JOIN

-   INNER JOIN returns only matching rows.
-   LEFT JOIN returns every left-table row and matching right-table
    data.

### JOIN vs Subquery

Both can express related data retrieval. One is not automatically faster
than the other; the optimizer and query shape determine performance.
Choose the clearest correct form and inspect the execution plan when
needed.

### RANK vs DENSE_RANK vs ROW_NUMBER

  Function         Tie behaviour                  Example ranks for 100, 90, 90, 80
  ---------------- ------------------------------ -----------------------------------
  `ROW_NUMBER()`   Always unique row numbers      1, 2, 3, 4
  `RANK()`         Ties share rank; gaps follow   1, 2, 2, 4
  `DENSE_RANK()`   Ties share rank; no gaps       1, 2, 2, 3

### CTE vs Subquery

-   A CTE is named using `WITH` and can improve readability.
-   A subquery is nested inside another query.
-   Performance depends on the database optimizer and query; a CTE is
    not automatically faster.

### Function vs Stored Procedure

-   A function generally returns a value or table and can often be used
    in SQL expressions.
-   A procedure is generally called as a command and may perform a
    sequence of operations.
-   Exact differences depend on the database system.

### NULL vs 0 vs empty string

-   `NULL`: missing or unknown value.
-   `0`: numeric zero.
-   `''`: empty text string.
-   They are different and should not be treated as interchangeable.

### Normalization vs Denormalization

-   Normalization reduces duplication by structuring data into related
    tables.
-   Denormalization intentionally duplicates or combines data to support
    particular read or reporting needs.

------------------------------------------------------------------------

## 18. Practice Questions

Try these questions after studying the topics. Use your own sample
tables and check the output.

### Beginner

1.  Display all columns from a `students` table.
2.  Display only employee names and salaries.
3.  Find employees whose salary is greater than 30,000.
4.  Find employees who belong to the IT or HR department.
5.  Display unique department IDs.
6.  Sort employees by salary from highest to lowest.
7.  Find employees whose names start with `A`.
8.  Find rows where `manager_id` is NULL.

### Intermediate

9.  Count the number of employees in each department.
10. Find the average salary in each department.
11. Display departments with more than five employees.
12. Join employees with departments and show department names.
13. Find employees who earn more than the company average.
14. Find departments that do not have employees.
15. Find the second-highest distinct salary.
16. Find duplicate email addresses.

### Advanced

17. Assign a row number to employees within each department based on
    salary.
18. Rank employees by salary within each department.
19. Find the top three salaries in each department.
20. Use `LAG()` to compare each employee's salary with the previous row
    in a defined order.
21. Use a CTE to calculate department-wise average salary.
22. Write a recursive CTE to display an employee hierarchy.
23. Explain how you would normalize a student-course table.
24. Explain the difference between 2NF and 3NF with examples.
25. Use `EXPLAIN` to inspect a query and discuss whether an index may
    help.
