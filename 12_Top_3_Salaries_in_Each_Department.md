# Question 12 - Find the Top 3 Salaries in Each Department

**Difficulty:** Medium

## Problem Statement

Write an SQL query to find the **top 3 highest salaries in each department**.

### Employees

| EmployeeID | Name | Department | Salary |
|------------|------|------------|--------|
| 1 | Sara | HR | 50000 |
| 2 | John | HR | 65000 |
| 3 | Alex | HR | 60000 |
| 4 | Emma | HR | 75000 |
| 5 | David | HR | 55000 |
| 6 | Michael | IT | 70000 |
| 7 | Sophia | IT | 85000 |
| 8 | Ethan | IT | 90000 |
| 9 | Olivia | IT | 78000 |
| 10 | Liam | IT | 72000 |

### Expected Output

| EmployeeID | Name | Department | Salary |
|------------|------|------------|--------|
| 4 | Emma | HR | 75000 |
| 2 | John | HR | 65000 |
| 3 | Alex | HR | 60000 |
| 8 | Ethan | IT | 90000 |
| 7 | Sophia | IT | 85000 |
| 9 | Olivia | IT | 78000 |

---

## Solution

```sql
SELECT EmployeeID,
       Name,
       Department,
       Salary
FROM (
    SELECT *,
           DENSE_RANK() OVER (
               PARTITION BY Department
               ORDER BY Salary DESC
           ) AS SalaryRank
    FROM Employees
) t
WHERE SalaryRank <= 3
ORDER BY Department, Salary DESC;
```

---

## Notes

- Uses `DENSE_RANK()` to rank employees based on salary within each department.
- `PARTITION BY Department` creates separate rankings for each department.
- `ORDER BY Salary DESC` ranks salaries from highest to lowest.
- Returns only the top 3 highest-paid employees from each department.
