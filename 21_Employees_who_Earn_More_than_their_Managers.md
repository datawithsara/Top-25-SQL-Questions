# Question 21 - Find Employees Who Earn More Than Their Manager

**Difficulty:** Medium

## Problem Statement

Write an SQL query to find employees whose salary is greater than their manager's salary.

### Employees

| EmployeeID | Name | Salary | ManagerID |
|------------|------|--------|-----------|
| 1 | Sara | 90000 | NULL |
| 2 | John | 70000 | 1 |
| 3 | Alex | 95000 | 1 |
| 4 | Emma | 60000 | 2 |
| 5 | David | 80000 | 2 |

### Expected Output

| EmployeeID | Name | Salary |
|------------|------|--------|
| 3 | Alex | 95000 |
| 5 | David | 80000 |

---

## Solution

```sql
SELECT e.EmployeeID,
       e.Name,
       e.Salary
FROM Employees e
JOIN Employees m
ON e.ManagerID = m.EmployeeID
WHERE e.Salary > m.Salary;
```

---

## Notes

- Uses a Self Join.
- Compares an employee's salary with their manager's salary.
