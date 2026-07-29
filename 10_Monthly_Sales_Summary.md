# Question 10 - Find Monthly Sales Summary

**Difficulty:** Easy

## Problem Statement

Write an SQL query to calculate the total sales for each month.

### Orders

| OrderID | OrderDate | Amount |
|---------|------------|--------|
| 101 | 2025-01-10 | 500 |
| 102 | 2025-01-15 | 700 |
| 103 | 2025-02-05 | 600 |
| 104 | 2025-02-18 | 900 |
| 105 | 2025-03-08 | 800 |

### Expected Output

| Month | TotalSales |
|-------|------------|
| 1 | 1200 |
| 2 | 1500 |
| 3 | 800 |

---

## Solution

```sql
SELECT MONTH(OrderDate) AS Month,
       SUM(Amount) AS TotalSales
FROM Orders
GROUP BY MONTH(OrderDate)
ORDER BY Month;
```

---

## Notes

- Uses `SUM()` and `GROUP BY`.
- `MONTH()` extracts the month from a date.
- `ORDER BY` sorts the output chronologically.
