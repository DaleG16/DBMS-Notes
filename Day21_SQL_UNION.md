# Day 21 - UNION & UNION ALL

## Introduction

Imagine your college has two separate lists.

Table-1 : AIML

```text
+-----------+
| Name      |
+-----------+
| Pablo     |
| Chris     |
| Raghav    |
+-----------+

```

Table-2 : CSDS

```text
+-----------+
| Name      |
+-----------+
| Leona     |
| Karan     |
| Mark      |
+-----------+
```

The principal asks:<br>
"Give me one single list of everyone."

We're not connecting tables.

We're simply **stacking one list on top of another**.<br>
That's what UNION does.

---

### JOIN vs UNION

This is one of the most important concepts.

**JOIN**

Think horizontal.

![join](/images/join.png)

<br>

**UNION**

Think vertical.

![union](/images/union.png)

---

## UNION

Combines the results of two or more SELECT queries.

Removes duplicate rows.

Example:

```sql
SELECT Name
FROM AIML

UNION

SELECT Name
FROM CSDS;
```

Output:<br>

![union](/images/union.png)

---

## UNION ALL

Combines all rows, including duplicates.

```sql
SELECT Name
FROM AIML

UNION ALL

SELECT Name
FROM CSDS
```

Output:<br>

![union](/images/union_all.png)

---

## Rules

- Both queries must return the same number of columns.

**Correct:** (Same number of columns)

```sql
SELECT Name
FROM AIML

UNION

SELECT Name
FROM CSDS;
```

**Wrong:** (Different number of columns )

```sql
SELECT Name,Age
FROM AIML

UNION

SELECT Name
FROM CSDS;
```

- Data types should be compatible. (You cannot give INT in one table and VARCHAR in another table)

---

## Difference between JOIN & Union

| JOIN             | UNION         |
| ---------------- | ------------- |
| Combines Columns | Combines Rows |
| Horizontal       | Vertical      |

---

## Summary

- UNION = Unique rows.
- UNION ALL = All rows.
- JOIN = columns.
- UNION = rows.
