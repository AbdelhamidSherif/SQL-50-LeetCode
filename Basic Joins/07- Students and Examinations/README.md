# 📘 Students and Examinations

## 🧾 Table Definitions

### Students

| Column Name   | Type    |
|---------------|---------|
| student_id    | int     |
| student_name  | varchar |

- `student_id` is the primary key.
- Each row contains information about a student in the school.

### Subjects

| Column Name  | Type    |
|--------------|---------|
| subject_name | varchar |

- `subject_name` is the primary key.
- Each row contains the name of a subject.

### Examinations

| Column Name  | Type    |
|--------------|---------|
| student_id   | int     |
| subject_name | varchar |

- There is no primary key and duplicates may exist.
- Each row indicates that a student attended an exam for a subject.

---

## 🎯 Goal

Find how many times each student attended each exam.

- You must return all possible combinations of students and subjects.
- Output should include:
  - `student_id`
  - `student_name`
  - `subject_name`
  - `attended_exams`
- The result should be ordered by `student_id` and `subject_name`.

---

## 🧠 Approach

- Use a `CROSS JOIN` between `Students` and `Subjects` to get all student-subject pairs.
- Use a `LEFT JOIN` with `Examinations` to count how many times each student took each subject.
- Use `GROUP BY` and `COUNT()` to calculate the attendance count per pair.

---

## ✅ SQL Solution

```sql
SELECT St.student_id, 
       St.student_name, 
       Su.subject_name, 
       COUNT(Ex.subject_name) AS attended_exams
FROM Students St
CROSS JOIN Subjects Su
LEFT JOIN Examinations Ex
ON Su.subject_name = Ex.subject_name AND 
St.student_id = Ex.student_id
GROUP BY
  St.student_id, 
  St.student_name, 
  Su.subject_name
ORDER BY s.student_id,
         s.student_name;

```

---
🔗 LeetCode Link: [Students and Examinations](https://leetcode.com/problems/students-and-examinations/description/)