# Question 02 - Find the Nth Highest Salary

**Difficulty:** Medium

## Problem Statement

Write an SQL query to find the **Nth highest salary** from the `Employees` table.

### Employees

| EmployeeID | Name | Salary |
|------------|------|--------|
| 1 | Sara | 50000 |
| 2 | John | 70000 |
| 3 | Alex | 60000 |
| 4 | Emma | 70000 |
| 5 | David | 45000 |

### Expected Output (N = 3)

| ThirdHighestSalary |
|--------------------|
| 50000 |

---

## Solution

```sql
SELECT Salary
FROM (
    SELECT Salary,
           DENSE_RANK() OVER (ORDER BY Salary DESC) AS SalaryRank
    FROM Employees
) t
WHERE SalaryRank = 3;
```

---

## Notes

- Replace `3` with the required value of **N**.
- Uses `DENSE_RANK()` to handle duplicate salaries.
- Demonstrates the use of a Window Function and a Subquery.
