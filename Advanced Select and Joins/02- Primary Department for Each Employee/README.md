
# Primary Department for Each Employee

## 📘 Problem Statement
We are given a table `Employee` that contains information about employees and the departments they belong to.  
Each employee can belong to multiple departments, and one of them is marked as their **primary department** using the column `primary_flag`.  

- If an employee belongs to **only one department**, then the `primary_flag` is `'N'`, but that department should still be considered as their primary department.  
- If an employee belongs to **multiple departments**, the department with `primary_flag = 'Y'` should be selected.  

We need to write a query to report **all employees with their primary department**.  

---

## 📝 Table: Employee

| Column Name   | Type    |
|---------------|---------|
| employee_id   | int     |
| department_id | int     |
| primary_flag  | varchar |

- `(employee_id, department_id)` is the **primary key**.  
- `primary_flag` is ENUM: `'Y'` (primary) or `'N'` (not primary).  

---

## 🎯 Goal
Return a result table with:  

| Column Name   | Type |
|---------------|------|
| employee_id   | int  |
| department_id | int  |

- Report each employee **with their primary department**.  
- If the employee has only one department, return that one.  
- Order does not matter.  

---

## 🔎 Example

### Input:
Employee table:

| employee_id | department_id | primary_flag |
|-------------|---------------|--------------|
| 1           | 1             | N            |
| 2           | 1             | Y            |
| 2           | 2             | N            |
| 3           | 3             | N            |
| 4           | 2             | N            |
| 4           | 3             | Y            |
| 4           | 4             | N            |

### Output:
| employee_id | department_id |
|-------------|---------------|
| 1           | 1             |
| 2           | 1             |
| 3           | 3             |
| 4           | 3             |

---

## 💡 Explanation
- Employee **1** belongs only to department 1 → primary department is `1`.  
- Employee **2** belongs to dept `1` and `2`, with `primary_flag='Y'` for dept `1` → primary department is `1`.  
- Employee **3** belongs only to dept `3` → primary department is `3`.  
- Employee **4** belongs to depts `2,3,4`, but only dept `3` has `primary_flag='Y'` → primary department is `3`.  

---

## ✅ Solution (T-SQL)

```sql
-- /* Write your T-SQL query statement below */

-- SELECT employee_id,
--         department_id
-- FROM Employee
-- WHERE employee_id IN(
--                     SELECT employee_id
--                     FROM Employee
--                     GROUP BY employee_id
--                     Having COUNT(employee_id)=1
-- )
-- OR primary_flag IN(SELECT primary_flag FROM Employee WHERE primary_flag='Y')

/*Another Solution*/
-- SELECT employee_id,
--         department_id
-- FROM Employee
-- WHERE primary_flag='Y'

-- UNION

-- SELECT employee_id,
--         department_id
-- FROM Employee
-- WHERE employee_id IN(
--                     SELECT employee_id
--                     FROM Employee
--                     GROUP BY employee_id
--                     Having COUNT(employee_id)=1
-- )

/*Another Solution*/
SELECT employee_id,
        department_id
FROM Employee
WHERE primary_flag='Y'
OR
employee_id IN(
                SELECT employee_id
                FROM Employee
                GROUP BY employee_id
                Having COUNT(employee_id)=1
)
         



```

## 🔗 LeetCode Link
[Primary Department for Each Employee](https://leetcode.com/problems/primary-department-for-each-employee/description/?envType=study-plan-v2&envId=top-sql-50)
