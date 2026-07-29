# Question 15 - Find Users with 3 or More Consecutive Login Days

**Difficulty:** Hard

## Problem Statement

Write an SQL query to find users who have logged in for **3 or more consecutive days**.

### Logins

| UserID | LoginDate |
|--------|------------|
| 1 | 2025-01-01 |
| 1 | 2025-01-02 |
| 1 | 2025-01-03 |
| 2 | 2025-01-01 |
| 2 | 2025-01-03 |
| 2 | 2025-01-04 |

### Expected Output

| UserID |
|--------|
| 1 |

---

## Solution

```sql
WITH ConsecutiveLogins AS (
    SELECT
        UserID,
        LoginDate,
        DATE_SUB(
            LoginDate,
            INTERVAL ROW_NUMBER() OVER (
                PARTITION BY UserID
                ORDER BY LoginDate
            ) DAY
        ) AS grp
    FROM Logins
)

SELECT UserID
FROM ConsecutiveLogins
GROUP BY UserID, grp
HAVING COUNT(*) >= 3;
```

---

## Notes

- Uses `ROW_NUMBER()` to identify consecutive dates.
- Groups consecutive login dates using a calculated key.
- Returns users who logged in for **3 or more consecutive days**.
