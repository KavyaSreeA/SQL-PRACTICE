# SQL-PRACTICE
# SQL Learning Log — INSERT • NULL • UPDATE

This repository log documents progress, mistakes, corrections, and key learning insights.

---

## 📘 Part 1 — Mistake Analysis Summary

SQL Learning Progress — Mistake Analysis (INSERT • NULL • UPDATE)

This document records my mistake patterns, corrections, and lessons
learned while practicing SQL data modification statements. The goal is
to build clean query habits and avoid real‑world data loss issues.

Topics Covered

-   INSERT INTO
-   NULL handling
-   IS NULL / IS NOT NULL
-   UPDATE (single + multiple rows)
-   UPDATE with conditions
-   Multi‑row INSERT
-   Auto‑increment awareness

------------------------------------------------------------------------

1) INSERT Statement — Mistake Patterns & Fixes

Mistake: Missing INTO and table name

Wrong: INSERT CustomerName, City, Country VALUES(…);

Correct: INSERT INTO Customers (CustomerName, City, Country) VALUES (…);

Lesson: Always include: - INTO - table name - column list inside
parentheses

Mistake: Inserting values without specifying columns

Wrong: INSERT INTO Customers VALUES (…);

Risk: * Breaks if table structure changes * Fails if auto‑increment
column exists

Correct (safe): INSERT INTO Customers (CustomerName, ContactName,
Address, City, PostalCode, Country) VALUES (…);

Lesson: ALWAYS specify column names in INSERT.

Mistake: Mixing SELECT + INSERT syntax

Wrong: SELECT CustomerName, Country VALUES(…);

Correct: INSERT INTO Customers (CustomerName, Country) VALUES (…);

Lesson: INSERT adds rows — SELECT retrieves rows.

Mistake: Multi‑row insert without column names

Correct form: INSERT INTO Customers (CustomerName, ContactName, Address,
City, PostalCode, Country) VALUES (…), (…);

Lesson: Multi‑row insert uses same column list for all rows.

Auto‑Increment Understanding

CustomerID was NOT manually inserted — correct behavior.

Rule: Auto‑increment ID is generated automatically. Do NOT insert values
into it.

------------------------------------------------------------------------

2) NULL & IS NULL — Mistake Patterns & Fixes

Core Rule: NULL cannot be compared using = or <>

Wrong: WHERE Address = NULL;

Correct: WHERE Address IS NULL;

Wrong: WHERE ContactName <> NULL;

Correct: WHERE ContactName IS NOT NULL;

Mistake: Missing FROM clause

Wrong: SELECT Customers WHERE Address IS NULL;

Correct: SELECT * FROM Customers WHERE Address IS NULL;

Lesson: SELECT requires: SELECT columns FROM table WHERE condition;

NULL Concept Lessons

-   NULL means “no value stored”
-   NOT the same as:
    -   zero
    -   empty string
    -   spaces

------------------------------------------------------------------------

3) UPDATE Statement — Mistake Patterns & Fixes

Mistake: Semicolon before WHERE

Wrong: UPDATE Customers SET ContactName = ‘Emma’; WHERE CustomerID = 3;

Effect: First line updates ALL rows

Correct: UPDATE Customers SET ContactName = ‘Emma’ WHERE CustomerID = 3;

Lesson: Never end UPDATE before WHERE.

Mistake: Updating without table name

Wrong: UPDATE CustomerName SET …

Correct: UPDATE Customers SET CustomerName = …

Mistake: Updating ALL rows accidentally

UPDATE Customers SET City = ‘Rome’;

Effect: Every record becomes Rome.

Lesson: Always confirm WHERE before UPDATE.

Safe Workflow Habit

1)  Run SELECT with same WHERE
2)  Verify affected rows
3)  Then run UPDATE

Mistake: Wrong field meaning change

Changing Country to a City value is logically invalid.

Lesson: SQL will not protect meaning — developer must.

UPDATE Multiple Columns — Correct Pattern

UPDATE Customers SET City = ‘Madrid’, ContactName = ‘Carlos Ruiz’ WHERE
Country = ‘Spain’ AND CustomerID > 10;

UPDATE with NULL Condition

UPDATE Customers SET PostalCode = ‘00000’ WHERE PostalCode IS NULL;

------------------------------------------------------------------------

Key Takeaways

✔ Always specify columns in INSERT
✔ Use IS NULL / IS NOT NULL
✔ UPDATE requires table name
✔ Double‑check WHERE before updating
✔ Avoid accidental full‑table updates
✔ Think about real‑world data meaning

Learning Mindset Reflection

