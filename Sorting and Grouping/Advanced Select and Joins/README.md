# The Number of Employees Which Report to Each Employee

## Problem Description

We are given a table `Employees` that contains information about employees and their managers.  

### Table: Employees

| Column Name | Type    |
|-------------|---------|
| employee_id | int     |
| name        | varchar |
| reports_to  | int     |
| age         | int     |

- `employee_id` is the column with **unique values**.  
- `reports_to` indicates the **manager's employee_id** that the employee reports to.  
- Some employees do not report to anyone (`reports_to` is `NULL`).  

A **manager** is defined as an employee who has at least **1 other employee reporting to them**.  

We need to report:  
- The `employee_id` and `name` of each manager.  
- The number of employees who report **directly** to them (`reports_count`).  
- The average age of their reports (`average_age`), **rounded to the nearest integer**.  

The result should be ordered by `employee_id`.  

---

## 🎯 Goal

Find all managers, along with the **count of direct reports** and the **average age of those reports**.  

---

## Solution

```sql
SELECT e1.employee_id,
                e1.name,
                COUNT (e2.reports_to) AS reports_count,
                ROUND(AvG(1.0*e2.age),0) AS average_age
FROM Employees e1
INNER JOIN Employees e2
ON e1.employee_id = e2.reports_to
GROUP BY e1.employee_id, e1.name
HAVING COUNT(e2.reports_to) >= 1
ORDER BY e1.employee_id ASC

```

## 🔗 LeetCode Link
[The Number of Employees Which Report to Each Employee](https://leetcode.com/problems/the-number-of-employees-which-report-to-each-employee/description/?envType=study-plan-v2&envId=top-sql-50)
