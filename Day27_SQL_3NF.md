# Day 27 - Third Normal Form (3NF)

## Introduction

A table can be in 2NF and still contain unnecessary redundancy.

Third Normal Form (3NF) deals with **transitive dependency**.

---

## Example

| StudentID | StudentName | BranchID | BranchName |
| --------- | ----------- | -------- | ---------- |
| 101       | Pablo       | B01      | AIML       |
| 102       | Alice       | B02      | CSE        |
| 103       | Bob         | B01      | AIML       |
| 104       | Charlie     | B03      | ECE        |

The primary key is:

```text
StudentID
```

---

## Functional Dependencies

The value of one attribute uniquely determines the value of another attribute.<br>
It is of the form X → Y

```text
StudentID → StudentName
StudentID → BranchID
BranchID → BranchName
```

Therefore:

```text
StudentID → BranchID → BranchName
```

StudentID can determine BranchName indirectly through BranchID.

This is called Transitive Dependency.

A depends on B and B depends on C, so A indirectly determines C.

---

## Transitive Dependency

A transitive dependency occurs when a **non-key attribute depends on another non-key attribute**.

`Formal Definition:`

A relation is in 3NF when:

1. It is already in 2NF.
2. It has no transitive dependency

`BranchID`(non-key) is not the primary key of the Student table, but it determines `BranchName` (another non-key).

---

## Why Is This a Problem?

`AIML` is repeated for every student belonging to branch B01.

If the branch name changes, multiple rows must be updated.

**If one row is not updated**, inconsistent data can occur.

This creates unnecessary redundancy and can lead to update anomalies.

---

## Removing the Transitive Dependency

### Student Table

| StudentID | StudentName | BranchID |
| --------- | ----------- | -------- |
| 101       | Pablo       | B01      |
| 102       | Alice       | B02      |
| 103       | Bob         | B01      |
| 104       | Charlie     | B03      |

### Branch Table

| BranchID | BranchName |
| -------- | ---------- |
| B01      | AIML       |
| B02      | CSE        |
| B03      | ECE        |

Now:

```text
StudentID → StudentName
StudentID → BranchID

BranchID → BranchName
```

Each piece of information is stored in the table where it belongs.

---

## 2NF vs 3NF

|               | 2NF                | 3NF                   |
| ------------- | ------------------ | --------------------- |
| Requires 1NF? | Yes                | Yes                   |
| Main problem  | Partial dependency | Transitive dependency |
| Main focus    | Composite key      | Non-key attributes    |

---

## Simple Mental Model

### 2NF

> Does a non-key attribute depend on only PART of my composite key?

If yes:

```text
Partial Dependency
```

### 3NF

Ask:

> Does a non-key attribute depend on ANOTHER non-key attribute?

If yes:

```text
Transitive Dependency
```

---

## Summary

- A table must already satisfy 2NF before it can satisfy 3NF.
- 3NF removes transitive dependencies.
- A transitive dependency occurs when a non-key attribute depends on another non-key attribute.
- 2NF deals mainly with partial dependency.
- 3NF deals mainly with transitive dependency.
