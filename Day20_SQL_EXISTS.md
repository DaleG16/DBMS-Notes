# Day 20 - EXISTS & NOT EXISTS

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

## EXISTS

Checks whether a subquery returns at least one row.

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

---

## Key Points

- EXISTS returns TRUE if the subquery returns one or more rows.
- NOT EXISTS returns TRUE if the subquery returns no rows.
- EXISTS is useful for checking whether related data is present.

---

## Summary

- EXISTS → At least one matching row exists.
- NOT EXISTS → No matching rows exist.
