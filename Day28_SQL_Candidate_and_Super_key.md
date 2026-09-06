# Candidate Key & Super Key

## Introduction

**Super Key = Can uniquely identify** (It may contain extra attributes.)
**Candidate Key = Can uniquely identify + Can't remove anything**

---

## Understanding

<br>

| StudentID | Name   | Age |
| --------- | ------ | --- |
| 101       | Leo    | 19  |
| 102       | Sophia | 21  |
| 103       | Marcus | 20  |
| 104       | Emma   | 19  |
| 105       | Pablo  | 20  |

StudentID → identifies you ✅ (Nothing extra)
StudentID + Name → also identifies you ✅ (extra attributes)
StudentID + Name + Age → also identifies you ✅ (extra attributes)

<br>

But ask:

`"Can I remove something and still identify the student?"`

1. For StudentID + Name:

**Remove Name**, still with StudentID you can uniquely identify a row.

It can still identify after removing

So not a candidate key.

2. For StudentID:

**Nothing to remove** and with studentID you can uniquely identify a row.

---

### Deeper Understanding

| StudentID | Name   | Age |
| --------- | ------ | --- |
| 101       | Leo    | 19  |
| 102       | Sophia | 21  |
| 103       | Marcus | 20  |
| 104       | Emma   | 19  |
| 101       | Leo    | 20  |

<br>

Two different students named Leo.

1. StudentID 101 appears twice.<br>
   One StudentID corresponds to two different rows - NOT UNIQUE

2. What about StudentID + Name?

   101 + Leo and still appears twice.<br>
   NOT a key either!

3. What about StudentID + Age? (Can't remove Age, if did cant uniquely identify)

   101 + 19<br>
   101 + 20

   CANDIDATE KEY

<br>

`Every candidate key is a super key.`

`But not every super key is a candidate key.`

`Candidate Key ⊂ Super Keys`

---

## Summary

Whenever you see a possible key, ask:

"Can I remove anything?"

If NO → Candidate Key (Unique+minimal)
If YES → Super Key (Unique)
