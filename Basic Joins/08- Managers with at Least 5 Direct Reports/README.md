# 🧑‍💼 Managers with at Least 5 Direct Reports

## 🧾 Table Definition

### Employee

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |
| department  | varchar |
| managerId   | int     |

- `id` is the primary key.
- Each row represents an employee and their department.
- `managerId` refers to the `id` of that employee’s manager.
- If `managerId` is `NULL`, the employee does not have a manager.
- No employee is their own manager.

---

## 🎯 Goal

Find the names of managers who have **at least 5 direct reports**.

- A direct report is an employee whose `managerId` matches the manager's `id`.

---
## ✅ SQL Solution

```sql
-- SELECT e1.name
-- FROM Employee e1
-- JOIN Employee e2 ON e1.id = e2.managerId
-- GROUP BY e1.id, e1.name
-- HAVING COUNT(e2.id) >= 5;

-- Another solution
SELECT name
FROM Employee
WHERE id IN(
SELECT managerId FROM Employee
WHERE managerId IS NOT NuLL
GROUP BY managerId
HAVING COUNT(managerId) >= 5
);

```
---
🔗 LeetCode Link: [Managers with at Least 5 Direct Reports](https://leetcode.com/problems/managers-with-at-least-5-direct-reports/?envType=study-plan-v2&envId=top-sql-50)