# Day 29 - Boyce-Codd Normal Form (BCNF)

## Introduction

BCNF stands for **Boyce-Codd Normal Form**.

It is a stronger form of normalization than 3NF.

The normalization journey so far:

```text
1NF → Atomic values
2NF → No partial dependency
3NF → No transitive dependency

```

`BCNF is used to remove certain redundancy and dependency problems that can still exist even when a relation satisfies 3NF`.

---

## What Is BCNF?

A relation is in **BCNF** if, for every non-trivial functional dependency:

```text
X → Y
```

`X` must be a **superkey**.

In simple terms:

> For every functional dependency, the attribute(s) on the left side must be capable of uniquely identifying a row.

The left side of a functional dependency is called the **determinant**.

For example:

```text
Course → Instructor
```

Here:

```text
Course = determinant
Instructor = dependent attribute
```

---

# College Example

Consider:

| Student | Course | Instructor |
| ------- | ------ | ---------- |
| Pablo   | DBMS   | Ravi       |
| Alice   | DBMS   | Ravi       |
| Pablo   | AI     | Kumar      |
| Bob     | AI     | Kumar      |

Assume:

```text
(Student, Course) → Instructor
Course → Instructor
```

---

## Candidate Key

The candidate key is:

```text
(Student, Course)
```

A student can take multiple courses, and a course can be taken by multiple students.

Therefore:

```text
Student
```

alone cannot uniquely identify a row.

Similarly:

```text
Course
```

alone cannot uniquely identify a row.

---

## Checking the BCNF Rule

Consider:

```text
Course → Instructor
```

The determinant is:

```text
Course
```

Now ask:

> Is Course a superkey?

No.

For example:

```text
Pablo | DBMS | Ravi
Alice | DBMS | Ravi
```

`DBMS` appears in multiple rows.

Therefore, `Course` does not uniquely identify a row.

So:

```text
Course → Instructor
```

violates the BCNF rule.

Therefore:

```text
The relation is NOT in BCNF.
```

---

# Why Does This Cause Redundancy?

The relationship:

```text
Course → Instructor
```

is stored repeatedly.

For example:

```text
DBMS → Ravi
DBMS → Ravi
```

If the instructor for DBMS changes, multiple rows must be updated.

If one row is missed, inconsistent data can occur.

---

# Decomposing the Relation

We separate the course-instructor dependency from the student-course relationship.

## Course Table

| Course | Instructor |
| ------ | ---------- |
| DBMS   | Ravi       |
| AI     | Kumar      |

Here:

```text
Course → Instructor
```

The dependency belongs naturally in this table.

---

## Enrollment Table

| Student | Course |
| ------- | ------ |
| Pablo   | DBMS   |
| Alice   | DBMS   |
| Pablo   | AI     |
| Bob     | AI     |

This table represents which student takes which course.

---

# Why Not Student + Instructor?

A wrong decomposition would be:

```text
Student
Instructor
```

This does not follow our functional dependency.

We do NOT have:

```text
Student → Instructor
```

A student can take different courses with different instructors.

Therefore, Student cannot determine one instructor.

---

# 3NF VS BCNF

|           | 3NF                          | BCNF                                            |
| --------- | ---------------------------- | ----------------------------------------------- |
| Main idea | Remove transitive dependency | Every determinant(left side) must be a superkey |
| Strength  | Less strict                  | Stricter                                        |

BCNF is stricter than 3NF.

---

# Important Mental Model

For 3NF, ask:

> Does a non-key attribute depend on another non-key attribute?

For BCNF, ask:

> For every functional dependency X → Y, is X a superkey?

If:

```text
X = superkey
```

then the dependency satisfies the BCNF requirement.

If:

```text
X ≠ superkey
```

then:

```text
BCNF violation
```

---

## Summary

- **BCNF** requires every determinant to be a superkey.
- BCNF is stronger than 3NF.
- To check BCNF, examine every functional dependency and ask whether its determinant is a superkey.
