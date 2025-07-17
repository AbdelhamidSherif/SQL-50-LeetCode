# 🌡️ Rising Temperature

## 🧾 Table Schema

**Weather**
| Column Name | Type | Description |
|-------------|------|-------------|
| id          | int  | Unique ID for each record |
| recordDate  | date | The date of the temperature record |
| temperature | int  | Temperature recorded on that day |

> Each row represents the temperature on a specific day. No two rows have the same `recordDate`.

---

## 🎯 Goal

Find the IDs of days where the temperature was **higher than the previous day**.

---

## ✅ Solution

```sql
/*
SELECT w1.id 
FROM Weather w1, Weather w2
WHERE w1.id-1 = w2.id
AND w1.temperature > w2.temperature AND w1.recordDate > w2.recordDate
*/

-- Another way
SELECT w1.id
FROM Weather w1
JOIN Weather w2
  ON DATEDIFF(DAY, w2.recordDate, w1.recordDate) = 1
WHERE w1.temperature > w2.temperature;
```
🔗 LeetCode Link: [Rising Temperature](https://leetcode.com/problems/rising-temperature/?envType=study-plan-v2&envId=top-sql-50)
