# 🚫 Invalid Tweets

## 🧾 Table Schema

**Tweets**
| Column Name | Type    | Description                         |
|-------------|---------|-------------------------------------|
| tweet_id    | int     | Primary key                         |
| content     | varchar | Text content of the tweet           |

> A tweet is invalid if its `content` length is **strictly greater than 15 characters**.

---

## 🎯 Goal

Find the IDs of tweets that are **invalid** (i.e., `content` length > 15).

---

## ✅ Solution

```sql
SELECT tweet_id
FROM Tweets
WHERE LEN(content) > 15;
```
## 🔗 LeetCode Link

[Invalid Tweets](https://leetcode.com/problems/invalid-tweets/description/?envType=study-plan-v2&envId=top-sql-50)