# Day 26 - Second Normal Form (2NF)

## Introduction

### OUR COLLEGE DATABASE

| StudentID | CourseID | StudentName | CourseName | Marks |
| --------- | -------- | ----------- | ---------- | ----- |
| 101       | C01      | Pablo       | DBMS       | 90    |
| 101       | C02      | Pablo       | AI         | 85    |
| 102       | C01      | Alice       | DBMS       | 92    |
| 103       | C01      | Bob         | DBMS       | 78    |

Every cell contains one value.

This table is in 1NF.

So our composite primary key is:(StudentID, CourseID)

1. What determines StudentName?

StudentID = 101 and 101 → Pablo<br>
Therefore, **StudentID → StudentName**

<br>
2. What determines CourseName?

**CourseID → CourseName**

<br>
3. What determines Marks?

StudentID = 101 alone isn't enough.

Pablo has:

C01 → 90
C02 → 85

CourseID = C01 alone isn't enough either.

Different students have different marks.

So we need:
**(StudentID, CourseID) → Marks**

---

## Partial Dependency

(StudentID, CourseID) -> Composite key

But:

StudentID(Part of composite key) → StudentName (non-key atrribute)<br>
StudentName depends on only part of the composite key.

CourseID → CourseName<br>
CourseName depends on only part of the composite key.

This is called **PARTIAL DEPENDENCY**

Partial dependency occurs when a **non-key attribute depends** on only **part of a composite key** instead of the entire composite key.

---

## WHAT IS 2NF?

A relation is in 2NF if it **is in 1NF** and has **no partial dependency** of a non-key attribute on a part of a composite candidate key.

This table is in 2NF

<br>
**Student Table**

| StudentID | StudentName |
| --------- | ----------- |
| 101       | Pablo       |
| 102       | Alice       |
| 103       | Bob         |

<br>

**Course Table**

| CourseID | CourseName |
| -------- | ---------- |
| C01      | DBMS       |
| C02      | AI         |

<br>

**Enrollment Table**

| StudentID | CourseID | Marks |
| --------- | -------- | ----- |
| 101       | C01      | 90    |
| 101       | C02      | 85    |
| 102       | C01      | 92    |
| 103       | C01      | 78    |

We separate information according to what it depends on.

---

## Summary

- 2NF requires the table to already be in 1NF.
- 2NF removes partial dependencies.
- A partial dependency occurs when a non-key attribute depends on only part of a composite key.
