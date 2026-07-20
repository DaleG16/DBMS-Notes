# Day 13 - ORDER BY, DISTINCT & LIMIT

## Introduction

Imagine asking:

Oldest student first?<br>
Students in alphabetical order?<br>
Only unique branches?<br>
Only the first 3 students?

Cnsider the Student Table:<br>
![Student Table](/images/Student_list.png)

## ORDER BY

Sorts query results.<br>
By default...

ORDER BY sorts in ascending order (ASC).

Example:

```sql
SELECT * FROM Student
ORDER BY Age;
```

Output<br>
![Age Ascending](/images/Age_ascending.png)

---

## DESC

Descending order.

```sql
SELECT * FROM Student
ORDER BY Age DESC;
```

Output<br>
![Age Descending](/images/Age_descending.png)

---

## DISTINCT

Returns unique values.

Imagine this Query:<br>
SELECT Branch FROM Student;

Output would be:<br>
![Without Distinct](/images/Without_distinct.png)

Branches are repeated which we dont want.

```sql
SELECT DISTINCT Branch
FROM Student;
```

Output:<br>
![With Distinct](/images/With_distinct.png)

---

## LIMIT

Returns only a specified number of rows.

```sql
SELECT * FROM Student
LIMIT 3;
```

LIMIT 3 displays only the first 3 rows from the table.

Output:<br>
![Limit](/images/Limit.png)

---

## Combining Commands

Lets say I want the oldest Student.

```sql
SELECT * FROM Student
ORDER BY AGE DESC
LIMIT 1;
```

Output:<br>
![Oldest Student](/images/Oldest_student.png)

---

## Summary

- ORDER BY sorts data.
- ASC = ascending.
- DESC = descending.
- DISTINCT removes duplicate values.
- LIMIT restricts the number of rows returned.
