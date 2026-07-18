# Day 11 - SQL INSERT, UPDATE & DELETE

## Introduction

Imagine you've built a brand-new library.

You have:<br>

- Shelves
- Sections
- Labels

But...<br>
There are no books on the shelves!

A database without data is just an empty structure.

**DML (Data Manipulation Language) is used to INSERT, UPDATE, and DELETE records in a database.**

---

# INSERT

Adds new rows to a table.

Preferred syntax:

```sql
INSERT INTO Student
(USN, NAME, BRANCH, AGE,Email)
VALUES
('4SO23AI021', 'Luis', 'AIML', 18,'Luis21@gmail.com');
```

For inserting multiple students,

```sql
INSERT INTO Student
(USN, NAME, BRANCH, AGE,Email)
VALUES
('4SO23AI021', 'Luis', 'AIML', 18,'Luis21@gmail.com'),
('4SO23AI022', 'Trisa', 'AIML', 18,'Trisa22@gmail.com'),
('4SO23AI023', 'Leona', 'AIML', 19,'Leona23@gmail.com'),
('4SO23AI024', 'Manuel', 'AIML', 18,'Manuel24@gmail.com'),
('4SO23AI025', 'Aldrin', 'AIML', 18,'Aldrin25@gmail.com');
```

Output<br>
![INSERTED OUTPUT](/images/Values_in_student.png)

---

# UPDATE

Modifies existing records.<br>
Suppose Trisa changes branch from AIML to Data Science.

Example:

```sql
UPDATE student
SET BRANCH='Data Science'
WHERE USN='4SO23AI022;
```

Output<br>
![Updated_output](/images/Updated_output.png)

---

# DELETE

Removes records from a table.

Suppose Manuel Leaves the college then only Manuels entry should be deleted.

Example:

```sql
DELETE FROM Student
WHERE USN='4SO23AI024;
```

Output<br>
![Deleted Output](/images/Deleted_output.png)

---

### Common Mistakes

❌ Forgetting quotes around text.

**Wrong:**

INSERT INTO Student
VALUES (4SO23AI031, Pablo, AIML, 18,pablo31@gmail.com);

**Correct:**

INSERT INTO Student
VALUES ('4SO23AI031;, 'Pablo', 'AIML', 18,'pablo31@gmail.com');

❌ Forgetting WHERE in UPDATE.

---

# Summary

- INSERT adds new records.
- UPDATE modifies existing records.
- DELETE removes records.
- Always use WHERE with UPDATE and DELETE unless you intentionally want to affect all rows.

---
