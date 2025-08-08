# 📈 Queries Quality and Percentage

## 🧾 Table Schema

### `Queries`

| Column Name | Type    | Description |
|-------------|---------|-------------|
| query_name  | varchar | Name of the query |
| result      | varchar | Result returned by the query |
| position    | int     | Position of the result (1–500) |
| rating      | int     | Rating given to the query result (1–5) |

> ℹ️ This table may contain **duplicate rows**.  
> **Poor query** → A query with `rating < 3`.

---

## 📌 Definitions

- **Query Quality** = Average of `(rating / position)` for all results of a query.
- **Poor Query Percentage** = `(Number of queries with rating < 3) / (Total number of queries) × 100`

---

## 🎯 Goal

For each `query_name`, calculate:
1. **quality** → rounded to **2 decimal places**
2. **poor_query_percentage** → rounded to **2 decimal places**

Return the result in any order.

---

## ✅ Solution

```sql
/* Write your T-SQL query statement below */
SELECT query_name, ROUND((SUM(rating * 1.0/ position) ) / COUNT(*), 2) AS quality, ROUND(SUM(CASE WHEN rating < 3 THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 2) AS poor_query_percentage
FROM Queries
GROUP BY query_name
ORDER BY quality DESC

-- Another solution
-- SELECT query_name, ROUND((AVG(CAST(rating AS FLOAT) / position) ), 2) AS quality, ROUND(SUM(CASE WHEN rating < 3 THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 2) AS poor_query_percentage
-- FROM Queries
-- GROUP BY query_name
-- ORDER BY quality DESC

```

## 🔗 LeetCode Link
[Queries Quality and Percentage](https://leetcode.com/problems/queries-quality-and-percentage/description/?envType=study-plan-v2&envId=top-sql-50)
