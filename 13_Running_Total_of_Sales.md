# Question 13 - Calculate Running Total of Sales

**Difficulty:** Medium

## Problem Statement

Write an SQL query to calculate the running total of sales.

### Orders

| OrderID | OrderDate | Amount |
|---------|-----------|--------|
|101|2025-01-01|500|
|102|2025-01-02|700|
|103|2025-01-03|600|

### Expected Output

| OrderID | Amount | RunningTotal |
|---------|--------|--------------|
|101|500|500|
|102|700|1200|
|103|600|1800|

---

## Solution

```sql
SELECT OrderID,
       Amount,
       SUM(Amount) OVER(
           ORDER BY OrderDate
       ) AS RunningTotal
FROM Orders;
```

---

## Notes

- Uses a Window Function.
- Calculates cumulative totals.
