# 🆔 Replace Employee ID With The Unique Identifier

## 🧾 Table Schema

**Employees**
| Column Name | Type    | Description              |
|-------------|---------|--------------------------|
| id          | int     | Employee ID (Primary key)|
| name        | varchar | Employee name            |

**EmployeeUNI**
| Column Name | Type    | Description                 |
|-------------|---------|-----------------------------|
| id          | int     | Employee ID                 |
| unique_id   | int     | Unique identifier for user  |

> `(id, unique_id)` is a composite primary key in **EmployeeUNI**

---

## 🎯 Goal

Get each employee's `unique_id` and `name`.  
If an employee has no unique ID in `EmployeeUNI`, show `null`.

---

## ✅ Solution

```sql
SELECT eu.unique_id, e.name
FROM Employees e
LEFT JOIN EmployeeUNI eu
ON e.id = eu.id;
```
## 🔗 LeetCode Link

[Replace Employee ID With The Unique Identifier](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/?envType=study-plan-v2&envId=top-sql-50)