# Day 19 - SQL Subqueries

## Introduction

<br>
Consider the Student Table<br>

![Student List](/images/Student_list_marks.png)
<br>
<br>
Suppose the Principal ask:

**"Tell me the highest marks in the class."**

The assistant replies: **95**

Now Principal ask:

**"Okay... now tell me the student who scored those marks."**

Notice what happened?

The second question depends on the answer to the first question.

That's exactly what a Subquery is.
<br>

---

# SubQuery

A subquery is a **query written inside another SQL query.**

The inner query executes first, and its result is used by the outer query.
<br>

**Find the student(s) who scored the highest marks.**

At first glance you might think:<br>
"I'll just write MAX(Marks)."

Let's see.

```sql
SELECT MAX(Marks)
FROM Student;
```

The Output:<br>

```text
+-------+
| Marks |
+-------+
| 95    |
+-------+
```

Did SQL tell us who scored 95?<br>
❌ No.

It only returned the number.<br>
We need another query.

<br>

## Example

```sql
SELECT Name
FROM Student
WHERE Marks =
(
    SELECT MAX(Marks)
    FROM Student
);
```

Lets Understand this:<br>

**Step 1 (Inner Query)**

```sql
SELECT MAX(Marks)
FROM Student;
```

SQL secretly executes this first.

Result: 95
<br>

**Step 2 (Outer Query)**

Now SQL replaces the subquery with its result.

So internally it becomes:

```sql
SELECT Name
FROM Student
WHERE Marks = 95;
```

Final Output:<br>

```text
+------------+-------+
| Name       | Marks |
+------------+-------+
| Neha Singh | 95    |
+------------+-------+
```

---

## Another Example

**Find students older than the average age.**
<br>

```sql
SELECT Name
FROM Student
WHERE Age >
(
    SELECT AVG(Age)
    FROM Student
);
```

Output:<br>

```text
+--------------+
| Name         |
+--------------+
| Rahul Verma  |
| Arjun Patel  |
| Vivek Kumar  |
| Karan Mehta  |
+--------------+
```

> Note: A subquery always finds the latest value. That's why it's useful.

---

## Summary

- A subquery is a query inside another query.
- The inner query executes first, and its result is used by the outer query to produce the final result.
- Subqueries avoid writing multiple SQL statements.
- Useful when a query depends on another query.
