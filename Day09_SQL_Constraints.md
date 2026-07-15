# Day 9 - SQL Constraints(THE RULES OF A DATABASE)

## Introduction

Constraints are rules applied to table columns to ensure the accuracy, consistency, and integrity of data.<br>
Constraints prevent invalid data from entering the database

Example:<br>

Student Table

| USN | Name|
| 1 | Dale|

Perfect.

Now imagine someone inserts:

|USN |Name|
|NULL |Dale|

Should this be allowed?<br>
No.

Constraints prevent this.

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

Every Email must be Unique.

---

# PRIMARY KEY( Important Concept)

A Primary Key uniquely identifies each record.

Properties:

- Unique
- Cannot be NULL

Example:

```sql
StudentID INT PRIMARY KEY
```

This automatically means:

- Unique
- NOT NULL

---

# DEFAULT

Assigns a default value when no value is provided.<br>
Suppose every new student belongs to Semester 1 unless specified.

Instead of typing:<br>
Semester = 1
everytime,

use:

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

# Summary

- Constraints maintain data integrity.
- PRIMARY KEY = UNIQUE + NOT NULL.
- UNIQUE prevents duplicate values.
- DEFAULT assigns automatic values.
- CHECK validates values before insertion.
