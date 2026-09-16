# Day 31 — ACID Properties

## Introduction

ACID properties are the four fundamental properties that make database transactions reliable and safe.

**ACID = Atomicity, Consistency, Isolation, Durability**

They ensure that `transactions behave correctly even when failures occur` or multiple transactions execute at the same time.

---

## 1. Atomicity

**Atomicity = All or Nothing**

Either:

- All required operations succeed <br>
  OR
- None of them should take effect.

### Example — Bank Transfer

Suppose Pablo transfers ₹2,000 to Alice.

The transaction contains:

```text
1. Deduct ₹2,000 from Pablo
2. Add ₹2,000 to Alice
```

If the deduction succeeds but the credit fails:

```text
Debit      → SUCCESS
Credit     → FAILURE
                 ↓
              ROLLBACK
                 ↓
Both changes undone
```

**Atomicity prevents the transaction from being left partially completed.**

---

## 2. Consistency

**Consistency = Rules Remain Valid**

Consistency ensures that a transaction takes the database from one valid state to another valid state while preserving database constraints and rules.

### Example

Suppose a database has the rule:

```text
Account Balance ≥ 0
```

Before the transaction:

```text
Pablo = ₹5,000
```

**Case 1:** After transferring ₹2,000:

```text
Pablo = ₹3,000
```

The database is still in a valid state.

**Case 2:** <br>

```text
Pablo = ₹5,000
```

Transaction tries to withdraw ₹1,500.

If the database allows: Pablo = `-₹500 `

The database has violated its rule. Consistency failure

Consistency also works with constraints such as:

- PRIMARY KEY
- FOREIGN KEY
- UNIQUE
- CHECK

---

## 3. Isolation

**Isolation = Concurrent Transactions Should Not Improperly Interfere**

Multiple transactions can execute concurrently.

Isolation ensures that one transaction does not improperly interfere with another transaction or expose inappropriate intermediate results.

### Example

Suppose:

```text
Pablo's Balance = ₹10,000
```

At the same time:

```text
Transaction T1 → Withdraw ₹6,000
Transaction T2 → Withdraw ₹5,000
```

If they interfere incorrectly, both might see: Balance = ₹10,000 and both may think they can withdraw.

That could produce a completely wrong result.

If both transactions incorrectly read the same old balance and proceed without proper isolation, the final result can be incorrect.

Isolation provides controlled concurrent execution.

---

## 4. Durability

**Durability = Committed Changes Survive Failures**

Once a transaction has successfully committed, its changes should remain saved even if the system crashes afterward.

### Example

```sql
COMMIT;
```

Then:

```text
💥 Server Crash
      ↓
Database Restarts
      ↓
Committed changes still exist
```

The DBMS uses mechanisms such as logging and recovery to provide durability.

---

## Atomicity vs Isolation

These two are commonly confused.

### Atomicity

Focuses on **one transaction**:

### Isolation

Focuses on **multiple concurrent transactions**:

---

## Summary

- ACID describes the fundamental properties of reliable transactions.
- **Atomicity** ensures all-or-nothing execution.
- **Consistency** ensures database rules remain satisfied.
- **Isolation** controls the interaction between concurrent transactions.
- **Durability** ensures committed changes survive failures.
