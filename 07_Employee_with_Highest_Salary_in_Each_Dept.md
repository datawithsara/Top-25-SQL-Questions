# Question 07 - Find the Employee with the Highest Salary in Each Department

**Difficulty:** Medium

## Problem Statement

Write an SQL query to find the employee(s) with the highest salary in each department.

### Employees

| EmployeeID | Name | Department | Salary |
|------------|------|------------|--------|
| 1 | Sara | HR | 50000 |
| 2 | John | IT | 70000 |
| 3 | Alex | HR | 60000 |
| 4 | Emma | IT | 80000 |
| 5 | David | Finance | 65000 |

### Expected Output

| EmployeeID | Name | Department | Salary |
|------------|------|------------|--------|
| 3 | Alex | HR | 60000 |
| 4 | Emma | IT | 80000 |
| 5 | David | Finance | 65000 |

---

## Solution

```sql
SELECT EmployeeID,
       Name,
       Department,
       Salary
FROM (
    SELECT *,
           DENSE_RANK() OVER(
               PARTITION BY Department
               ORDER BY Salary DESC
           ) AS SalaryRank
    FROM Employees
) t
WHERE SalaryRank = 1;
```

---

## Notes

- Uses `DENSE_RANK()`.
- `PARTITION BY` ranks employees within each department.
- Handles ties correctly.
