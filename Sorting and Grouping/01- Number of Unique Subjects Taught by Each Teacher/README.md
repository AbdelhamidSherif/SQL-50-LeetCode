# Number of Unique Subjects Taught by Each Teacher

## Problem Description

We are given a table `Teacher` that stores information about which teacher teaches which subject in which department.  

### Table: Teacher

| Column Name | Type |
|-------------|------|
| teacher_id  | int  |
| subject_id  | int  |
| dept_id     | int  |

- `(subject_id, dept_id)` is the **primary key** (unique combination).  
- Each row indicates that a teacher with `teacher_id` teaches a subject `subject_id` in a department `dept_id`.  

---

## 🎯 Goal  

We need to **calculate the number of unique subjects each teacher teaches** across all departments.  

---

## Solution

```sql
SELECT teacher_id, COUNT(DISTINCT subject_id) AS cnt
FROM Teacher
GROUP BY teacher_id
```

## 🔗 LeetCode Link
[Number of Unique Subjects Taught by Each Teacher](https://leetcode.com/problems/number-of-unique-subjects-taught-by-each-teacher/description/?envType=study-plan-v2&envId=top-sql-50)