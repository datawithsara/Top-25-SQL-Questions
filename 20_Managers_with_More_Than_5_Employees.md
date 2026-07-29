# Question 20 - Find Managers with More Than 5 Employees

**Difficulty:** Medium

## Problem Statement

Write an SQL query to find managers who supervise more than five employees.

### Employees

| EmployeeID | ManagerID |
|------------|-----------|
|1|101|
|2|101|
|3|101|
|4|101|
|5|101|
|6|101|
|7|102|

### Expected Output

| ManagerID |
|-----------|
|101|

---

## Solution

```sql
SELECT ManagerID
FROM Employees
GROUP BY ManagerID
HAVING COUNT(*) > 5;
```

---

## Notes

- Uses `GROUP BY`.
- Uses `HAVING` with `COUNT()`.
