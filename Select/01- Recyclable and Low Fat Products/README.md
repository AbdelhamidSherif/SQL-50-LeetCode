# 🥗 Recyclable and Low Fat Products

## 🧾 Table Schema

**Products**
| Column Name | Type  | Description                          |
|-------------|-------|--------------------------------------|
| product_id  | int   | Primary key                          |
| low_fats    | enum  | 'Y' if product is low fat, else 'N'  |
| recyclable  | enum  | 'Y' if product is recyclable, else 'N' |

---

## 🎯 Goal

Get `product_id`s of products that are:
- Low fat (`low_fats = 'Y'`)
- AND recyclable (`recyclable = 'Y'`)

---

## ✅ Solution

```sql
SELECT product_id
FROM Products
WHERE low_fats = 'Y' AND recyclable = 'Y';
```
## 🔗 LeetCode Link

[Recyclable and Low Fat Products](https://leetcode.com/problems/recyclable-and-low-fat-products/?envType=study-plan-v2&envId=top-sql-50)