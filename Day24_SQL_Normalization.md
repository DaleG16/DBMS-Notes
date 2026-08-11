# 🏫 Normalization in DBMS

## Imagine Your College Database

Suppose your college stores student enrollment information in **one giant table**.

It looks like this:

```text
+-----------+-------------+--------+----------+------------+------------+
| StudentID | StudentName | Branch | CourseID | CourseName | Instructor |
+-----------+-------------+--------+----------+------------+------------+
| 101       | Pablo       | AIML   | C01      | DBMS       | Dr. Rao    |
| 101       | Pablo       | AIML   | C02      | AI         | Dr. Sharma |
| 102       | Alice       | CSE    | C01      | DBMS       | Dr. Rao    |
| 103       | Bob         | ECE    | C01      | DBMS       | Dr. Rao    |
+-----------+-------------+--------+----------+------------+------------+
```

Everything is in one place.

But imagine this database becomes **huge**:

- Thousands of students
- Hundreds of courses
- Multiple instructors
- Thousands of enrollments

And suddenly...

**Problems begin.**

---

# Problem 1 — Data Redundancy

Look at Pablo - stored twice

Similarly, Dr. Rao may appear hundreds or thousands of times if many students take DBMS.

This repeated **storage of the same information** is called: **Data Redundancy**

Why is redundancy a problem?

1. Wastes storage.
2. Makes updates difficult.
3. Can lead to inconsistent data.

---

# Problem 2 — Update Anamoly

Anomaly = Something goes wrong when we INSERT, UPDATE, or DELETE data and <br>
when data is poorly organized.

Suppose:

_Dr. Rao_ changes his name to _Dr. Raj Rao_. We may need to update every DBMS record.

Imagine there are 1000 rows : What if we accidentally update only 990 rows?

10 rows its still the same _Dr. Rao_

This creates Inconsistency called an **UPDATE ANOMALY**

An update anomaly occurs when the same information is stored in multiple places and **updating it in one place but not in another place causes inconsistent data**.

---

# Problem 3 — Insert Anomaly

Suppose the college introduces a new course:

```text
CourseID:    C10
CourseName:  Cloud Computing
Instructor:  Dr. Kumar
```

Our table requires:

StudentID
StudentName
Branch

But since its a new course - No student has enrolled yet.
Without students you cannot insert data into the table.

This is called: **Insert Anomaly**

An insert anomaly happens when you **cannot add new data without adding unrelated data**.

---

# Problem 4 — Delete Anomaly

Suppose Bob is the only student enrolled in a particular course.

Bob's row contains:

StudentID
StudentName
Branch
CourseID
CourseName
Instructor

Now Bob graduates and we delete his row.

```sql
DELETE FROM Enrollment
WHERE StudentID = 103;
```

But that row also contained:

CourseID
CourseName
Instructor

So we accidentally lose information about the course itself.

We wanted to delete - Bob's enrollment

But we also lost - Course information

This is called **Delete Anomaly**

A delete anomaly occurs **when deleting one piece of information accidentally removes other useful information**.

---

# What is the Actual Problem here?

Different types of information are mixed together.

We are storing three different types of information in one table.

Student Information

- StudentID
- StudentName
- Branch

Course Information

- CourseID
- CourseName
- Instructor

Enrollment Information

- StudentID
- CourseID

**All of these are stored together in one giant table.**

---

# Normalization

Normalization is the process of **organizing data into well-structured tables** **to reduce data redundancy** and **prevent insertion, update, and deletion anomalies.**

<br>

Instead of one giant table:(We separate them)

```text
                 GIANT TABLE
                      │
          ┌───────────┼───────────┐
          ↓           ↓           ↓
       Student      Course     Enrollment
      Information  Information  Information
```

---

Then why don't we normalize everything into 100 tiny tables?"

Because more normalization means:

1. More tables
2. More JOINs
3. Queries can become more complex

So database design is about finding an appropriate balance.
