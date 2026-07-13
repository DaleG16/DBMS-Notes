# Day 8 - SQL Basics & Creating Tables

## Introduction

SQL (Structured Query Language) is used to communicate with relational databases.<br>
It allows users to create databases, create tables, insert data, update records, delete records, and retrieve information.

---

# What is SQL?

**SQL is a language** used to interact with a Relational Database Management System (RDBMS).

Examples of RDBMS(Relational):

- MySQL
- PostgreSQL
- Oracle
- SQL Server

---

# Database vs Table

A Database is a collection of related tables.

Example:

CollegeDB

- Student
- Teacher
- Course
- Attendance

Each is a table inside the database.

---

# Creating a Database

```sql
CREATE DATABASE CollegeDB;
```

Creates a new database named CollegeDB.

---

# Selecting a Database

Suppose you have:

- CollegeDB
- LibraryDB
- HospitalDB

Which one should MySQL use?<br>
Tell it.

```sql
USE CollegeDB;
```

Meaning:

"From now on, work inside CollegeDB."<br>
Selects the database for further operations.

---

# Creating a Table

```sql
CREATE TABLE Student
(
    USN INT,
    Name VARCHAR(50),
    Branch VARCHAR(20),
    Age INT
);
```

This creates a table named Student with four columns.

---

# Common Data Types

| Data Type  | Description           |
| ---------- | --------------------- |
| INT        | Whole numbers         |
| VARCHAR(n) | Variable-length text  |
| CHAR(n)    | Fixed-length text     |
| DATE       | Stores dates          |
| FLOAT      | Stores decimal values |

---

# Note

SQL is NOT Case Sensitive<br>

CREATE TABLE Student;<br>
create table student;

These are the same.

But... <br>
Professionals write: CREATE TABLE Student<br>
Much easier to read.

# Common Mistakes

1. VARCHAR ❌

Need size.<br>
VARCHAR(50) ✅

2. Forget semicolon.

# Summary

- SQL is used to communicate with databases.
- A database contains multiple tables.
- CREATE DATABASE creates a database.
- USE selects a database.
- CREATE TABLE creates a new table.
- **Every SQL statement ends with a semicolon (;).**
