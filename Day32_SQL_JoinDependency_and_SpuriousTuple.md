# Day 32 - Join Dependency and Spurious Tuple

<br>

## Join Dependency

A join dependency means:

A table can be decomposed into multiple smaller tables and then reconstructed exactly by joining those tables.

Ex:

| Supplier | Part | Project |
| -------- | ---- | ------- |
| S1       | P1   | J1      |
| S1       | P2   | J1      |
| S2       | P1   | J1      |

We could potentially represent the relationships separately:

**Relationship 1: Supplier-Part**

| Supplier | Part |
| -------- | ---- |
| S1       | P1   |
| S1       | P2   |
| S2       | P1   |

**Relationship 2: Suplier-Project**

| Supplier | Project |
| -------- | ------- |
| S1       | J1      |
| S2       | J1      |

**Relationship 3: Part-Project**

| Part | Project |
| ---- | ------- |
| P1   | J1      |
| P2   | J1      |

If you try to reconstruct these smaller tables then the final table would be an Original Table.

> Note: If the decomposition doesn't lose information and the original relation can be reconstructed correctly, we have a valid join dependency.

---

## Spurious Tuples

Spurious Tuples are those rows(unwanted) in a table, which occur as a result of joining two tables in the wrong manner.

They are extra tuples (rows) that might not be required.

Ex:

![Spurious_1](/images/Spurious_1.png)

Let R be a Relation, and R1 and R2 be relations that we get after decomposing R.

<br>

![Spurious_2](/images/Spurious_2.png)

After performing the join operation of relations R1 and R2 we do not get back the original relation R.

---

### References

Spurious Tuple - GeeksforGeeks (https://www.geeksforgeeks.org/dbms/spurious-tuples-in-dbms/)
