# 🙅‍♂️ Find Customer Referee

## 🧾 Table Schema

**Customer**
| Column Name | Type    | Description                          |
|-------------|---------|--------------------------------------|
| id          | int     | Primary key                          |
| name        | varchar | Customer name                        |
| referee_id  | int     | Referrer customer id (nullable)      |

---

## 🎯 Goal

Get names of customers **not referred by customer with `id = 2`**.

---

## ✅ Solution

```sql
SELECT name
FROM Customer
WHERE referee_id IS NULL OR referee_id != 2;
```
## 🔗 LeetCode Link

[Find Customer Referee](https://leetcode.com/problems/find-customer-referee/?envType=study-plan-v2&envId=top-sql-50)