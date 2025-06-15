# Task 3 - SQL for Data Analysis

## 📌 Objective

The objective of this task was to perform data analysis using SQL queries on a simulated database. The dataset was designed for a **Movie Streaming Platform** which includes tables for Users, Subscriptions, Movies, and Watch History.

The task included:
- Creating tables and inserting sample data
- Writing SQL queries: SELECT, JOIN, WHERE, AGGREGATE, SUBQUERIES
- Creating Views
- Index optimization

---

## 🔧 Tools Used

- **DB Browser for SQLite**  
  (for database creation, data insertion, and query execution)

- **SQLite (SQL language)**  
  (for executing queries and performing analysis)

- **GitHub**  
  (for uploading project files, screenshots, and documentation)

---

## 🗃️ Dataset Tables

- Users
- Subscriptions
- Movies
- Watch_History

---

## 📊 Queries and Sample Outputs

### 1️⃣ SELECT + WHERE

```sql
SELECT * FROM Users WHERE city = 'New York';

SELECT s.subscription_id, u.name, s.amount_paid 
FROM Subscriptions s
INNER JOIN Users u ON s.user_id = u.user_id;

SELECT u.name, s.subscription_id 
FROM Users u
LEFT JOIN Subscriptions s ON u.user_id = s.user_id;

SELECT user_id, SUM(amount_paid) AS total_paid 
FROM Subscriptions 
GROUP BY user_id;

SELECT movie_id, AVG(watch_duration) AS avg_watch_duration 
FROM Watch_History 
GROUP BY movie_id;

SELECT * FROM Subscriptions 
WHERE amount_paid > (SELECT AVG(amount_paid) FROM Subscriptions);

CREATE VIEW UserSubscriptions AS
SELECT u.name, s.subscription_id, s.amount_paid 
FROM Users u 
JOIN Subscriptions s ON u.user_id = s.user_id;

CREATE INDEX idx_user_id ON Subscriptions(user_id);


Task3-SQL-Data-Analysis/
│
├── README.md
├── task3.sql
└── screenshots/
    ├── select_where.png
    ├── inner_join.png
    ├── left_join.png
    ├── aggregate_function.png
    ├── subquery.png
    ├── create_view.png
    └── index_creation.png
