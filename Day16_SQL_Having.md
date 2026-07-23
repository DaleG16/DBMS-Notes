# Day 16 - HAVING

## Introduction

Consider the Student Table:<br>
![Student list](/images/Student_list_marks.png)

Suppose the principal asks:<br>
"Show only the branches whose average marks are greater than 85."

Can we use:<br>
WHERE AVG(Marks) > 85

❌ No.

Why?

Because **WHERE** works **before the groups are created**.

But here average marks refers to after we do GROUP BY.

---

## HAVING

The HAVING clause filters groups created by the GROUP BY clause.

Example:

```sql
SELECT Branch, AVG(Marks)
FROM Student
GROUP BY Branch
HAVING AVG(Marks) > 85;
```

Output:<br>
![Having Average](/images/Having_Avg.png)

---

## Difference Between WHERE and HAVING

| WHERE                                   | HAVING                                 |
| --------------------------------------- | -------------------------------------- |
| Filters rows                            | Filters groups                         |
| Used before GROUP BY                    | Used after GROUP BY                    |
| Cannot use aggregate functions directly | Commonly used with aggregate functions |

---

## Combining WHERE and HAVING

Find branches whose average marks are above 85, but consider only students older than 20.

```sql
SELECT Branch, AVG(Marks)
FROM Student
WHERE Age > 20
GROUP BY Branch
HAVING AVG(Marks) > 80;
```

Read it in order:

1. Filter rows (WHERE)
2. Create groups (GROUP BY)
3. Filter groups (HAVING)

This order is very important.

Output:<br>
**Step 1:** WHERE Age > 20

![Step1 Where](/images/Step1_Where.png)

**Step 2:** GROUP BY Branch

![Step2 Branch](/images/Step2_Branch.png)

**Step 3:** HAVING AVG(Marks) > 80

First, SQL computes the averages:<br>
![Step3 ](/images/Step3_Avg.png)

> Note: Step 1 to Step 3 are calculated internally.

Actual Display of the Output:

![Having](/images/Having.png)

---

## Summary

- WHERE filters rows.
- HAVING filters groups.
- WHERE executes before GROUP BY.
- HAVING executes after GROUP BY.
