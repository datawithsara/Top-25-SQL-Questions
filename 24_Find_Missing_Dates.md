# Question 24 - Find Missing Dates

**Difficulty:** Hard

## Problem Statement

Write an SQL query to find missing dates from the Attendance table between '2025-01-01' and '2025-01-07'.

### Attendance

| AttendanceDate |
|----------------|
| 2025-01-01 |
| 2025-01-02 |
| 2025-01-04 |
| 2025-01-06 |
| 2025-01-07 |

### Expected Output

| MissingDate |
|-------------|
| 2025-01-03 |
| 2025-01-05 |

---

## Solution

```sql
WITH RECURSIVE Dates AS (
    SELECT DATE('2025-01-01') AS AttendanceDate

    UNION ALL

    SELECT DATE_ADD(AttendanceDate, INTERVAL 1 DAY)
    FROM Dates
    WHERE AttendanceDate < '2025-01-07'
)

SELECT d.AttendanceDate AS MissingDate
FROM Dates d
LEFT JOIN Attendance a
ON d.AttendanceDate = a.AttendanceDate
WHERE a.AttendanceDate IS NULL;
```

---

## Notes

- Uses a Recursive CTE.
- Generates all dates in a range.
- Uses `LEFT JOIN` to identify missing dates.
