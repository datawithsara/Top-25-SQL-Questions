# Question 08 - Find Customers with No Orders

**Difficulty:** Easy

## Problem Statement

Write an SQL query to find customers who have never placed an order.

### Customers

| CustomerID | CustomerName |
|------------|--------------|
| 1 | Sara |
| 2 | John |
| 3 | Alex |
| 4 | Emma |

### Orders

| OrderID | CustomerID |
|---------|------------|
| 101 | 1 |
| 102 | 2 |
| 103 | 1 |

### Expected Output

| CustomerID | CustomerName |
|------------|--------------|
| 3 | Alex |
| 4 | Emma |

---

## Solution

```sql
SELECT c.CustomerID,
       c.CustomerName
FROM Customers c
LEFT JOIN Orders o
ON c.CustomerID = o.CustomerID
WHERE o.CustomerID IS NULL;
```

---

## Notes

- Uses `LEFT JOIN`.
- Finds records that have no matching values.
- Common interview question.
