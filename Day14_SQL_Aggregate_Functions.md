# Day 14 - SQL Aggregate Functions

## Introduction

Aggregate functions **perform calculations on multiple rows** and return a single result.

---

Consider the Student Table

![Student Table](/images/Student_list_marks.png)

# COUNT()

Counts the number of rows.<br>
Suppose your principal asks:

"How many students are there?"

```sql
SELECT COUNT(*)
FROM Student;
```

Output<br>
![Count](/images/count.png)

---

# SUM()

Returns the total of a numeric column.

```sql
SELECT SUM(Marks)
FROM Student;
```

Output:<br>
![Sum](/images/Sum.png)

Calculation:<br>
88 + 91 + 76 + 84 + 69 + 95 + 82 + 90 + 73 + 87 = 835

** Tip**

> SUM() works only on numeric columns.
> NULL values are ignored.

---

# AVG()

Returns the average value.

```sql
SELECT AVG(Marks)
FROM Student;
```

Output:<br>
![Average](/images/Average.png)

Calculation:<br>
= 835 / 10<br>
= 83.5

---

# MIN()

Returns the smallest value.

```sql
SELECT MIN(Age)
FROM Student;
```

Output:<br>
![Minimum](/images/Minimum.png)

---

# MAX()

Returns the largest value.

```sql
SELECT MAX(Marks)
FROM Student;
```

Output:<br>
![Maximum](/images/Maximum.png)

---

# Summary

- COUNT counts records.
- SUM totals numeric values.
- AVG calculates the average.
- MIN returns the smallest value.
- MAX returns the largest value.
- Aggregate functions can be combined with WHERE.
