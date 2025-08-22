# Immediate Food Delivery II

## Problem Description

We are given a table `Delivery` that stores information about customer food delivery orders.  

### Table: Delivery

| Column Name                 | Type |
|-----------------------------|------|
| delivery_id                 | int  |
| customer_id                 | int  |
| order_date                  | date |
| customer_pref_delivery_date | date |

- `delivery_id` is the primary key.  
- If `customer_pref_delivery_date = order_date`, the order is **immediate**.  
- Otherwise, the order is **scheduled**.  
- A customer's **first order** is defined as the order with the earliest `order_date`.  
- It is guaranteed that each customer has exactly one first order.  
---
## 🎯 Goal
We need to calculate the **percentage of immediate orders among the first orders** of all customers, rounded to **2 decimal places**.  

---

## Example

**Input:**

**Delivery**
| delivery_id | customer_id | order_date | customer_pref_delivery_date |
|-------------|-------------|------------|-----------------------------|
| 1           | 1           | 2019-08-01 | 2019-08-02                  |
| 2           | 2           | 2019-08-02 | 2019-08-02                  |
| 3           | 1           | 2019-08-11 | 2019-08-12                  |
| 4           | 3           | 2019-08-24 | 2019-08-24                  |
| 5           | 3           | 2019-08-21 | 2019-08-22                  |
| 6           | 2           | 2019-08-11 | 2019-08-13                  |
| 7           | 4           | 2019-08-09 | 2019-08-09                  |

**Output:**
| immediate_percentage |
|----------------------|
| 50.00                |

**Explanation:**
- Customer **1** → First order (id=1) → Scheduled.  
- Customer **2** → First order (id=2) → Immediate.  
- Customer **3** → First order (id=5) → Scheduled.  
- Customer **4** → First order (id=7) → Immediate.  

Out of 4 customers, 2 have immediate first orders → `2/4 * 100 = 50.00`.

---

## ✅ Solution

```sql
SELECT ROUND(100.0 * SUM(CASE WHEN order_date = customer_pref_delivery_date THEN 1 ELSE 0 END) / COUNT(*), 2) AS immediate_percentage
FROM Delivery d1
INNER JOIN (SELECT customer_id, MIN(order_date) first_order_date
 FROM Delivery 
 GROUP BY customer_id) first_orders
 ON d1.customer_id = first_orders.customer_id AND 
 d1.order_date = first_orders.first_order_date;

```

## 🔗 LeetCode Link
[Immediate Food Delivery II](https://leetcode.com/problems/immediate-food-delivery-ii/description/?envType=study-plan-v2&envId=top-sql-50)
