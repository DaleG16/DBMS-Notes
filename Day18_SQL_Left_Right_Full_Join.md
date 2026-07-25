# Day 18 - LEFT JOIN, RIGHT JOIN & FULL OUTER JOIN

## Introduction

Consider the Student Table (Left Table)

```text
+-----------+---------+
| StudentID | Name    |
+-----------+---------+
| 1         | Alice   |
| 2         | Bob     |
| 3         | Charlie |
| 4         | David   |
+-----------+---------+
```

<br>
<br>
Consider the Enrollment Table (Right Table)

```text
+-----------+--------+
| StudentID | Course |
+-----------+--------+
| 1         | DBMS   |
| 3         | AI     |
| 5         | ML     |
+-----------+--------+
```

StudentID 5 exists in Enrollment...<br>
But StudentID 5 does not exist in Student.

Also...

David exists in Student...<br>
But he isn't enrolled in anything.

## INNER JOIN

INNER JOIN says:

"I only want students who exist in BOTH tables(Matching rows)."

```sql
SELECT Student.Name, Enrollment.Course
FROM Student
INNER JOIN Enrollment
ON Student.StudentID = Enrollment.StudentID;
```

Bob?<br>
❌ No course.

David?<br>
❌ No course.

StudentID 5?<br>
❌ No student.
<br>

Output:<br>

```text
+---------+--------+
| Name    | Course |
+---------+--------+
| Alice   | DBMS   |
| Charlie | AI     |
+---------+--------+
```

---

## LEFT JOIN

LEFT JOIN always **keeps every row from the LEFT table** and **matching rows from other table**.<br>
Otherwise SQL displays NULL for the missing values." .

```sql
SELECT Student.Name, Enrollment.Course
FROM Student
LEFT JOIN Enrollment
ON Student.StudentID = Enrollment.StudentID;
```

Lets understand this clearly:<br>
**keeps every row from the LEFT table** - Alice,Bob,Charlie,David from left table are returned.<br>
**matching rows from other table** - StudentID 1 and StudentID 3 (Right Table) matches StudentID 1 and StudentID 3(Left Table)<br>
Otherwise SQL displays NULL for the missing values - Bob and David did not enroll in any course so it's NULL.
<br>
<br>
Output:<br>

```text
+---------+--------+
| Name    | Course |
+---------+--------+
| Alice   | DBMS   |
| Bob     | NULL   |
| Charlie | AI     |
| David   | NULL   |
+---------+--------+
```

---

## RIGHT JOIN

Returns all rows from the right table and matching rows from the left table.

```sql
SELECT Student.Name, Enrollment.Course
FROM Student
RIGHT JOIN Enrollment
ON Student.StudentID = Enrollment.StudentID;
```

**All rows from right table** - DBMS,AI and ML(No student)<br>
**Matching rows from left table** - StudentID 1 and Student ID 3(Left Table) matches StudentID 1 and StudentID 3(Right Table).<br>
Displays NULL for for missing value(No student for ML)
<br>
<br>
Output:<br>

```text
+---------+--------+
| Name    | Course |
+---------+--------+
| Alice   | DBMS   |
| Charlie | AI     |
| NULL    | ML     |
+---------+--------+
```

---

## FULL OUTER JOIN

Returns all rows from both tables.

```sql
SELECT Student.Name, Enrollment.Course
FROM Student
FULL OUTER JOIN Enrollment
ON Student.StudentID = Enrollment.StudentID;
```

Nobody disappears.<br>
Everybody comes.
<br>
<br>
Output:<br>

```text
+---------+--------+
| Name    | Course |
+---------+--------+
| Alice   | DBMS   |
| Bob     | NULL   |
| Charlie | AI     |
| David   | NULL   |
| NULL    | ML     |
+---------+--------+
```

---

## Summary

- INNER JOIN → Matching rows only.
- LEFT JOIN → All rows from the left table.
- RIGHT JOIN → All rows from the right table.
- FULL OUTER JOIN → All rows from both tables.
