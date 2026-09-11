# Day 29 - Fourth Normal Form (4NF)

## Introduction

4NF stands for **Fourth Normal Form**.

It deals mainly with **multivalued dependencies**.

## Why Do We Need 4NF?

Consider:

| Student | Hobby    | Language |
| ------- | -------- | -------- |
| Pablo   | Guitar   | English  |
| Pablo   | Guitar   | Kannada  |
| Pablo   | Football | English  |
| Pablo   | Football | Kannada  |

Pablo has multiple hobbies and multiple languages, and the two sets are **independent**.

The table stores every possible combination, creating unnecessary redundancy.

---

## The Problem

If Pablo learns another language:

```text
German
```

we need:

```text
Pablo | Guitar   | German
Pablo | Football | German
```

The combinations are created because `Hobby and Language are independent`.

This causes redundancy and makes insertion, deletion, and maintenance more complicated.

---

## 4NF Rule

A relation is in **4NF** if:

> For every non-trivial multivalued dependency `X ↠ Y`, X must be a superkey.

Simple process:

1. Find the multivalued dependency.( Student ↠ Hobby)
2. Identify its determinant.(Student)
3. Check whether the determinant is a superkey. (Student isn't a super key)
4. If it is not a superkey, there is a 4NF violation.

---

## How 4NF Fixes It

Separate the independent facts.

### Student_Hobby

| Student | Hobby    |
| ------- | -------- |
| Pablo   | Guitar   |
| Pablo   | Football |

MVD : Student ↠ Hobby<br>
Superkey: (Student, Hobby)

<br>

### Student_Language

| Student | Language |
| ------- | -------- |
| Pablo   | English  |
| Pablo   | Kannada  |
| Pablo   | German   |

MVD : Student ↠ Language<br>
Superkey: (Student, Language)

Now there are no unnecessary combinations.

---

## 3NF vs BCNF vs 4NF

|               | 3NF                               | BCNF                           | 4NF                          |
| ------------- | --------------------------------- | ------------------------------ | ---------------------------- |
| Main concept  | Transitive dependency             | Determinant must be a superkey | Multivalued dependency       |
| Dependency    | `X → Y`                           | `X → Y`                        | `X ↠ Y`                      |
| Main question | Is there a transitive dependency? | Is X a superkey?               | Is X a superkey for the MVD? |

---

## Functional Dependency vs Multivalued Dependency

### Functional Dependency

```text
Student → Department
```

A student determines one specific department.

### Multivalued Dependency

```text
Student ↠ Hobby
```

A student can have multiple hobby values.

```text
Student ↠ Language
```

The key difference:

```text
→  = determines a value
↠  = determines a set of values
```

---

## Summary

- **1NF** → Atomic values.
- **2NF** → No partial dependency.
- **3NF** → No transitive dependency.
- **BCNF** → Every determinant must be a superkey.
- **4NF** → Remove problematic multivalued dependencies.
- `→` represents a functional dependency.
- `↠` represents a multivalued dependency.
- Independent multi-valued facts should be stored in separate tables.
