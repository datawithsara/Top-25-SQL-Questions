# Question 01 - Find the 2nd Highest Salary

**Difficulty:** Easy

## Problem Statement

Write an SQL query to find the **second highest salary** from the `Employees` table.

### Employees

| EmployeeID | Name | Salary |
|------------|------|--------|
| 1 | Sara | 50000 |
| 2 | John | 70000 |
| 3 | Alex | 60000 |
| 4 | Emma | 70000 |

### Expected Output

| SecondHighestSalary |
|----------------------|
| 60000 |

---

## Solution

```sql
SELECT Salary
FROM (
    SELECT Salary,
           DENSE_RANK() OVER (ORDER BY Salary DESC) AS SalaryRank
    FROM Employees
) t
WHERE SalaryRank = 2;
```

---

## Notes

- Uses `DENSE_RANK()` to rank salaries in descending order.
- Correctly handles duplicate salaries.
- Demonstrates the use of a Window Function and a Subquery.
