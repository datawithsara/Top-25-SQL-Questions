# Question 19 - Unpivot Columns into Rows

**Difficulty:** Hard

## Problem Statement

Write an SQL query to convert columns into rows.

### Sales

| Q1 | Q2 | Q3 | Q4 |
|----|----|----|----|
| 100 | 150 | 200 | 250 |

### Expected Output

| Quarter | Sales |
|---------|-------|
| Q1 | 100 |
| Q2 | 150 |
| Q3 | 200 |
| Q4 | 250 |

---

## Solution

```sql
SELECT 'Q1' AS Quarter, Q1 AS Sales
FROM Sales

UNION ALL

SELECT 'Q2', Q2
FROM Sales

UNION ALL

SELECT 'Q3', Q3
FROM Sales

UNION ALL

SELECT 'Q4', Q4
FROM Sales;
```

## Alternative (SQL Server)
```sql
SELECT Quarter, Sales
FROM Sales
UNPIVOT (
    Sales
    FOR Quarter IN (Q1,Q2,Q3,Q4)
) u;
```
---

## Notes

- Uses `UNION ALL` to convert columns into rows.
- Works across most SQL databases.
- `UNPIVOT` is available in SQL Server as an alternative.
