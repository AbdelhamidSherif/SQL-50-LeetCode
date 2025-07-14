# 🌍 Big Countries

## 🧾 Table Schema

**World**
| Column Name | Type    | Description                       |
|-------------|---------|-----------------------------------|
| name        | varchar | Country name (Primary key)        |
| continent   | varchar | Continent                         |
| area        | int     | Area in km²                       |
| population  | int     | Population count                  |
| gdp         | bigint  | Gross Domestic Product            |

---

## 🎯 Goal

Get the `name`, `population`, and `area` of countries that are considered **big**:

- area ≥ 3,000,000 **OR**
- population ≥ 25,000,000

---

## ✅ Solution

```sql
SELECT name, population, area
FROM World
WHERE area >= 3000000 OR population >= 25000000;
```
## 🔗 LeetCode Link

[Big Countries](https://leetcode.com/problems/big-countries/?envType=study-plan-v2&envId=top-sql-50)