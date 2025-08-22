# Game Play Analysis IV

## Problem Description

We are given a table `Activity` that stores information about players' game activity.  

### Table: Activity

| Column Name  | Type |
|--------------|------|
| player_id    | int  |
| device_id    | int  |
| event_date   | date |
| games_played | int  |

- `(player_id, event_date)` is the primary key.  
- Each row represents a record of a player who logged in and played a number of games on a specific date.  

---

## 🎯 Goal  

We need to **report the fraction of players who logged in again on the day immediately after their first login**, rounded to **2 decimal places**.  

---

## Example

**Input:**

**Activity**
| player_id | device_id | event_date | games_played |
|-----------|-----------|------------|--------------|
| 1         | 2         | 2016-03-01 | 5            |
| 1         | 2         | 2016-03-02 | 6            |
| 2         | 3         | 2017-06-25 | 1            |
| 3         | 1         | 2016-03-02 | 0            |
| 3         | 4         | 2018-07-03 | 5            |

**Output:**
| fraction |
|----------|
| 0.33     |

**Explanation:**
- Player **1** → First login = `2016-03-01`, logged in again on `2016-03-02` → Counted.  
- Player **2** → First login = `2017-06-25`, no login on `2017-06-26` → Not counted.  
- Player **3** → First login = `2016-03-02`, next login = `2018-07-03` (not consecutive) → Not counted.  

Out of 3 players, only 1 logged in the next day → `1 / 3 = 0.33`.

---

## ✅ Solution

```sql
SELECT ROUND(1.0 * COUNT(a2.player_id)/COUNT( a1.player_id), 2) AS fraction
FROM (SELECT player_id,
             MIN(event_date) AS first_day
      FROM Activity 
             GROUP BY player_id) a1
LEFT JOIN Activity a2
ON a1.player_id = a2.player_id
AND a2.event_date = DATEADD(day, 1, a1.first_day);

```
## 🔗 LeetCode Link
[Game Play Analysis IV](https://leetcode.com/problems/game-play-analysis-iv/description/?envType=study-plan-v2&envId=top-sql-50)