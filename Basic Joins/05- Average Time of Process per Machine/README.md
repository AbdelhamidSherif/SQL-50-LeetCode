
# 🏭 Average Time of Process per Machine

## 🧾 Table Schema

### `Activity`
| Column Name    | Type   | Description |
|----------------|--------|-------------|
| machine_id     | int    | ID of the machine |
| process_id     | int    | ID of the process |
| activity_type  | enum   | 'start' or 'end' |
| timestamp      | float  | Time in seconds |

- `(machine_id, process_id, activity_type)` is the **primary key**.
- Each process has exactly one `start` and one `end`.

---

## 🎯 Goal

Find the **average processing time** per machine.  
A process’s time is calculated as `end_timestamp - start_timestamp`.

- Return columns:  
  - `machine_id`  
  - `processing_time` → rounded to 3 decimal places

---

## ✅ Solution

```sql
SELECT 
    a.machine_id,
    ROUND(AVG(b.timestamp - a.timestamp), 3) AS processing_time
FROM Activity a
JOIN Activity b
  ON a.machine_id = b.machine_id
 AND a.process_id = b.process_id
 AND a.activity_type = 'start'
 AND b.activity_type = 'end'
GROUP BY a.machine_id;

--Another way
-- SELECT machine_id, ROUND(SUM(CASE WHEN activity_type = 'start' THEN timestamp * -1 ELSE timestamp END)/(COUNT(machine_id)/2), 3) AS processing_time
--FROM Activity
--GROUP BY machine_id

```

---

## 🧠 Explanation

- We join the `start` and `end` rows using `machine_id` and `process_id`.
- For each pair, calculate the duration and take the average per machine.
- Use `ROUND(..., 3)` to round the result to 3 decimal places.

---
🔗 LeetCode Link: [Average Time of Process per Machine](https://leetcode.com/problems/average-time-of-process-per-machine/description/?envType=study-plan-v2&envId=top-sql-50)
