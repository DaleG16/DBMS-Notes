# Day 23 - SQL Indexes

## Introduction

Imagine Your College Library

Suppose your library has 1,00,000 books.

Every book has:

```text

+--------+-------------------+-----------+
| BookID | Title             | Author    |
+--------+-------------------+-----------+
| 1      | DBMS Fundamentals | Korth     |
| 2      | Operating Systems | Galvin    |
| 3      | Computer Networks | Tanenbaum |
| ...    | ...               | ...       |
| 100000 | Deep Learning     | Goodfellow|
+--------+-------------------+-----------+

```

Now you walk into the library and ask:<br>
"Find the book called Deep Learning."

How could the librarian find it?

❌ Method 1 — Search Everything

The librarian starts at Book #1 and continue till Book #1,00,000 (It's a Linear Search)

But...

That's terrible if you have a huge database.

This is called a **full table scan**.

**SOLUTION : INDEXING**

<br>

---

## What is an Index?

Indexing is a technique(data structure) used to **speed up data retrieval** from a database.

Instead of searching through every row in a table, the database uses an index to quickly locate the required rows.

> Note : An index is not another copy of the entire table.
> It is an additional structure that helps the database find rows more efficiently.

A common structure used for database indexes is a B+ Tree.

### Example

```sql
CREATE INDEX idx_student_name
ON Student(Name);
```

Now searches involving Name can potentially use this index:

Example:

```sql
SELECT *
FROM Student
WHERE Name = 'Pablo';
```

---

### Primary Key and Indexes

Suppose:

```sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50),
    Branch VARCHAR(20)
);
```

The primary key is commonly backed by an index automatically in database systems such as MySQL.<br>
So you usually don't need to manually create another index on the primary key.

---

## Advantages

- Faster data retrieval.
- Useful for frequently searched or filtered columns.
- Can improve performance on large tables.

## Disadvantages

- Requires additional storage.
- INSERT, UPDATE and DELETE operations may become more expensive because indexes may also need to be maintained.
- Too many indexes can hurt overall performance.

---

### Important Point

An index does not mean : "Every query using this column will definitely become faster."

The database's query optimizer decides whether using the index is beneficial.

For example, if a table has only 10 rows, scanning the table may be perfectly fine.

---

## Key Idea

VIEW:

- Provides a virtual table based on a saved query.

INDEX:

- Helps the database find data faster.

---

## Summary

INDEX = Faster data retrieval, with storage and maintenance trade-offs.
