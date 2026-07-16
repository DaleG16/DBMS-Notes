# Day 10 - Foreign Keys & Referential Integrity

## Introduction

A Foreign Key is used to establish a relationship between two tables.

It references the Primary Key of another table and helps maintain data consistency.

---

# Foreign Key

A Foreign Key is a column that refers to the Primary Key of another table.

Example:

```sql
FOREIGN KEY(StudentID)
REFERENCES Student(StudentID);
```

---

# Parent Table

The table containing the Primary Key.

Example:

Student

---

# Child Table

The table containing the Foreign Key.

Example:

Enrollment

---

# Referential Integrity

Referential Integrity ensures that every Foreign Key value matches an existing Primary Key value.

This prevents invalid references between tables.

---

# ON DELETE CASCADE

Automatically deletes child records when the parent record is deleted.

---

# ON DELETE SET NULL

Sets the Foreign Key to NULL when the parent record is deleted.

---

# RESTRICT

Prevents deletion of the parent record if related child records exist.

---

# Difference Between Primary Key and Foreign Key

| Primary Key                  | Foreign Key              |
| ---------------------------- | ------------------------ |
| Uniquely identifies a record | References another table |
| One per table                | Multiple allowed         |
| Cannot be NULL               | Can be NULL              |

---

# Summary

- Foreign Keys connect tables.
- Foreign Keys reference Primary Keys.
- Foreign Keys maintain Referential Integrity.
- Parent tables contain Primary Keys.
- Child tables contain Foreign Keys.

---
