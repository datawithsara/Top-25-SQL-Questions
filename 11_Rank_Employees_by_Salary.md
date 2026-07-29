# Question 11 - Rank Employees by Salary

**Difficulty:** Medium

## Problem Statement

Write an SQL query to rank employees based on their salary in descending order.

### Employees

| EmployeeID | Name | Salary |
|------------|------|--------|
| 1 | Sara | 50000 |
| 2 | John | 70000 |
| 3 | Alex | 60000 |
| 4 | Emma | 70000 |
| 5 | David | 40000 |

### Expected Output

| EmployeeID | Name | Salary | Rank |
|------------|------|--------|------|
|2|John|70000|1|
|4|Emma|70000|1|
|3|Alex|60000|2|
|1|Sara|50000|3|
|5|David|40000|4|

---

## Solution

```sql
SELECT EmployeeID,
       Name,
       Salary,
       DENSE_RANK() OVER(ORDER BY Salary DESC) AS SalaryRank
FROM Employees;
```

---

## Notes

- Uses `DENSE_RANK()`.
- Employees with the same salary receive the same rank.
