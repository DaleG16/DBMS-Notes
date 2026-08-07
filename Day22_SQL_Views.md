# Day 22 - SQL Views

## Introduction

The database has a huge Student table.

```text
+-----------+--------+--------+-------+------------+------------+
| StudentID | Name   | Branch | Marks | Phone      | Address    |
+-----------+--------+--------+-------+------------+------------+
| 101       | Pablo  | AIML   | 95    | 9000000001 | Mangalore  |
| 102       | Alice  | CSE    | 88    | 9000000002 | Udupi      |
| 103       | Bob    | ECE    | 92    | 9000000003 | Mysore     |
| 104       | Chris  | AIML   | 90    | 9000000004 | Bangalore  |
| 105       | Mark   | CSDS   | 85    | 9000000005 | Hubli      |
| 106       | Leona  | CSE    | 97    | 9000000006 | Belagavi   |
| 107       | Karan  | AIML   | 81    | 9000000007 | Shivamogga |
| 108       | Raghav | EEE    | 89    | 9000000008 | Hassan     |
| 109       | Priya  | CSDS   | 94    | 9000000009 | Davanagere |
| 110       | Neha   | AIML   | 87    | 9000000010 | Udupi      |
+-----------+--------+--------+-------+------------+------------+
```

Now imagine...

A teacher logs into the system.

Should the teacher see:

Phone Number?<br>
Address?

❌ No.

The teacher only needs:

Name<br>
Branch<br>
Marks<br>

<br>

**--The Problem--**

Every day the teacher writes:

```sql
SELECT Name, Branch, Marks
FROM Student;
```

Again.<br>
Again.<br>
Again.

Hundreds of times.

Wouldn't it be nice if SQL remembered this query?<br>
**That's why Views were invented.**

<br>

---

## What is a VIEW?

A VIEW is a **saved SQL query** that behaves like a virtual table.<br>
It does not store data separately.

<br>
---What does virtual table mean?---

When you create a normal table:

```sql
CREATE TABLE Student (...);
```

SQL actually stores data.

But when you create a VIEW : It only remembers the query.<br>
**A VIEW is not another table.**

---

## Create a VIEW

```sql
CREATE VIEW TeacherView AS
SELECT Name, Branch, Marks
FROM Student;
```

---

## Use a VIEW

Instead of writing:

```sql
SELECT Name, Branch, Marks
FROM Student;
```

every time...

Simply write:

```sql
SELECT *
FROM TeacherView;
```

Output:<br>

```text
+--------+--------+-------+
| Name   | Branch | Marks |
+--------+--------+-------+
| Pablo  | AIML   | 95    |
| Alice  | CSE    | 88    |
| Bob    | ECE    | 92    |
| Chris  | AIML   | 90    |
| Mark   | CSDS   | 85    |
| Leona  | CSE    | 97    |
| Karan  | AIML   | 81    |
| Raghav | EEE    | 89    |
| Priya  | CSDS   | 94    |
| Neha   | AIML   | 87    |
+--------+--------+-------+
```

### Real-Life Analogy

![Sql View](/images/Sql_View.png)

---

## Advantages

- Reduces repeated queries.
- Improves security by hiding unnecessary columns.
- Makes complex queries easier to reuse.

---

## Summary

- A VIEW is a virtual table.
- VIEW doesnt create another table.
- A VIEW stores the query
- The data always comes from the original table.
