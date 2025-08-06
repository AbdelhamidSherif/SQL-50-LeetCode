# 🎬 Not Boring Movies

## 🧾 Table Schema

### `Cinema`

| Column Name | Type    | Description                          |
|-------------|---------|--------------------------------------|
| id          | int     | Primary key, unique movie identifier |
| movie       | varchar | Name of the movie                    |
| description | varchar | Description of the movie             |
| rating      | float   | Movie rating (2 decimal places)      |

---

## 🎯 Goal

Report all movies that:
- Have an **odd-numbered ID**
- Have a **description that is not 'boring'**

The result should be **ordered by rating in descending order**.

---

## ✅ Solution

```sql
-- SELECT *
-- FROM Cinema
-- WHERE id % 2 = 1
--   AND description != 'boring'
-- ORDER BY rating DESC;

-- Another solution using => Bitwise And Manipulation
SELECT *
FROM Cinema
WHERE id & 1 = 1 
    AND description <> 'boring'
ORDER BY rating DESC;
```
## 🔗 LeetCode Link

[Not Boring Movies](https://leetcode.com/problems/not-boring-movies/description/?envType=study-plan-v2&envId=top-sql-50)