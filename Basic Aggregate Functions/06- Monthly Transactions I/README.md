# Monthly Transactions I

## Problem Description

We are given a table `Transactions` that stores information about incoming transactions.

### Table: Transactions

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| country     | varchar |
| state       | enum    |
| amount      | int     |
| trans_date  | date    |

- `id` is the primary key.
- `state` is an enum with values `["approved", "declined"]`.
- `trans_date` stores the date of the transaction.
---
## 🎯 Goal

We need to find **for each month and country**:
- Total number of transactions (`trans_count`)
- Number of approved transactions (`approved_count`)
- Total transaction amount (`trans_total_amount`)
- Total approved transaction amount (`approved_total_amount`)

The `month` should be in the format `YYYY-MM`.

Return the result table in any order.

---

```sql
SELECT 
        FORMAT(trans_date, 'yyyy-MM') AS month,
        country, COUNT(*) AS trans_count,
        SUM(CASE WHEN state = 'approved' THEN 1 ELSE 0 END) AS approved_count,
        SUM(amount) AS trans_total_amount,
        SUM(CASE WHEN state = 'approved' THEN amount ELSE 0 END) AS approved_total_amount 
FROM Transactions
GROUP BY FORMAT(trans_date, 'yyyy-MM'), country
ORDER BY trans_count DESC

```

## 🔗 LeetCode Link
[Monthly Transactions I](https://leetcode.com/problems/monthly-transactions-i/?envType=study-plan-v2&envId=top-sql-50)
