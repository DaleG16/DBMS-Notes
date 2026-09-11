# Day 30 - Multivalued Dependency

## Introduction

A multivalued dependency occurs in a relation when **one attribute** determines **multiple independent values** of another attribute, independent of other attributes.

A multivalued dependency always **requires at least three attributes** because it consists of at least two attributes that are dependent on a third.

---

### Trivial vs Non-Trivial

**Trivial**

A multivalued dependency X->>Y is trivial if Y is a subset of X, or if X and Y together make up all attributes in the relation.

**Non-Trivial**

It is non-trivial if X and Y are independent and separate sets of columns.

---

### Example

```
| Course     | Instructor      | TextBook_Author |
|------------|-----------------|-----------------|
| Management | John Smith      | Churchill       |
| Management | Robert Peters   | Peters          |
| Management | David Wilson    | Peters          |
| Finance    | Michael Brown   | Weston          |
| Finance    | Michael Brown   | Gilbert         |

```

Three attributes: Course, Instructor, and TextBook_Author.

For a single Course -> there is a set of Instructors. <br>
For the same Course -> there is a set of TextBook_Authors.

The Instructors and Authors have no relationship to each other; they are independent.

---

### How it is represented?

Using symbol: `->>`

Course ->> Instructor<br>
Course ->> TextBook_Author

---

### Problem

If stored in the same table, this creates redundant combinations and data anomalies.
