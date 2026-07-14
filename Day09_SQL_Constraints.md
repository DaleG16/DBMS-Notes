# Day 9 - SQL Constraints

## Introduction

Constraints are rules applied to table columns to ensure the accuracy, consistency, and integrity of data.

---

# NOT NULL

Prevents a column from storing NULL values.

Example:

```sql
Name VARCHAR(50) NOT NULL
```

---

# UNIQUE

Ensures that every value in the column is unique.

Example:

```sql
Email VARCHAR(100) UNIQUE
```

---

# PRIMARY KEY

A Primary Key uniquely identifies each record.

Properties:

- Unique
- Cannot be NULL

Example:

```sql
StudentID INT PRIMARY KEY
```

---

# DEFAULT

Assigns a default value when no value is provided.

Example:

```sql
Semester INT DEFAULT 1
```

---

# CHECK

Ensures values satisfy a condition.

Example:

```sql
Age INT CHECK(Age>=18)
```

---

# Key Points

- Constraints maintain data integrity.
- PRIMARY KEY = UNIQUE + NOT NULL.
- UNIQUE prevents duplicate values.
- DEFAULT assigns automatic values.
- CHECK validates values before insertion.

---

# Summary

- NOT NULL → No empty values
- UNIQUE → No duplicate values
- PRIMARY KEY → Unique identifier
- DEFAULT → Automatic value
- CHECK → Validation rule
