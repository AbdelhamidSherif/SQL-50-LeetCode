# 👥 Project Employees I

## 🧾 Table Schemas

### `Project`
| Column Name | Type | Description |
|-------------|------|-------------|
| project_id  | int  | Project identifier |
| employee_id | int  | Employee identifier |

> 🔑 `(project_id, employee_id)` is the **primary key**.  
> 🔗 `employee_id` is a **foreign key** to Employee table.  
> 📌 Each row indicates that the employee is working on the project.

---

### `Employee`
| Column Name      | Type    | Description |
|------------------|---------|-------------|
| employee_id      | int     | Employee identifier |
| name             | varchar | Employee name |
| experience_years | int     | Years of experience |

> 🔑 `employee_id` is the **primary key**.  
> ✅ It's guaranteed that `experience_years` is **not NULL**.

---

## 🎯 Goal
Write an SQL query that reports the **average experience years** of all employees for each project.
- Round the result to **2 decimal places**.
- Return the result table in **any order**.

---

## ✅ Solution
```sql
SELECT p.project_id,
       ROUND(AVG(e.experience_years * 1.0), 2) AS average_years
FROM Project p
JOIN Employee e ON p.employee_id = e.employee_id
GROUP BY p.project_id;
```

## 🔗 LeetCode Link
[Project Employees I](https://leetcode.com/problems/project-employees-i/?envType=study-plan-v2&envId=top-sql-50)