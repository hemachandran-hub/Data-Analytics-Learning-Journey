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
