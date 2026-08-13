# Day 25 - First Normal Form (1NF)

## Why Do We Need 1NF?

Consider a table where multiple courses are stored inside one cell:

| StudentID | Name | Courses |
|---|---|---|
|101|Pablo|DBMS, AI|
|102|Alice|DBMS, OS|
|103|Bob|AI, OS, Cloud|

The `Courses` column contains multiple values in a single cell.

This creates problems when searching, filtering, updating, and maintaining the data.

---

## What is 1NF?

**First Normal Form (1NF)** requires each attribute to contain **atomic values**.

In simple words:

> **One cell should contain one value.**

---

## ❌ Table Not in 1NF

| StudentID | Name | Courses |
|---|---|---|
|101|Pablo|DBMS, AI|
|102|Alice|DBMS, OS|

The `Courses` attribute contains multiple values.

---

## ✅ Table in 1NF

| StudentID | Name | Course |
|---|---|---|
|101|Pablo|DBMS|
|101|Pablo|AI|
|102|Alice|DBMS|
|102|Alice|OS|

Each cell now contains a single value.

---

## Example with Phone Numbers

### ❌ Not in 1NF

| StudentID | Name | Phone |
|---|---|---|
|101|Pablo|9876543210, 9123456789|

The Phone column contains multiple values.

### ✅ 1NF

| StudentID | Name | Phone |
|---|---|---|
|101|Pablo|9876543210|
|101|Pablo|9123456789|

---

## Atomic Values

Atomic means that the attribute contains a single value for the purpose of that attribute.

For example:

```text
Name = Pablo Chris