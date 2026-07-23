# Day 15 - GROUP BY

## Introduction

Consider the Student Table<br>

![Student list](/images/Student_list_marks.png)

But what if the principal asks:

"How many students are there in **each branch** ?"

`GROUP BY` is used to divide rows into groups based on one or more columns so that aggregate functions like COUNT, SUM, AVG, MIN, and MAX can be calculated separately for each group.

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

**Tip**

> Whenever you see phrases like:

> - per department
> - for each student
> - by category
> - in every branch
> - for every course

> 💡Your brain should immediately think: GROUP BY!

---

## Summary

- GROUP BY creates groups.
- Aggregate functions are calculated separately for each group.

.
