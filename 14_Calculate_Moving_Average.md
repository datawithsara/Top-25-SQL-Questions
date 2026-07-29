# Question 14 - Calculate Moving Average

**Difficulty:** Medium

## Problem Statement

Write an SQL query to calculate a 3-day moving average of sales.

### Orders

| OrderDate | Amount |
|-----------|--------|
|2025-01-01|500|
|2025-01-02|700|
|2025-01-03|600|
|2025-01-04|900|

### Expected Output

| OrderDate | MovingAverage |
|-----------|---------------|
|2025-01-01|500|
|2025-01-02|600|
|2025-01-03|600|
|2025-01-04|733.33|

---

## Solution

```sql
SELECT OrderDate,
       Amount,
       AVG(Amount) OVER(
           ORDER BY OrderDate
           ROWS BETWEEN 2 PRECEDING AND CURRENT ROW
       ) AS MovingAverage
FROM Orders;
```

---

## Notes

- Uses `AVG()` Window Function.
- Calculates a rolling average.
