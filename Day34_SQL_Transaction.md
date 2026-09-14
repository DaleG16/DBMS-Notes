# Day 31 — Transactions

## Introduction

A **Transaction** is a sequence of one or more database operations that together perform **one logical task**.

---

## Concept Explanation

### What is a Transaction?

Consider a bank transfer:

- Pablo has ₹10,000
- Alice has ₹5,000
- Pablo transfers ₹2,000 to Alice

The transaction involves two important operations:

1. Deduct ₹2,000 from Pablo
2. Add ₹2,000 to Alice

These operations together form **one logical transaction**.

If the deduction succeeds but the addition fails, the database could become inconsistent.

Therefore, the DBMS must handle both operations as one unit.

---

## COMMIT

`COMMIT` permanently saves the changes made by the current transaction.

```sql
COMMIT;
```

Example:

```sql
BEGIN;

UPDATE Account
SET Balance = Balance - 2000
WHERE AccountID = 101;

UPDATE Account
SET Balance = Balance + 2000
WHERE AccountID = 102;

COMMIT;
```

If all required operations succeed, the transaction can be committed.

---

## ROLLBACK

What if something goes wrong?

`ROLLBACK` cancels uncommitted changes made by the current transaction.

```sql
ROLLBACK;
```

Example:

```sql
BEGIN;

UPDATE Account
SET Balance = Balance - 2000
WHERE AccountID = 101;

UPDATE Account
SET Balance = Balance + 2000
WHERE AccountID = 102;

ROLLBACK;
```

The changes are undone instead of being permanently saved.

---

## Why Transactions Are Important

Without proper transaction handling, a failure between related operations can leave the database in an invalid state.

With transaction management:

```text
Debit succeeds
      ↓
Credit fails
      ↓
ROLLBACK
      ↓
Original state restored
```

---

## Transaction States

A transaction can move through different states.

### 1. ACTIVE

The transaction is currently executing its operations.

### 2. PARTIALLY COMMITTED

The final statement has executed successfully, but the transaction has not yet been fully committed.

### 3. COMMITTED

The transaction has successfully completed and its changes are permanently saved.

```text
ACTIVE → PARTIALLY COMMITTED → COMMITTED
```

### 4. FAILED

The transaction cannot continue because of an error or failure.

```text
ACTIVE → FAILED
```

### 5. ABORTED

The transaction has been rolled back and its changes have been undone.<br>
An aborted transaction may be restarted or terminated.

```text
ACTIVE → FAILED → ABORTED
```

---

## Transaction State Diagram

```text
                  ┌──────────────────────┐
                  │        ACTIVE        │
                  └──────────┬───────────┘
                             │
                Last statement successful
                             │
                             ▼
                  ┌──────────────────────┐
                  │ PARTIALLY COMMITTED  │
                  └──────────┬───────────┘
                             │
                           COMMIT
                             │
                             ▼
                  ┌──────────────────────┐
                  │      COMMITTED       │
                  └──────────────────────┘



**In the case of Error:**

                  ┌──────────────────────┐
                  │        ACTIVE        │
                  └──────────┬───────────┘
                             │
                           Error
                             │
                             ▼
                  ┌──────────────────────┐
                  │        FAILED        │
                  └──────────┬───────────┘
                             │
                          ROLLBACK
                             │
                             ▼
                  ┌──────────────────────┐
                  │       ABORTED        │
                  └──────────────────────┘
```

---

## Real-World Example

### ATM Withdrawal

Suppose you withdraw ₹2,000 from an ATM.

The transaction may involve:

1. Verify the account
2. Check available balance
3. Deduct ₹2,000
4. Dispense cash
5. Record the transaction

These operations are logically connected.

If something fails, the DBMS must prevent an incorrect final database state.

---

## Summary

- A transaction is a **logical unit of work**.
- A transaction can contain **one or more database operations**.
- `COMMIT` permanently saves a transaction's changes.
- `ROLLBACK` undoes uncommitted changes.
- Transactions help prevent inconsistent database states.
