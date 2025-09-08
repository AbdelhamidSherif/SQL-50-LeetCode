
# Customers Who Bought All Products

## Problem Description

We are given two tables:  

### Table: Customer

| Column Name | Type |
|-------------|------|
| customer_id | int  |
| product_key | int  |

- This table may contain **duplicate rows**.  
- `customer_id` is not NULL.  
- `product_key` is a foreign key referencing the `Product` table.  

### Table: Product

| Column Name | Type |
|-------------|------|
| product_key | int  |

- `product_key` is the **primary key**.  

---

## 🎯 Goal

Find all **customer IDs** from the `Customer` table who bought **all the products** listed in the `Product` table.  

Return the result table in **any order**.  

---

## Example 1

**Input:**  

**Customer**  
| customer_id | product_key |
|-------------|-------------|
| 1           | 5           |
| 2           | 6           |
| 3           | 5           |
| 3           | 6           |
| 1           | 6           |

**Product**  
| product_key |
|-------------|
| 5           |
| 6           |

**Output:**  
| customer_id |
|-------------|
| 1           |
| 3           |

**Explanation:**  
- Customer **1** bought products `{5, 6}` → ✅ Bought all.  
- Customer **2** bought product `{6}` → ❌ Missing 5.  
- Customer **3** bought products `{5, 6}` → ✅ Bought all.  

So, the answer is customers `{1, 3}`.  

---

## Solution

```sql
-- SELECT customer_id 
-- FROM Customer c
-- GROUP BY customer_id
-- HAVING COUNT(DISTINCT c.product_key) = (SELECT COUNT(DISTINCT p.product_key)
-- FROM Product p)

-- Another solution
SELECT c.customer_id
FROM Customer c
 JOIN Product p ON c.product_key = p.product_key
GROUP BY c.customer_id
HAVING COUNT(DISTINCT c.product_key) = (SELECT COUNT(DISTINCT product_key) FROM Product)

```

## 🔗 LeetCode Link
[Customers Who Bought All Products](https://leetcode.com/problems/customers-who-bought-all-products/description/?envType=study-plan-v2&envId=top-sql-50)
