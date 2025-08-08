# 📊 Percentage of Users Attended a Contest

## 🧾 Table Schemas

### `Users`

| Column Name | Type    | Description |
|-------------|---------|-------------|
| user_id     | int     | Unique identifier of the user |
| user_name   | varchar | Name of the user |

> 🔑 `user_id` is the **primary key**.

---

### `Register`

| Column Name | Type | Description |
|-------------|------|-------------|
| contest_id  | int  | Contest identifier |
| user_id     | int  | User identifier |

> 🔑 `(contest_id, user_id)` is the **primary key**.

---

## 🎯 Goal

Find the **percentage of users** registered in each contest, rounded to **two decimal places**.  
Sort results by:
1. `percentage` in **descending** order.
2. `contest_id` in **ascending** order when percentages are equal.

---

## ✅ Solution

```sql
SELECT contest_id, ROUND(COUNT(user_id) * 1.0 / (SELECT COUNT(user_id) FROM Users) * 100, 2) AS percentage
FROM Register
GROUP BY contest_id
ORDER BY percentage DESC, contest_id ASC
```

## 🔗 LeetCode Link
[Percentage of Users Attended a Contest](https://leetcode.com/problems/percentage-of-users-attended-a-contest/description/?envType=study-plan-v2&envId=top-sql-50)