# Question 03 - Find Duplicate Records

**Difficulty:** Easy

## Problem Statement

Write an SQL query to find all duplicate email addresses from the `Employees` table.

### Employees

| EmployeeID | Name | Email |
|------------|------|---------------------|
| 1 | Sara | sara@mail.com |
| 2 | John | john@mail.com |
| 3 | Alex | sara@mail.com |
| 4 | Emma | emma@mail.com |
| 5 | David | john@mail.com |

### Expected Output

| Email |
|---------------------|
| sara@gmail.com |
| john@gmail.com |

---

## Solution

```sql
SELECT Email
FROM Employees
GROUP BY Email
HAVING COUNT(*) > 1;
```

---

## Notes

- Uses `GROUP BY` to group identical values.
- `HAVING COUNT(*) > 1` filters only duplicate records.
- One of the most common SQL interview questions.
