# Question 16 - Find the Latest Record for Each Customer

**Difficulty:** Medium

## Problem Statement

Write an SQL query to find the latest order placed by each customer.

### Orders

| OrderID | CustomerID | OrderDate |
|---------|------------|-----------|
|101|1|2025-01-10|
|102|1|2025-01-20|
|103|2|2025-01-15|

### Expected Output

| OrderID | CustomerID | OrderDate |
|---------|------------|-----------|
|102|1|2025-01-20|
|103|2|2025-01-15|

---

## Solution

```sql
SELECT *
FROM (
    SELECT *,
           ROW_NUMBER() OVER(
               PARTITION BY CustomerID
               ORDER BY OrderDate DESC
           ) AS rn
    FROM Orders
) t
WHERE rn = 1;
```

---

## Notes

- Uses `ROW_NUMBER()`.
- Returns the latest record for every customer.
