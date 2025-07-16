# 📊 Product Sales Analysis I

## 🧾 Table Schema

**Sales**
| Column Name | Type | Description                                     |
|-------------|------|-------------------------------------------------|
| sale_id     | int  | Composite PK (with year)                        |
| product_id  | int  | Foreign key referencing Product table           |
| year        | int  | Year of the sale                                |
| quantity    | int  | Number of units sold                            |
| price       | int  | Price per unit                                  |

**Product**
| Column Name  | Type    | Description               |
|--------------|---------|---------------------------|
| product_id   | int     | Primary key               |
| product_name | varchar | Name of the product       |

---

## 🎯 Goal

Report the `product_name`, `year`, and `price` for each sale in the `Sales` table.

---

## ✅ Solution

```sql
SELECT p.product_name, s.year, s.price
FROM Sales s
JOIN Product p
ON s.product_id = p.product_id;
```
## 🔗 LeetCode Link

[Product Sales Analysis I](https://leetcode.com/problems/product-sales-analysis-i/description/?envType=study-plan-v2&envId=top-sql-50)