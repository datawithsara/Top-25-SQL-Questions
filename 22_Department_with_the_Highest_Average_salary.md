# Question 22 - Find the Department with the Highest Average Salary

**Difficulty:** Medium

## Problem Statement

Write an SQL query to find the department having the highest average salary.

### Employees

| EmployeeID | Name | Department | Salary |
|------------|------|------------|--------|
| 1 | Sara | HR | 50000 |
| 2 | John | HR | 70000 |
| 3 | Alex | IT | 90000 |
| 4 | Emma | IT | 80000 |
| 5 | David | Finance | 60000 |

### Expected Output

| Department | AverageSalary |
|------------|---------------|
| IT | 85000 |

---

## Solution

```sql
SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department
ORDER BY AverageSalary DESC
LIMIT 1;
```

---

## Notes

- Uses `AVG()`.
- Uses `GROUP BY`.
- Orders by average salary in descending order.
