# Day 20 - Alias, EXISTS & NOT EXISTS

## Introduction

Consider the Student Table

```text
+-----------+-------+
| StudentID | Name  |
+-----------+-------+
| 101       | Alice |
| 102       | Bob   |
| 103       | Mark  |
+-----------+-------+
```

Consider the Enrollment Table

```text
+-----------+--------+
| StudentID | Course |
+-----------+--------+
| 101       | DBMS   |
| 101       | AI     |
| 103       | OS     |
+-----------+--------+
```

---

### Aliases

An alias is simply a temporary nickname given to a table or a column in a SQL query.

Instead of writing:<br>

```sql
FROM Student
Student.StudentID
```

<br>

Use alias:<br>

```sql
FROM Student S
S.StudentID
```

Here:

Student = original table name
S = alias (nickname)

<br>

Why use aliases?<br>
They make queries shorter and easier to read, especially when working with multiple tables.

<br>

---

## EXISTS

Checks whether a **subquery returns at least one row**.<br>
EXISTS returns TRUE if atleast one row exists and returns FALSE if no row exists.

Example:

```sql
SELECT Name
FROM Student S
WHERE EXISTS
(
    SELECT *
    FROM Enrollment E
    WHERE E.StudentID = S.StudentID
);
```

**Step-by-Step**

**Step 1:**

Student: Alice (101)<br>
Starts with subquery
<br>

```sql
SELECT *
FROM Enrollment E
WHERE E.StudentID = 101;
```

Two rows: DBMS and AI<br>
Since at least one row exists, EXISTS returns TRUE → Alice is included.

**Step 2:**

Student: Bob (102)

```sql
SELECT *
FROM Enrollment E
WHERE E.StudentID = 102;
```

Result: (no rows)<br>
EXISTS returns FALSE → Bob is not included.
<br>

**Step 3:**

Student: Mark (103)

```sql

SELECT *
FROM Enrollment E
WHERE E.StudentID = 103;
```

One row: OS<br>
EXISTS returns TRUE → Mark is included.
<br>

**Output**:<br>

```text
+-----------+
| Name      |
+-----------+
| Alice     |
| Mark      |
+-----------+
```

People often wonder why we write:

EXISTS (SELECT 1 ...)

instead of

EXISTS (SELECT \* ...)

With EXISTS, SQL doesn't care what is selected—it only checks whether any row is returned(You can use any one of them).

The convention is to use SELECT 1 because it makes it clear that the actual values are irrelevant; only the existence of matching rows matters.

<br>

> Note: You can also use JOIN.

---

## NOT EXISTS

Returns rows where the subquery finds no matching rows.

```sql
SELECT Name
FROM Student S
WHERE NOT EXISTS
(
    SELECT *
    FROM Enrollment E
    WHERE E.StudentID = S.StudentID
);
```

**Output**:<br>

```text
+-----------+
| Name      |
+-----------+
| Bob       |
+-----------+
```

---

<br>

| Use `JOIN` when...                               | Use `EXISTS` when...                                |
| ------------------------------------------------ | --------------------------------------------------- |
| You need data from both tables (e.g., `Course`). | You only need to know whether a related row exists. |

---

## Summary

- EXISTS returns TRUE if the subquery returns one or more rows.
- NOT EXISTS returns TRUE if the subquery returns no rows.
- EXISTS is useful for checking whether related data is present.
