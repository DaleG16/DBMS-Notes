# Day 23 - SQL Indexes

## What is an Index?

An index is a data structure created on one or more columns to help the database retrieve rows more efficiently.

### Example

```sql
CREATE INDEX idx_student_name
ON Student(Name);
```

## Why Use Indexes?

Indexes can improve query performance, especially for large tables and frequently searched columns.

Example:

```sql
SELECT *
FROM Student
WHERE Name = 'Pablo';
```

## Advantages

- Faster data retrieval.
- Useful for frequently searched or filtered columns.
- Can improve performance on large tables.

## Disadvantages

- Requires additional storage.
- INSERT, UPDATE and DELETE operations may become more expensive because indexes may also need to be maintained.
- Too many indexes can hurt overall performance.

## Primary Keys

A primary key is commonly backed by an index automatically by database systems.

## Key Idea

VIEW:

- Provides a virtual table based on a saved query.

INDEX:

- Helps the database find data faster.

## Summary

INDEX = Faster data retrieval, with storage and maintenance trade-offs.
