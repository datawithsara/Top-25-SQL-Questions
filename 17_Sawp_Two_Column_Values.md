# Question 17 - Swap Two Column Values

**Difficulty:** Easy

## Problem Statement

Write an SQL query to swap values of two columns.

### Employees

| EmployeeID | FirstName | LastName |
|------------|-----------|----------|
|1|Ria|Sharma|

### Expected Output

| EmployeeID | FirstName | LastName |
|------------|-----------|----------|
|1|Sharma|Ria|

---

## Solution

```sql
SELECT EmployeeID,
       LastName AS FirstName,
       FirstName AS LastName
FROM Employees;
```

---

## Notes

- Uses column aliases.
- Useful for basic SQL transformations.
