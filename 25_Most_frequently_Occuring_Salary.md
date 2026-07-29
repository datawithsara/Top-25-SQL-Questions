# Question 25 - Find the Most Frequently Occurring Salary

**Difficulty:** Medium

## Problem Statement

Write an SQL query to find the salary that appears most frequently.

### Employees

| EmployeeID | Name | Salary |
|------------|------|--------|
| 1 | Sara | 50000 |
| 2 | John | 70000 |
| 3 | Alex | 60000 |
| 4 | Emma | 70000 |
| 5 | David | 70000 |
| 6 | Olivia | 50000 |

### Expected Output

| Salary | Frequency |
|--------|-----------|
| 70000 | 3 |

---

## Solution

```sql
SELECT Salary,
       COUNT(*) AS Frequency
FROM Employees
GROUP BY Salary
ORDER BY Frequency DESC
LIMIT 1;
```

---

## Notes

- Uses `COUNT()`.
- Groups identical salary values.
- Returns the most frequently occurring salary.
