# Day 2 - Database Architecture \& Data Independence

## Three-Level Architecture

The DBMS is organized into three levels _to hide complexity from users_.

### 1. External Level (View Level)

- This is what users see.

- Different users can have different views.

- Improves security by restricting access.

Example:

- Student sees marks and attendance but cannot see faculty salaries.

- Teacher sees all student records.

- Principal sees all information.

--

### 2. Conceptual Level (Logical Level)

- This is the blueprint of the entire database

- Defines tables, relationships, constraints, and keys.

Example:

Student

|USN |Name |Branch

| | |

---

### 3. Internal Level (Physical Level)

- Describes how data is physically stored.

- Includes storage structures, indexes, and memory organization.

- Managed by the DBMS.

### Why do we need these three levels?

Because if everything were directly connected, even small changes would break applications.

---

## Data Independence

It is the ability to modify one level of the database architecture without affecting the higher levels.

There are 2 types.

### Physical Data Independence

- Changes at the Internal Level.

- Does not affect the Conceptual or External Level.

Example:

- Imagine your college changes:

Old HDD

↓

New SSD

Did the student portal change?

No.

Students don't even know.

Because only the Internal Level changed.

### Logical Data Independence

- Changes at the Conceptual Level.

- External views remain mostly unchanged.

Example:

- Adding a new column (Email) to the Student table.

---

Why do we need three-level architecture?

Because it provides:

- Data Independence – Changes in storage or database structure don't affect users.

- Security – Different users see only the information they are authorized to access.

- Flexibility – The database can evolve without rewriting every application.

- Maintainability – Developers can modify one layer without impacting the others.

## Key Point

- External Level = User View

- Conceptual Level = Database Design

- Internal Level = Physical Storage

- Physical Data Independence is easier to achieve.

- Logical Data Independence is harder to achieve(Because changing the database structure can affect applications if not handled properly).
