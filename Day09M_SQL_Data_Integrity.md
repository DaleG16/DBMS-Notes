# Data Integrity

## Introduction

Data integrity in a database ensures that stored data remains accurate, consistent, valid, and reliable throughout its lifecycle.<br>
It prevents corrupt, duplicate, or broken entries from entering or persisting in the system.

----
## Main Types of Data Integrity

1. **Physical integrity**: Protects data as it is stored and retrieved from hardware, guarding against power outages, storage corruption, crashes, and disasters.<br>
2. **Logical integrity**: Keeps data accurate and meaningful within its structure and relationships. It includes:

i) **Entity integrity**: Ensures every table has a primary key with unique, non-NULL values so each row is uniquely identifiable.<br>
ii) **Referential Integrity**: Ensures foreign key values match an existing primary key in a related table (or are NULL where allowed).<br>
iii) **Domain Integrity**:Restricts column values to valid data types, formats, lengths, or ranges (such as NOT NULL, CHECK, or DEFAULT rules).
