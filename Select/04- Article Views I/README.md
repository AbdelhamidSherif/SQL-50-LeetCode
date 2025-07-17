# 👁️ Article Views I

## 🧾 Table Schema

**Views**
| Column Name | Type | Description                                |
|-------------|------|--------------------------------------------|
| article_id  | int  | ID of the article                          |
| author_id   | int  | ID of the author of the article            |
| viewer_id   | int  | ID of the person who viewed the article    |
| view_date   | date | Date the article was viewed                |

> No primary key. Rows may be duplicated.  
> An author is also a viewer if `author_id = viewer_id`.

---

## 🎯 Goal

Return the IDs of authors who **viewed at least one of their own articles**.

---

## ✅ Solution

```sql
SELECT DISTINCT author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY id;
```
## 🔗 LeetCode Link

[Article Views I](https://leetcode.com/problems/article-views-i/?envType=study-plan-v2&envId=top-sql-50)