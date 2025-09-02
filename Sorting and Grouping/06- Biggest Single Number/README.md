
# Biggest Single Number

## Problem Description

We are given a table `MyNumbers` that contains integers.  

### Table: MyNumbers

| Column Name | Type |
|-------------|------|
| num         | int  |

- This table **may contain duplicates** (no primary key).  
- A **single number** is a number that appears **exactly once** in the table.  

---

## 🎯 Goal

Find the **largest single number** in the table.  
If there is no single number, return **null**.  

---

## Solution

```sql
-- SELECT 
--     COALESCE(
--         (
--             SELECT TOP 1 num
--             FROM MyNumbers
--             GROUP BY num
--             HAVING COUNT(*) = 1
--             ORDER BY num DESC
--         ), 
--         NULL
--     ) AS num

--Another solution
SELECT MAX(num) AS num
FROM (
    SELECT num
    FROM MyNumbers
    GROUP BY num
    HAVING COUNT(num) = 1
) AS single_numbers;

```

## 🔗 LeetCode Link
[Biggest Single Number](https://leetcode.com/problems/biggest-single-number/description/?envType=study-plan-v2&envId=top-sql-50)
