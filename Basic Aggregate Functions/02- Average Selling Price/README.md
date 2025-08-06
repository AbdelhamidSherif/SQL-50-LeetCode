# 🧮 Average Selling Price

## 🧾 Table Schemas

### `Prices`

| Column Name | Type | Description |
|-------------|------|-------------|
| product_id  | int  | Product identifier |
| start_date  | date | Price validity start date |
| end_date    | date | Price validity end date |
| price       | int  | Price during the period |

> 🔑 `(product_id, start_date, end_date)` is the **primary key**.  
> 📌 For each product, price periods do **not overlap**.

---

### `UnitsSold`

| Column Name    | Type | Description |
|----------------|------|-------------|
| product_id     | int  | Product identifier |
| purchase_date  | date | Date of purchase |
| units          | int  | Number of units sold |

> 🔁 This table may contain **duplicate rows**.

---

## 🎯 Goal

Calculate the **average selling price** for each product using the formula:

Average selling price = Total Price of Product / Number of products sold.

- Match sales to the correct price based on the **purchase date falling within a price period**.
- Round the final `average_price` to **two decimal places**.
- If a product has no sales, the average price is **0**.

---

## ✅ Solution

```sql
SELECT p.product_id,
       COALESCE(ROUND(SUM(u.units * p.price * 1.0) / SUM(u.units), 2), 0) AS average_price
FROM Prices p
LEFT JOIN UnitsSold u
ON p.product_id = u.product_id AND purchase_date BETWEEN p.start_date AND p.end_date
GROUP BY p.product_id;

```
## 🔗 LeetCode Link

[Average Selling Price](https://leetcode.com/problems/average-selling-price/?envType=study-plan-v2&envId=top-sql-50)
