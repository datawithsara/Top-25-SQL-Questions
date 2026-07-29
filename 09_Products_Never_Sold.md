# Question 09 - Find Products That Were Never Sold

**Difficulty:** Easy

## Problem Statement

Write an SQL query to find products that have never been sold.

### Products

| ProductID | ProductName |
|-----------|-------------|
| 1 | Laptop |
| 2 | Mouse |
| 3 | Keyboard |
| 4 | Monitor |

### Orders

| OrderID | ProductID |
|---------|-----------|
| 101 | 1 |
| 102 | 2 |
| 103 | 1 |

### Expected Output

| ProductID | ProductName |
|-----------|-------------|
| 3 | Keyboard |
| 4 | Monitor |

---

## Solution

```sql
SELECT p.ProductID,
       p.ProductName
FROM Products p
LEFT JOIN Orders o
ON p.ProductID = o.ProductID
WHERE o.ProductID IS NULL;
```

---

## Notes

- Uses `LEFT JOIN`.
- Returns products with no matching order.
- Similar logic to "Customers with No Orders".
