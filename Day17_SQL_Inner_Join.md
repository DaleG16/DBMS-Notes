# Day 17 - SQL INNER JOIN

## Introduction

**Imagine a College Database**

Instead of one huge table...

We divide the data into multiple tables.

### Student Table<br>

![Student](/images/StudentID_Name.png)

### Course Table<br>

![Course](/images/CourseID_Name.png)

### Enrollment Table<br>

![Enrollment](/images/Enrollment.png)

The Enrollment table doesn't store names.<br>
It stores IDs.

Why?<br>
Because **IDs are unique** and avoid repeating the same data. That's good database design.

### THE PROBLEM

Suppose the principal asks:

**"Show me each student's name along with the course they are taking."**

Can we get that from just the Student table?<br>
❌ No.

Can we get it from just the Course table?<br>
❌ No.

Can we get it from just the Enrollment table?<br>
❌ No.

We need to combine information from multiple tables. That's exactly what a JOIN does.

**A JOIN combines rows from two or more related tables.**

---

## INNER JOIN

INNER JOIN returns matching rows.

Example:

Show me each student's name along with the course they are taking

```sql
SELECT Student.Name, Course.CourseName
FROM Enrollment
INNER JOIN Student
ON Enrollment.StudentID = Student.StudentID
INNER JOIN Course
ON Enrollment.CourseID = Course.CourseID;
```
<br>
<br>
<strong>Basic Idea</strong>

1. Firstly I need to connect Enrollment Table to Student Table.
2. Secondly I need to connect Enrollment Table to Course Table.
<br>
<br>
<br>
<strong>Why Student.Name?</strong>

Imagine a large Database where both tables have a column called StudentID.

Writing:<br>
```sql
SELECT StudentID can confuse SQL.
```

Instead, specify the table:<br>
```sql
SELECT Student.StudentID
```

That means StudentID is specifically from Student Table not any other table.
<br>
<br>
<br>
**Understanding the ON Clause**

The line:<br>

```sql
ON Enrollment.StudentID = Student.StudentID
```

means match rows where the Student IDs are equal.<br>
The **ON clause** tells SQL **how the tables are related.**

Here I have specifically written Enrollment.StudentID so that I want StudentID from the Enrollment Table not the Student Table.
<br>
<br>
<br>
**STEP-1 Enrollment INNER JOIN Student** (Happens Internally)

Join with the Student table.

```text
StudentID 101(From Enrollment Table) → PABLO(Student Table)
StudentID 101 → PABLO
StudentID 102 → Alice
StudentID 103 → Bob
StudentID 104 → Xavier
```

The output:<br>

```text
+--------+----------+
| Name   | CourseID |
+--------+----------+
| Alice  |    2     |
| Bob    |    3     |
| Xavier |    4     |
| PABLO  |    1     |
| PABLO  |    2     |
+--------+----------+
```

### Actual Display of the Output:<br>

![Inner join](/images/Inner_Join.png)

---

## Summary

- JOIN combines tables.
- INNER JOIN returns matching rows.
- The ON clause defines how tables are connected.
- Primary Keys and Foreign Keys make joins possible.
