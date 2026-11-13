# SQL Normalization

## 1. Introduction

SQL Normalization is the process of organizing data in a database to reduce data duplication and improve data consistency.

It divides large tables into smaller, related tables and establishes relationships between them using primary keys and foreign keys.

### Why is Normalization Important?

- Reduces duplicate data.
- Improves data consistency.
- Makes database management easier.
- Organizes data efficiently.

---

## 2. First Normal Form (1NF)

First Normal Form (1NF) ensures that every column contains only a single, atomic value. Each record should be unique, and there should be no repeating groups or multiple values in a single cell.

### Rules of 1NF

- Each column must contain atomic (single) values.
- Each row must be unique.
- Each column should contain values of the same type.
- There should be no repeating groups.

### Example

**Before 1NF:**

| Student_ID | Student_Name | Subjects |
|---|---|---|
| 1 | Rahul | SQL, Python |
| 2 | Priya | Java, C++ |

The Subjects column contains multiple values in a single cell, which violates 1NF.

**After 1NF:**

| Student_ID | Student_Name | Subject |
|---|---|---|
| 1 | Rahul | SQL |
| 1 | Rahul | Python |
| 2 | Priya | Java |
| 2 | Priya | C++ |

Now, each cell contains only one value.

**Conclusion:** 1NF removes multiple values from a single column and ensures atomic data.

---

## 3. Second Normal Form (2NF)

Second Normal Form (2NF) ensures that a table is already in 1NF and that every non-key column depends on the entire primary key, not just a part of it.

It removes partial dependencies.

### Rules of 2NF

- The table must already be in 1NF.
- It should not contain partial dependencies.
- Every non-key attribute must depend on the complete primary key.

### Example

Consider a table with a composite primary key consisting of Student_ID and Course_ID.

**Before 2NF:**

| Student_ID | Course_ID | Student_Name | Course_Name |
|---|---|---|---|
| 1 | 101 | Rahul | SQL |
| 1 | 102 | Rahul | Python |
| 2 | 103 | Priya | Java |

Here:

- Student_Name depends only on Student_ID.
- Course_Name depends only on Course_ID.
- Both columns do not depend on the complete composite key.

This is called a partial dependency.

**After 2NF:**

**Student Table**

| Student_ID | Student_Name |
|---|---|
| 1 | Rahul |
| 2 | Priya |

**Course Table**

| Course_ID | Course_Name |
|---|---|
| 101 | SQL |
| 102 | Python |
| 103 | Java |

**Student_Course Table**

| Student_ID | Course_ID |
|---|---|
| 1 | 101 |
| 1 | 102 |
| 2 | 103 |

Now, each non-key attribute depends on the complete primary key of its respective table.

**Conclusion:** 2NF removes partial dependencies and ensures complete dependency on the primary key.

---

## 4. Third Normal Form (3NF)

Third Normal Form (3NF) ensures that a table is already in 2NF and that non-key attributes do not depend on other non-key attributes.

It removes transitive dependencies.

### Rules of 3NF

- The table must already be in 2NF.
- There should be no transitive dependency.
- Non-key attributes should depend directly on the primary key.

### Example

**Before 3NF:**

| Student_ID | Student_Name | Department_ID | Department_Name |
|---|---|---|---|
| 1 | Rahul | 10 | Computer Science |
| 2 | Priya | 20 | Information Technology |
| 3 | Amit | 10 | Computer Science |

Here:

- Student_ID determines Student_Name.
- Student_ID determines Department_ID.
- Department_ID determines Department_Name.

Therefore, Department_Name indirectly depends on Student_ID through Department_ID.

This is called a transitive dependency.

**After 3NF:**

**Student Table**

| Student_ID | Student_Name | Department_ID |
|---|---|---|
| 1 | Rahul | 10 |
| 2 | Priya | 20 |
| 3 | Amit | 10 |

**Department Table**

| Department_ID | Department_Name |
|---|---|
| 10 | Computer Science |
| 20 | Information Technology |

Now, department information is stored separately.

**Conclusion:** 3NF removes transitive dependencies and ensures that non-key attributes depend directly on the primary key.

---

## 5. Boyce-Codd Normal Form (BCNF)

Boyce-Codd Normal Form (BCNF) is a stronger version of Third Normal Form (3NF).

A table is in BCNF if, for every non-trivial functional dependency X → Y, X must be a super key.

In simple words, every determinant must be a candidate key or super key.

### Rules of BCNF

- The table must satisfy 3NF.
- Every determinant must be a super key.
- Every functional dependency must have a super key on its left side.

### Example

Consider the following table:

| Student | Subject | Teacher |
|---|---|---|
| Rahul | SQL | Amit |
| Priya | Python | Neha |
| Rahul | Python | Neha |

Assume:

- Each student can study multiple subjects.
- Each subject is taught by only one teacher.
- A teacher teaches only one subject.

The functional dependencies are:

- (Student, Subject) → Teacher
- Teacher → Subject

Here, Teacher determines Subject, but Teacher is not a super key.

Therefore, the table violates BCNF.

**After BCNF:**

**Teacher_Subject Table**

| Teacher | Subject |
|---|---|
| Amit | SQL |
| Neha | Python |

**Student_Teacher Table**

| Student | Teacher |
|---|---|
| Rahul | Amit |
| Priya | Neha |
| Rahul | Neha |

Now, every determinant in the resulting tables is a super key.

**Conclusion:** BCNF removes functional dependencies where the determinant is not a super key.

---


## Summary

| Normal Form | Main Purpose |
|---|---|
| 1NF | Removes multiple values in a single cell. |
| 2NF | Removes partial dependencies. |
| 3NF | Removes transitive dependencies. |
| BCNF | Ensures every determinant is a super key. |


## Final Conclusion

SQL Normalization is an important database design technique that helps organize data, reduce redundancy, and maintain data consistency.

Each normal form solves a specific type of database problem.
