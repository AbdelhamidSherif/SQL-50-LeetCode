# User Activity for the Past 30 Days I

## Problem Description

We are given a table `Activity` that stores user activity logs for a social media website.  

### Table: Activity

| Column Name   | Type   |
|---------------|--------|
| user_id       | int    |
| session_id    | int    |
| activity_date | date   |
| activity_type | enum   |

- This table **may contain duplicate rows**.  
- The `activity_type` column is an ENUM of type:  
  - `'open_session'`, `'end_session'`, `'scroll_down'`, `'send_message'`.  
- Each `session_id` belongs to exactly one user.  
- A **user is considered active on a given day** if they made **at least one activity** on that day.  

---

## 🎯 Goal  

We need to find the **daily active user count** for the **30-day period ending on 2019-07-27 (inclusive)**.  
Only include days where there is **at least one active user**.  

---

## Solution

```sql
SELECT activity_date AS day, COUNT(DISTiNCT user_id) AS active_users
FROM Activity
WHERE activity_date BETWEEN '2019-06-28' AND '2019-07-27'
GROUP BY activity_date

```

## 🔗 LeetCode Link
[User Activity for the Past 30 Days I](https://leetcode.com/problems/user-activity-for-the-past-30-days-i/description/?envType=study-plan-v2&envId=top-sql-50)