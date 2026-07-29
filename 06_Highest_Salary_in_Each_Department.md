# Question 06 - Find the Highest Salary in Each Department

**Difficulty:** Easy

## Problem Statement

Write an SQL query to find the highest salary in each department.

### Employees

| EmployeeID | Name | Department | Salary |
|------------|------|------------|--------|
| 1 | Sara | HR | 50000 |
| 2 | John | IT | 70000 |
| 3 | Alex | HR | 60000 |
| 4 | Emma | IT | 80000 |
| 5 | David | Finance | 65000 |

### Expected Output

| Department | HighestSalary |
|------------|---------------|
| HR | 60000 |
| IT | 80000 |
| Finance | 65000 |

---

## Solution

```sql
SELECT Department,
       MAX(Salary) AS HighestSalary
FROM Employees
GROUP BY Department;
```

---

## Notes

- Uses the `MAX()` aggregate function.
- `GROUP BY` returns one row per department.
