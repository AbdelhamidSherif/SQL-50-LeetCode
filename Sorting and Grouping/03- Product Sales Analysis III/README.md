# Product Sales Analysis III

## Problem Description

We are given a table `Sales` that stores information about product sales over different years.  

### Table: Sales

| Column Name | Type |
|-------------|------|
| sale_id     | int  |
| product_id  | int  |
| year        | int  |
| quantity    | int  |
| price       | int  |

- `(sale_id, year)` is the **primary key** (combination of columns with unique values).  
- `product_id` is a **foreign key** referencing the `Product` table.  
- Each row represents a sale of a product in a given year.  
- A product may have multiple sales entries in the same year.  
- The `price` column represents the **per-unit price**.  

---

## 🎯 Goal

For each product, determine the **first year** it was sold and return all sales entries for that product in that year.  

The result table should include the following columns:  
- `product_id`  
- `first_year`  
- `quantity`  
- `price`  

---

## Solution

```sql
SELECT s.product_id,
       s.year AS first_year,
       s.quantity,
       s.Price
FROM Sales s
WHERE s.year = (SELECT MIN(year) FROM Sales WHERE product_id = s.product_id)

```

## 🔗 LeetCode Link
[Product Sales Analysis III](https://leetcode.com/problems/product-sales-analysis-iii/description/?envType=study-plan-v2&envId=top-sql-50)