# Day 6 - Strong Entity & Weak Entity

## Introduction

Entities in a database can either exist **independently** or **depend on another entity** for identification.

Based on this, entities are classified as Strong Entities and Weak Entities.

---

# Strong Entity

A Strong Entity is an entity that has its own Primary Key and can exist independently.

Example:

- Student
  USN : 1AI22AI001 <br>
  Name : Pablo

Can we identify this student?<br>
Yes.

The USN uniquely identifies the student.

- Employee
- Book
- Customer

Each has its own ID

### Visual Representation

Strong Entity represented as 'Rectangle' <br>
![Strong Entity](images/entity.png)

---

# Weak Entity

A Weak Entity is an entity that cannot be uniquely identified using its own attributes.<br>
It depends on a Strong Entity.

Examples:

- Dependent
- Order Item

### Visual Representation

Weak Entity represented as 'Double Rectangle' <br>
![Weak Entity](images/weak_entity.png)

---

# Partial Key

A Partial Key is an attribute that partially identifies a Weak Entity.

It becomes unique only when combined with the Primary Key of the Strong Entity.

Example:

EmployeeID = 101<br>
Dependent Name = Father

Together they become unique.

---

# Identifying Relationship

An Identifying Relationship connects a Weak Entity to its Strong Entity.

Examples:

- Customer -> Borrows
- Order → Order Item

### Visual Representation

Represented as 'Double Diamond'<br>
![Identification](/images/Identification.png)

---

# Difference Between Strong and Weak Entity

| Strong Entity           | Weak Entity                |
| ----------------------- | -------------------------- |
| Has its own Primary Key | Depends on another entity  |
| Exists independently    | Cannot exist independently |
| Easily identified       | Requires Strong Entity     |

---

# Real World Example

![Customer_borrows_loan](/images/Real_world.png)

---

# Summary

- Strong Entity = Independent
- Weak Entity = Dependent
- Partial Key = Partially identifies a Weak Entity
- Identifying Relationship = Connects Strong and Weak Entities
