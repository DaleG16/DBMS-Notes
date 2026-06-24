# Day 1 - Introduction to DBMS

## What is Data?

Data refers to raw unprocessed facts.


Example:

Rahul, 101, 21, AIML

These are pieces of data without much meaning.

---

## What is Information?

Information is processed data that provides meaning.

Example:

"Rahul is a 21-year-old AIML student."

Data + Processing = Information

---

## Problems with File Systems

### 1. Data Redundancy

The same data may be stored multiple times.

Example:

A student's phone number stored in:

- Attendance File
- Fees File
- Exam File

This wastes storage.

---

### 2. Data Inconsistency

If one copy is updated and another is not updated, conflicting information occurs.

Example: Consider a student record

Attendance File → 9008965190

Fees File → 8976543123
Creates conflict.

---

### 3. Difficult Data Retrieval

Searching large files becomes slow and inefficient.

---

### 4. Security Issues

Unauthorized users may access sensitive information.

Examples:

- Marks
- Fees
- Personal Details
If a student access and change the information it will cause a big problem.

---

### 5. Data Loss

System crashes or file corruption may result in loss of data.

---


## What is a Database?

A Database is an organized collection of related data.

Example:

| USN | Name  | Branch 
|-----|------ |-------
| 101 | Rahul | AIML 
| 102 | Priya | CSE 

The stored records themselves form the database.

---

## What is DBMS?

DBMS stands for Database Management System.

It is software used to store, organize, retrieve, update and manage data efficiently.

Examples:

- MySQL
- PostgreSQL
- Oracle

---

## Database vs DBMS

### Database

The actual stored data.

Example:

Student records stored in tables.

### DBMS

The software that manages the database.

Example:

MySQL

---

## SQL vs DBMS

SQL is a language used to communicate with a DBMS.

Example:

- MySQL → DBMS
- SQL → Language


---

## Advantages of DBMS

1. Reduces Data Redundancy
2. Improves Data Consistency
3. Provides Better Security
4. Supports Multiple Users
5. Faster Data Retrieval
6. Backup and Recovery Support

---

## Real World Applications

- Instagram
- Amazon
- Banking Systems
- Hospital Management Systems

---

## Key Takeaways:

- Data = Raw facts
- Information = Processed data
- Database = Collection of organized data
- DBMS = Software that manages databases
- SQL = Language used to communicate with DBMS
- DBMS solves problems present in traditional file systems