# Day 7 - ER Diagram Design

## Introduction

An Entity-Relationship (ER) Diagram is a graphical representation of a database. It shows entities, attributes, relationships, keys, and cardinality.

It acts as the blueprint for designing a database before implementation.

---

# Steps to Design an ER Diagram

## Step 1 - Identify Entities

Find the real-world objects involved in the system.

Example:

- Student
- Book
- Course

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

- Student → USN
- Book → BookID

---

## Step 4 - Identify Relationships

Determine how entities are connected.

Examples:

- Student enrolls in Course
- Student borrows Book

---

## Step 5 - Identify Cardinality

Determine whether the relationship is:

- One-to-One (1:1)
- One-to-Many (1:M)
- Many-to-One (M:1)
- Many-to-Many (M:N)

---

# Common Mistakes

- Treating verbs as entities.
- Choosing Name as Primary Key.
- Forgetting cardinality.
- Treating the application as an entity.

---

# Key Points

- ER Diagram is the blueprint of a database.
- Start by identifying entities.
- Every entity should have a Primary Key.
- Relationships connect entities.
- Cardinality describes how entities are related.

---

# Summary

1. Identify Entities
2. Add Attributes
3. Choose Primary Keys
4. Create Relationships
5. Add Cardinality