
# Find Followers Count

## Problem Description

We are given a table `Followers` that stores information about users and their followers in a social media app.  

### Table: Followers

| Column Name | Type |
|-------------|------|
| user_id     | int  |
| follower_id | int  |

- `(user_id, follower_id)` is the **primary key** (combination of columns with unique values).  
- Each row indicates that the `follower_id` is following the `user_id`.  

---

## 🎯 Goal

For each user, return the **number of followers** they have.  

The result should include two columns:  
- `user_id`  
- `followers_count`  

The output must be ordered by `user_id` in ascending order.  

---

## Solution
```sql
SELECT user_id,
       COUNT(follower_id) AS followers_count
FROM Followers
GROUP BY user_id

```

## 🔗 LeetCode Link
[Find Followers Count](https://leetcode.com/problems/find-followers-count/description/?envType=study-plan-v2&envId=top-sql-50)