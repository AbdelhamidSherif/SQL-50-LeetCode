# 🙋‍♂️ Customer Who Visited but Did Not Make Any Transactions

## 🧾 Table Schema

### Visits
| Column Name | Type |
|-------------|------|
| visit_id    | int  |
| customer_id | int  |

- visit_id is the unique identifier for each visit to the mall.

### Transactions
| Column Name    | Type |
|----------------|------|
| transaction_id | int  |
| visit_id       | int  |
| amount         | int  |

- Each transaction is tied to a specific visit via visit_id.

---

## 🎯 Goal

Find customers who **visited the mall** but did **not make any transactions**, and count how many times this occurred for each customer.

---

## ✅ Solution

```sql
SELECT customer_id, COUNT(*) AS count_no_trans
FROM Visits v
LEFT JOIN Transactions t
ON v.visit_id = t.visit_id
WHERE t.visit_id IS NULL
GROUP BY (customer_id)


--Another way
/*
SELECT customer_id, COUNT(*) AS count_no_trans
FROM Visits v
WHERE NOT EXISTS(
    SELECT 1 
    FROM Transactions t
    WHERE v.visit_id = t.visit_id
)
GROUP BY customer_id
*/

--Another way
/*
SELECT customer_id, COUNT(*) AS count_no_trans
FROM Visits v
WHERE visit_id NOT IN(
    SELECT visit_id 
    FROM Transactions t
    WHERE v.visit_id = t.visit_id
)
GROUP BY customer_id
*/
```
## 🔗 LeetCode Link

[LeetCode - Customer Who Visited but Did Not Make Any Transactions](https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/?envType=study-plan-v2&envId=top-sql-50)