Mistakes were logic‑based, not guess‑based. Every correction improved: *
syntax discipline * reasoning ability * awareness of data safety

This progress helps build strong SQL foundations for future topics
like: * DELETE / TRUNCATE * ORDER BY * GROUP BY & Aggregations * JOINs *
Transactions & rollback safety

------------------------------------------------------------------------

End of Mistake Analysis — Version 1


---

## 📝 Part 2 — My Answer Mistakes (Reviewed & Corrected)

Mistakes Made in Practice Answers — Detailed Review (INSERT • NULL • UPDATE)

This file documents ONLY the mistakes from my submitted answers, with
the correct SQL form and the lesson behind each one.

Purpose: To track recurring pattern‑errors and prevent repeating them in
future queries.

------------------------------------------------------------------------

INSERT Statement — My Mistakes

1)  Missing INTO + table name

Wrong: INSERT CustomerName,City,Country VALUES(…);

Correct: INSERT INTO Customers (CustomerName, City, Country) VALUES (…);

Lesson: INSERT must always contain: * INTO * table name * column list in
( )

2)  Insert without column list (unsafe)

Wrong: INSERT INTO Customers VALUES (…);

Correct: INSERT INTO Customers (CustomerName, ContactName, Address,
City, PostalCode, Country) VALUES (…);

Lesson: Always specify column names to avoid column‑order issues.

3)  Multi‑row INSERT without column list

Correct approach should be: INSERT INTO Customers (…columns…) VALUES
(…), (…);

Lesson: All rows must share the same defined column order.

4)  Mixed SELECT + INSERT syntax

Wrong: SELECT CustomerName , Country VALUES(…);

Correct: INSERT INTO Customers (CustomerName, Country) VALUES (…);

Lesson: INSERT adds rows — SELECT retrieves rows.

5)  Auto‑Increment misunderstanding

CustomerID was not inserted manually — this is correct.

Lesson: Auto‑increment keys are generated automatically.

------------------------------------------------------------------------

NULL / IS NULL Mistakes

6)  Missing FROM clause

Wrong: SELECT Customers WHERE Address IS NULL;

Correct: SELECT * FROM Customers WHERE Address IS NULL;

Lesson: SELECT requires: SELECT columns FROM table WHERE condition;

7)  Same issue for IS NOT NULL

Wrong: SELECT Customers WHERE ContactName IS NOT NULL;

Correct: SELECT * FROM Customers WHERE ContactName IS NOT NULL;

8)  NULL insert confusion

Wrong: SELECT CustomerName , Country VALUES(…);

Correct: INSERT INTO Customers (CustomerName, Country) VALUES (‘Green
Farm’, ‘India’);

Lesson: INSERT creates rows — SELECT cannot insert.

------------------------------------------------------------------------

UPDATE Statement Mistakes

9)  Semicolon before WHERE (dangerous)

Wrong: UPDATE Customers SET ContactName=‘Emma Watson’; WHERE
CustomerID=3;

Effect: First statement updates ALL rows

Correct: UPDATE Customers SET ContactName=‘Emma Watson’ WHERE
CustomerID=3;

Lesson: Never end UPDATE before WHERE.

10) UPDATE without table name

Wrong: UPDATE CustomerName SET …

Correct: UPDATE Customers SET CustomerName = …;

11) Incorrect UPDATE syntax with columns after UPDATE

Wrong: UPDATE City , ContactName SET …

Correct: UPDATE Customers SET City=‘Madrid’, ContactName=‘Carlos Ruiz’
WHERE Country=‘Spain’ AND CustomerID>10;

12) Updating field meaning incorrectly

Changing Country -> City value is logically invalid.

Lesson: SQL will not protect semantic meaning — I must.

13) Correct use of UPDATE + IS NULL

UPDATE Customers SET PostalCode=‘00000’ WHERE PostalCode IS NULL;

Lesson: IS NULL must be used for NULL comparison.

------------------------------------------------------------------------

Key Improvement Goals

✔ Always specify column list in INSERT
✔ Do not place semicolon before WHERE
✔ UPDATE must reference table name
✔ Avoid unsafe full‑table updates
✔ Run SELECT before UPDATE to verify rows
✔ Think about real‑world data meaning

------------------------------------------------------------------------

End of Mistake Review — Version 1.1


---

## 🎯 Purpose of this Learning Log

This log is meant to:

* Track learning progress
* Maintain correction history
* Prevent repeating mistakes
* Build disciplined SQL habits
* Serve as a personal reference

Future logs will include:

* DELETE / TRUNCATE
* ORDER BY
* LIMIT / TOP
* GROUP BY & Aggregations
* JOINS
* Query optimization & real‑world case study practice

