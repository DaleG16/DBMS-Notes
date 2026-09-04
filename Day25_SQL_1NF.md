# Day 25 - First Normal Form (1NF)

## 📌 Introduction

Before we can understand **First Normal Form (1NF)**, we need to understand why databases need to be normalized.

In a poorly designed table, a single cell may contain **multiple values**. For example:

| StudentID | Name  | Courses  |
| --------- | ----- | -------- |
| 101       | Pablo | DBMS, AI |
| 102       | Alice | DBMS, OS |

Here, the `Courses` column contains **more than one value** in a single cell.

This creates problems when we want to:

- Search for a particular course
- Update a course
- Delete a course
- Analyze the data
- Work with the data efficiently

---

## What is 1NF?

**First Normal Form (1NF)** requires each attribute to contain **atomic values**.

In simple words:

> **One cell should contain one value.**

---

Ex:

The `Courses` attribute contains multiple values.

---

## Table in 1NF

| StudentID | Name  | Course |
| --------- | ----- | ------ |
| 101       | Pablo | DBMS   |
| 101       | Pablo | AI     |
| 102       | Alice | DBMS   |
| 102       | Alice | OS     |

Each cell now contains a single value.

---

## Example with Phone Numbers

### Not in 1NF

| StudentID | Name  | Phone                  |
| --------- | ----- | ---------------------- |
| 101       | Pablo | 9876543210, 9123456789 |

The Phone column contains multiple values.

### 1NF

| StudentID | Name  | Phone      |
| --------- | ----- | ---------- |
| 101       | Pablo | 9876543210 |
| 101       | Pablo | 9123456789 |
