# Question 18 - Pivot Rows into Columns

**Difficulty:** Hard

## Problem Statement

Write an SQL query to convert rows into columns.

### Sales

| Quarter | Sales |
|---------|-------|
| Q1 | 100 |
| Q2 | 150 |
| Q3 | 200 |
| Q4 | 250 |

### Expected Output

| Q1 | Q2 | Q3 | Q4 |
|----|----|----|----|
| 100 | 150 | 200 | 250 |

---

## Solution

```sql
SELECT
    SUM(CASE WHEN Quarter = 'Q1' THEN Sales END) AS Q1,
    SUM(CASE WHEN Quarter = 'Q2' THEN Sales END) AS Q2,
    SUM(CASE WHEN Quarter = 'Q3' THEN Sales END) AS Q3,
    SUM(CASE WHEN Quarter = 'Q4' THEN Sales END) AS Q4
FROM Sales;
```

---

## Alternative (SQL Server)

```sql
SELECT *
FROM Sales
PIVOT (
    SUM(Sales)
    FOR Quarter IN ([Q1],[Q2],[Q3],[Q4])
) p;
```
## Notes

- Uses `CASE WHEN` for conditional aggregation.
- `SUM()` converts row values into separate columns.
- Works across most SQL databases.
- `PIVOT` can also be used in SQL Server.
