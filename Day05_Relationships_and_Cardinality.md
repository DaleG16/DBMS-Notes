# Day 5 - Relationships & Cardinality

## Introduction

### Imagine a College

We have two entities.

- Student
- Course

Are they independent?
No.

Students enroll in courses.
There is a connection.

That connection is called a **Relationship**

Entities in a database do not exist independently. They are connected with one another through relationships.
The ER Model uses relationships to represent how entities interact.

---

# Relationship

A Relationship is an association between two or more entities.
A relationship tells us how entities are connected.

Examples:

- Student enrolls in Course
- Customer places Order

---

**Memory Trick**

> Entity = Person Relationship = Verb

---

# Degree of Relationship

## Unary Relationship

One entity is related to itself.

Example:

Employee manages Employee.
Same entity.

---

## Binary Relationship

Two entities participate.

Example:

Student enrolls in Course.
This is the most common relationship.

---

## Ternary Relationship

Three entities participate.

Example:

Doctor prescribes Medicine to Patient.

---

# Cardinality

Cardinality specifies how many instances of one entity can be associated with another.

---

## One-to-One (1:1)

Example:

Person -------- Passport
1 1
Every person has exactly one passport.
Every passport belongs to exactly one person.

---

## One-to-Many (1:M)

Example:

Teacher → Students

One teacher teaches many students.
Each student has one class teacher.

---

## Many-to-One (M:1)

Example:

Students → Department
Many students belong to one department.

---

## Many-to-Many (M:N)

Example:

Students-----Courses

One student can study:

- DBMS
- AI
- Cloud Computing

One course can have:

- Pablo
- Alice
- Bob

Many-to-Many relationships are implemented using a Junction (Bridge) Table.

---

# Participation

## Total Participation

Every entity must participate in the relationship.

Example:

Every Student must have a USN.

---

## Partial Participation

Participation is optional.

Example:

Only some teachers are HODs.
Not all the teachers can become HODs.

---

# Real World Example

We daily use **Youtube** for entertainment, to gain knowledge and learn.

What are the entities?

we identify the objects inside YouTube.
For example:

- User
- Channel
- Video
- Comment

**Relationship 1**
User ---- Watches ---- Video

Can one user watch many videos?
Yes.

Can one video be watched by many users?
Yes.

Therefore:
M:N

**Relationship 2**
User ---- Owns ---- Channel

One user can own multiple channels.
One channel belongs to one user.

Therefore:
1:M

---

# Summary

- Relationship connects entities.
- Relationship names are usually verbs.
- Binary relationships are the most common.
- Many-to-Many relationships require a Junction Table.
- Cardinality defines how many entities can participate.

---
