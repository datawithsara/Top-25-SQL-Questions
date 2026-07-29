# Question 23 - Generate Numbers from 1 to 10 Using a Recursive CTE

**Difficulty:** Hard

## Problem Statement

Write an SQL query to generate numbers from 1 to 10 using a Recursive CTE.

### Expected Output

| Number |
|--------|
| 1 |
| 2 |
| 3 |
| 4 |
| 5 |
| 6 |
| 7 |
| 8 |
| 9 |
| 10 |

---

## Solution

```sql
WITH RECURSIVE Numbers AS (
    SELECT 1 AS Number

    UNION ALL

    SELECT Number + 1
    FROM Numbers
    WHERE Number < 10
)

SELECT *
FROM Numbers;
```

---

## Notes

- Uses a Recursive CTE.
- Generates sequential numbers.
- Useful for recursion-based SQL problems.
