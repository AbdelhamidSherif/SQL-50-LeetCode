
# Classes With at Least 5 Students

## Problem Description

We are given a table `Courses` that stores information about students and the classes they are enrolled in.  

### Table: Courses

| Column Name | Type    |
|-------------|---------|
| student     | varchar |
| class       | varchar |

- `(student, class)` is the **primary key** (combination of columns with unique values).  
- Each row represents that a student is enrolled in a specific class.  

---

## 🎯 Goal

Find all the **classes that have at least 5 students enrolled**.  

The result should return only the `class` column.  

---

## Solution

```sql
SELECT class
FROM Courses
GROUP BY class
HAVING COUNT(class) >= 5

```

## 🔗 LeetCode Link
[Classes With at Least 5 Students](https://leetcode.com/problems/classes-with-at-least-5-students/description/?envType=study-plan-v2&envId=top-sql-50)