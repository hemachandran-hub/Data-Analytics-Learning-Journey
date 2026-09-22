# Data Analytics Learning Log

Documenting my daily progress as I learn data analytics — coming from a background in the healthcare industry.

---

## Day 1 - SQL Basics: WHERE, ORDER BY, UPDATE, DELETE

```sql
-- Filtering rows
SELECT * FROM customer WHERE Country = 'Portugal';

-- Filtering with multiple conditions
SELECT * FROM customer WHERE Gender = 'Male' AND Country = 'China';

-- Pattern matching
SELECT * FROM customer WHERE Email LIKE '%gmail%';

-- Sorting results
SELECT * FROM customer ORDER BY FirstName ASC;
SELECT * FROM customer ORDER BY CustomerID DESC LIMIT 5;

-- Sorting a text-based date column correctly
SELECT * FROM customer
ORDER BY STR_TO_DATE(DateOfBirth, '%m/%d/%Y') DESC;

-- Updating records safely
UPDATE customer SET Country = 'India' WHERE CustomerID = 1;

-- Deleting specific records
DELETE FROM customer WHERE CustomerID = 999;
```

**What I learned:** WHERE always needs to come with UPDATE/DELETE to avoid affecting every row. LIKE with % wildcards is needed for partial text matches. Dates stored as text need STR_TO_DATE() to sort correctly.

---

## Day 2 - GROUP BY

```sql
-- Using GROUP BY to see what cities are there
SELECT City
FROM employees
GROUP BY City;

-- Using GROUP BY to see what genders are there
SELECT Gender
FROM employees
GROUP BY Gender;

-- Using GROUP BY on two columns together
SELECT Department, City
FROM employees
GROUP BY Department, City;
```

**What I learned:** GROUP BY alone shows unique values, but doesn't count anything by itself. To count how many rows fall into each group, COUNT() needs to be added:

```sql
SELECT City, COUNT(*) AS total_employees
FROM employees
GROUP BY City;
```

## Day 3 - More Practice: Multiple Conditions & Pattern Matching

```sql
-- Filter method
SELECT * FROM customer
WHERE Country = 'China';

-- Ordering method
SELECT * FROM customer
ORDER BY FirstName ASC;

-- Update method
UPDATE customer
SET Gender = 'Female'
WHERE CustomerID = 262;

-- Delete method
DELETE FROM customer
WHERE CustomerID = 1;

-- Descending order
SELECT * FROM customer
ORDER BY CustomerID DESC;

-- Sort by country
SELECT * FROM customer
ORDER BY Country;

-- Multiple conditions with AND
SELECT * FROM customer
WHERE Gender = 'Male' AND Country = 'China';

-- Pattern matching with LIKE
SELECT * FROM customer
WHERE Email LIKE '%gmail%';

-- Selecting specific columns
SELECT CustomerID, FirstName, LastName, Country, Address
FROM customer
ORDER BY CustomerID DESC;

-- Update address
UPDATE customer
SET Address = 'Dunning Pass'
WHERE CustomerID = 2;
```

**What I learned:** Practiced combining WHERE with AND for multiple conditions, LIKE with % wildcards for partial text search, and selecting specific columns instead of using * for cleaner output.

---

## Day 4 - LIMIT and OFFSET

```sql
-- Get only the first 10 rows
SELECT * FROM customer
LIMIT 10;

-- Skip the first 10 rows, then get the next 10
SELECT * FROM customer
LIMIT 10 OFFSET 10;

-- Get the 5 customers with the highest CustomerID
SELECT * FROM customer
ORDER BY CustomerID DESC
LIMIT 5;
```

**What I learned:** LIMIT controls how many rows are returned, OFFSET controls where it starts counting from. Together they're useful for pagination — like showing "page 2" of results by skipping the first page's rows.
