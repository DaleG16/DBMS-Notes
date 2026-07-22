# Day 15 - GROUP BY

## Introduction

Consider the Student Table<br>

![Student list](/images/Student_list_marks.png)

But what if the principal asks:

"How many students are there in **each branch** ?"

`GROUP BY` groups rows that have the same value in one or more columns.<br>
It is commonly used with aggregate functions.

---

How does GROUP BY Work?

```text
AIML
│
├── Neha
└── Aarav

CSE
│
├── Priya
└── Vivek

ECE
│
├──Ananya
└── Rahul

EEE
│
├── Sneha
└── Karan

CIV
│
├── Arjun
└── Meera
```

Now SQL performs **calculations inside each classroom**, not on the entire school.

---

## COUNT

```sql
SELECT Branch, COUNT(*)
FROM Student
GROUP BY Branch;
```

Output:<br>
![Count](/images/GroupBy_Count.png)

---

## AVG

```sql
SELECT Branch, AVG(Marks)
FROM Student
GROUP BY Branch;
```

Output:<br>
![Average](/images/GroupBy_Avg.png)

---

## SUM

```sql
SELECT Branch, SUM(Marks)
FROM Student
GROUP BY Branch;
```

Output:<br>
![Sum](/images/GroupBy_Sum.png)

---

## MIN

```sql
SELECT Branch, MIN(Marks)
FROM Student
GROUP BY Branch;
```

Output:<br>
![Minimum](/images/GroupBy_Min.png)

---

## MAX

```sql
SELECT Branch, MAX(Marks)
FROM Student
GROUP BY Branch;
```

Output:<br>
![Maximum](/images/GroupBy_Max.png)

---

## Summary

- GROUP BY creates groups.
- Aggregate functions are calculated separately for each group.

.
