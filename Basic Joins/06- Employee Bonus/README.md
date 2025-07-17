# 💰 Employee Bonus

> **LeetCode Problem**: [Employee Bonus](https://leetcode.com/problems/employee-bonus/)

## 🧾 Table Schemas

### Employee
| Column Name | Type    | Description                              |
|-------------|---------|------------------------------------------|
| empId       | int     | Employee ID (Primary key)                |
| name        | varchar | Name of the employee                     |
| supervisor  | int     | ID of the employee's manager             |
| salary      | int     | Salary of the employee                   |

### Bonus
| Column Name | Type | Description                               |
|-------------|------|-------------------------------------------|
| empId       | int  | Foreign key to Employee.empId            |
| bonus       | int  | Bonus amount for the employee             |

---

## 🎯 Goal
Return the name and bonus amount of each employee who has a bonus **less than 1000**.

---

## ✅ Solution

```sql
SELECT e.name, b.bonus
FROM Employee e
JOIN Bonus b
ON e.empId = b.empId
WHERE b.bonus < 1000 OR bonus IS NULL;
```
---
🔗 LeetCode Link: [Employee Bonus](https://leetcode.com/problems/employee-bonus/?envType=study-plan-v2&envId=top-sql-50)
