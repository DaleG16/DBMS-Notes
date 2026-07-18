# Day 10 - Foreign Keys & Referential Integrity

## Introduction

A Foreign Key creates a connection between two tables.

Lets Start with a Problem:

Student

| StudentID | Name  |
| --------- | ----- |
| 101       | Pablo |
| 102       | Rahul |

Course

| CourseID | CName |
| -------- | ----- |
| 1        | DBMS  |
| 2        | OS    |

Now suppose Pablo enrolls in DBMS.

Where do we store this?

Inside Student?<br>
No.

Inside Course?<br>
No.

**We need another table**.

Enrollment

| StudentID | CourseID |
| --------- | -------- |
| 101       | 1        |

How does SQL know that StudentID 101 actually belongs to Pablo?

Answer:<br>
Using a Foreign Key.

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

# Need of Foreign Key

Imagine this:

Enrollment

| StudentID | CourseID |
| --------- | -------- |
| 999       | 1        |

But...<br>
There is no student with ID 999.

Should the database allow this?<br>
No.

Without Foreign Keys, your database becomes inconsistent.

With a Foreign Key, SQL says:

"Before inserting StudentID 999, let me check whether StudentID 999 exists in the Student table."

If not...<br>
Insertion fails.

---

# Referential Integrity

Referential Integrity ensures that **every Foreign Key value matches an existing Primary Key value**.

Example:<br>

Student

| StudentID |
| --------- |
| 101       |

Enrollment

| StudentID |
| --------- |
| 101       |

**VALID**

| StudentID |
| --------- |
| 999       |

**Invalid**

Student 999 doesn't exist.<br>
This rule is called Referential Integrity.

**This prevents invalid references between tables.**

### What Happens When Parent Data is Deleted?

Now someone runs:

DELETE FROM Student<br>
WHERE StudentID=101;

What happens to Enrollment?

Student 101 disappears.

Enrollment still says:<br>
StudentID =101

Broken data.

SQL gives options

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

## Complete Example

```sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL
);
```

```sql
CREATE TABLE Enrollment(

    StudentID INT
    FOREIGN KEY(StudentID)
    REFERENCES Student(StudentID)
);
```

Now, StudentID in Enrollment must exist in Student.

---

# Difference Between Primary Key and Foreign Key

| Primary Key                  | Foreign Key              |
| ---------------------------- | ------------------------ |
| Uniquely identifies a record | References another table |
| One per table                | Multiple allowed         |
| Cannot be NULL               | Can be NULL              |

---

# Summary

Foreign Keys are used to **establish relationships between tables and maintain referential integrity by ensuring that child records always reference valid parent records**.

- Foreign Keys connect tables.
- Foreign Keys reference Primary Keys.
- Foreign Keys maintain Referential Integrity.
- Parent tables contain Primary Keys.
- Child tables contain Foreign Keys.

---
