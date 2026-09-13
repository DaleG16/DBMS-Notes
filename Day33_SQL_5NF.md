# Day 33 - Fifth Normal Form (5NF)

## Introduction

5NF stands for **Fifth Normal Form** and is also called **Project-Join Normal Form (PJ/NF)**.

5NF mainly deals with **join dependencies**.

---

## Why Do We Need 5NF?

Consider a relationship involving:

- Supplier
- Part
- Project

![Original Table](/images/Supplier_1.png)

Sometimes a three-way relationship can be represented using several smaller relationships.

![Decomposed Table](/images/Supplier_2.png)

The problem is that after decomposing the table and joining the smaller tables back together, the JOIN may create combinations that **did not exist in the original table**.

![Reconstructed Table](/images/Supplier_3.png)

This is where 5NF becomes important.

---

## Why Do Spurious Tuples Appear?

They appear because the `decomposition loses some information` about the original relationship.

---

## 5NF Rule

A relation is in **5NF** if:

> Every non-trivial join dependency is implied by the candidate keys.

For placement understanding:

> **Can this table be decomposed into smaller tables and reconstructed perfectly without creating incorrect combinations?**

---

## Normalization Journey

```text
1NF → Atomic values
2NF → No partial dependency
3NF → No transitive dependency
BCNF → Every determinant must be a superkey
4NF → No problematic multivalued dependency
5NF → No problematic join dependency
```

---

## Summary

- 5NF deals with **join dependencies**.
- A relation may be decomposed into smaller relations.
- Joining the decomposed relations should not produce incorrect information.
- Incorrect rows created after reconstruction are called **spurious tuples**.
- 5NF is stricter than 4NF.
