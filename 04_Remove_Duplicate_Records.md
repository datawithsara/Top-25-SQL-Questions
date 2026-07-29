# Question 04 - Remove Duplicate Records

**Difficulty:** Medium

## Problem Statement

Write an SQL query to remove duplicate records while keeping only the first occurrence.

### Employees

| EmployeeID | Name | Email |
|------------|------|---------------------|
| 1 | Sara | sara@gmail.com |
| 2 | John | john@gmail.com |
| 3 | Alex | sara@gmail.com |
| 4 | Emma | emma@gmail.com |
| 5 | David | john@gmail.com |

### Expected Output

| EmployeeID | Name | Email |
|------------|------|---------------------|
| 1 | Sara | sara@gmail.com |
| 2 | John | john@gmail.com |
| 4 | Emma | emma@gmail.com |

---

## Solution

```sql
WITH DuplicateRecords AS (
    SELECT *,
           ROW_NUMBER() OVER (
               PARTITION BY Email
               ORDER BY EmployeeID
           ) AS rn
    FROM Employees
)
DELETE FROM DuplicateRecords
WHERE rn > 1;
```

---

## Notes

- Uses `ROW_NUMBER()` to identify duplicate rows.
- Keeps the first occurrence (`rn = 1`).
- Deletes all remaining duplicate records.
