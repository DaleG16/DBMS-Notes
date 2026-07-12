# Day 7 - ER Diagram Design

## Introduction

An Entity-Relationship (ER) Diagram is a graphical representation of a database. <br>
It shows entities, attributes, relationships, keys, and cardinality.

Just like an architect draws a blueprint before building a house, a **database designer draws an ER diagram before creating tables**.

---

# Steps to Design an ER Diagram

## Step 1 - Identify Entities

Find the real-world objects involved in the system.<br>
Example:

Library Management System

- Student
- Book
- Course

These are Entities.

---

## Step 2 - Identify Attributes

List the properties of each entity.

Example:

Student

- USN
- Name
- Branch

Book

- BookID
- Title
- Author

---

## Step 3 - Identify Primary Keys

Assign a unique identifier to each entity.

Examples:

- For Student, Primary key is USN since from USN we can uniquely identify a student.
- For Book → BookID is Primary key.

---

## Step 4 - Identify Relationships

Determine how entities are connected.

Examples:

- Student enrolls in Course
- Student borrows Book
- Librarian issues Book

---

## Step 5 - Identify Cardinality

Determine whether the relationship is:

- One-to-One (1:1)
- One-to-Many (1:M)
- Many-to-One (M:1)
- Many-to-Many (M:N)

Example:

Librarian <--> Book

One librarian can issue many books.<br>
One book is issued by one librarian at a time.

1:M

---

# Complete ER Diagram

Example Student Management system<br>
![ER Diagram](/images/ER_Diagram.png)
<br>

- One Admin can manage many courses but each course is managed by one admin.

- If Course means Subject (DBMS, Java, Python), then:<br>
  A student takes many courses and a course has many students.

- One teacher can teach multiple courses but one course can have only one teacher.

Why not connect Teacher and Student directly?<br>
Because the database designer decided that:

- A teacher teaches many courses.
- A student enrolls in courses.

Once you know the course, you automatically know which teacher teaches which student.

---

# Summary

- ER Diagram is the blueprint of a database.
- Start by identifying entities.
- Every entity should have a Primary Key.
- Relationships connect entities.
- Cardinality describes how entities are related.
