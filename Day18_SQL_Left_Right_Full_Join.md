# Day 18 - LEFT JOIN, RIGHT JOIN & FULL OUTER JOIN

## Introduction

Consider the Users (Left Table)

```text
+-----------+---------+
| userID     | name   |
+-----------+---------+
| 1         | Alice   |
| 2         | Bob     |
| 3         | Charlie |
+-----------+---------+
```

<br>
<br>
Consider the Orders Table (Right Table)

```text
+-----------+--------+---------+
| orderID   | userID |product  |
+-----------+--------+---------+
| 101       | 1      | Laptop  |
| 102       | 2      | Phone   |
+-----------+--------+---------+
```

userID 3 exists in Left Table...<br>
But usertID 3 does not exist in Right Table.
<br>

--Syntax--

```text
SELECT column_name(s)
FROM tableA                     -- The "Left" Table
RIGHT JOIN tableB               -- The "Right" Table
  ON tableA.key = tableB.key;   -- The Matching Condition
```

## INNER JOIN

INNER JOIN says:

"I only want users who exist in BOTH tables(Matching rows)."

```sql
SELECT Users.Name, Orders.product
FROM Users
INNER JOIN Orders
ON Users.userID = Orders.userID;
```


Output:<br>

```text
+---------+--------+
| name    |product |
+---------+--------+
| Alice   |Laptop  |
| Bob     |Phone   |
+---------+--------+
```

---

## LEFT JOIN

LEFT JOIN always **keeps every row from the LEFT table** and **matching rows from other table**.<br>
Otherwise SQL displays NULL for the missing values." .

```sql
SELECT Users.Name, Orders.product
FROM Users
LEFT JOIN Orders
ON Users.userID = Orders.userID;
```

Lets understand this clearly:<br>
**keeps every row from the LEFT table** - Alice, Bob, Charlie from left table are returned.<br>
**matching rows from other table** - UserID 1 and UserID 2 (Right Table) matches UserID 1 and UserID 3(Left Table)<br>
Otherwise SQL displays NULL for the missing values - For charlie it's NULL.
<br>
<br>
Output:<br>

```text
+---------+--------+
| name    |product |
+---------+--------+
| Alice   |Laptop  |
| Bob     |Phone   |
| Charlie |  NULL  |
+---------+--------+
```

---

## RIGHT JOIN

Returns all rows from the right table and matching rows from the left table.

```sql
SELECT Users.Name, Orders.product
FROM Users
Right JOIN Orders
ON Users.userID = Orders.userID;
```

**All rows from right table** - DBMS,AI and ML(No student)<br>
**Matching rows from left table** - StudentID 1 and Student ID 3(Left Table) matches StudentID 1 and StudentID 3(Right Table).<br>
Displays NULL for for missing value(No student for ML)
<br>
<br>
Output:<br>

```text
+---------+--------+
| name    |product |
+---------+--------+
| Alice   | Laptop |
| Bob     | Phone  |
+---------+--------+
```

> Note: In real-world database development, RIGHT JOIN is rarely used.Developers almost exclusively use LEFT JOIN because code is read from left to right.

---

## FULL OUTER JOIN

Returns all rows from both tables.

```sql
SELECT Users.name, Orders.product
FROM Users
FULL OUTER JOIN Orders
ON Users.user_id = Orders.user_id;

```

Nobody disappears.<br>
Everybody comes.
<br>
<br>
Output:<br>

```text
+---------+--------+
| name    | product|
+---------+--------+
| Alice   | Laptop |
| Bob     | Phone  |
| Charlie | NULL   |
+---------+--------+
```

---

## Summary

- INNER JOIN → Matching rows only.
- LEFT JOIN → All rows from the left table.
- RIGHT JOIN → All rows from the right table.
- FULL OUTER JOIN → All rows from both tables.
