
# ✅ Confirmation Rate

## 🧾 Table Schema

### `Signups`

| Column Name | Type     | Description                        |
|-------------|----------|------------------------------------|
| user_id     | int      | Unique ID of the user              |
| time_stamp  | datetime | The signup time of the user        |

---

### `Confirmations`

| Column Name | Type     | Description                                  |
|-------------|----------|----------------------------------------------|
| user_id     | int      | ID of the user (FK to Signups.user_id)       |
| time_stamp  | datetime | Time of confirmation or timeout              |
| action      | enum     | Either `'confirmed'` or `'timeout'`          |

Primary Key: (`user_id`, `time_stamp`)

---

## 🎯 Goal

Find the **confirmation rate** of each user:
- Confirmation rate = ` of confirmed / total  of requests`
- If a user made **no confirmation requests**, their rate should be **0.00**
- Round the result to **2 decimal places**

---

## ✅ Solution

```sql
-- SELECT s.user_id,
-- CASE WHEN COUNT(c.user_id) = 0 THEN 0.00 ELSE
-- ROUND(SUM(CASE WHEN c.action = 'confirmed' THEN 1.0 ELSE 0 END) / COUNT(c.user_id), 2) END AS confirmation_rate
-- FROM Signups s
-- LEFT JOIN Confirmations c
-- ON s.user_id = c.user_id
-- GROUP BY s.user_id

-- Another solution
SELECT s.user_id, ROUND(COALESCE(SUM(CASE WHEN c.action = 'confirmed' THEN 1.0 ELSE 0.0 END)/NULLIF(COUNT(c.user_id),0), 0), 2) AS confirmation_rate
FROM Signups s
LEFT JOIN Confirmations c
ON s.user_id = c.user_id
GROUP BY s.user_id

```
---
🔗 LeetCode Link: [Confirmation Rate](https://leetcode.com/problems/confirmation-rate/description/?envType=study-plan-v2&envId=top-sql-50)