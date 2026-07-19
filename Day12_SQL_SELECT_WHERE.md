# Day 12 - SQL SELECT & WHERE

## Introduction

Consider the STUDENT Table<br>
![Student List](/images/Student_list.png)

The SELECT statement is used to retrieve data from a database table.

---

# SELECT

Retrieves all columns from a table.

```sql
SELECT *
FROM Student;
```

![Student List](/images/Student_list.png)

Why "\*"?

The asterisk means:<br>
**All columns**

It does not mean all rows.

---

# Selecting Specific Columns

```sql
SELECT Name, Branch
FROM Student;
```

## ![Name and Branch](/images/Name_Branch.png)

# WHERE

Filters rows based on a condition.

```sql
SELECT *
FROM Student
WHERE Branch='AIML';
```

![AIML Students](/images/AIML_Only.png)

---

# AND

Returns rows only if all conditions are true.

```sql
SELECT *
FROM Student
WHERE Branch='CSE'
AND Age>20;
```

![AND Operator](/images/AND_Operator.png)

---

# OR

Returns rows if at least one condition is true.

```sql
SELECT *
FROM Student
WHERE Branch='EEE'
OR Branch='CIVIL';
```

![ORc Opeartor](/images/OR_Operator.png)

---

### Common Mistakes

❌ SELECT FROM Student;<br>
Missing column names.

❌SELECT Name Branch FROM Student;<br>
Missing comma.

❌ WHERE Branch=AIML<br>
Text values need quotes

---

# Summary

- SELECT retrieves data.
- WHERE filters rows.
- AND requires all conditions.
- OR requires at least one condition.
