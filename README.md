#  Retail Sales Analysis using PostgreSQL

##  Project Overview

This project analyzes retail sales transaction data to uncover revenue trends, customer purchasing behavior, and product category performance using PostgreSQL.

The objective is to simulate a real-world business scenario where SQL is used to extract actionable insights for decision-making.

---

##  Dataset Information

- Total Records: 5,000+ transactions  
- Time Period: 2022  
- Unique Customers: 1,000+  
- Product Categories: Clothing, Beauty, Electronics  
- Database Name: `p1_retail_db`

---

##  Database Schema

### Table: `retail_sales`

| Column Name      | Data Type |
|------------------|----------|
| transactions_id  | INT (Primary Key) |
| sale_date        | DATE |
| sale_time        | TIME |
| customer_id      | INT |
| gender           | VARCHAR |
| age              | INT |
| category         | VARCHAR |
| quantity         | INT |
| price_per_unit   | FLOAT |
| cogs             | FLOAT |
| total_sale       | FLOAT |

---

##  SQL Concepts Used

- SELECT Statements  
- WHERE, GROUP BY, HAVING  
- Aggregate Functions (SUM, AVG, COUNT)  
- CTE (Common Table Expressions)  
- Window Functions (RANK, LAG)  
- CASE Statements  
- Data Cleaning (NULL Handling)  
- Date & Time Functions  

---

##  Business Questions Answered

1. What are the top revenue-generating categories?
2. Which month had the highest average sales?
3. Who are the top 5 highest-spending customers?
4. How many unique customers purchased from each category?
5. What time of day generates the most transactions?
6. Are there high-value transactions (>1000)?

---

##  Data Cleaning Process

- Identified NULL values across columns  
- Removed incomplete transaction records  
- Verified unique customer and category counts  

---

##  Key Business Insights

- Clothing category generated the highest total revenue.
- Afternoon shift recorded the maximum number of transactions.
- Top 5 customers contributed a significant percentage of total sales.
- High-value transactions (>1000) indicate strong premium purchase behavior.
- November showed peak sales performance, suggesting seasonal demand.

---

##  Sample Advanced Query (Window Function)

```sql
SELECT 
       year,
       month,
       avg_sale
FROM 
(    
SELECT 
    EXTRACT(YEAR FROM sale_date) as year,
    EXTRACT(MONTH FROM sale_date) as month,
    AVG(total_sale) as avg_sale,
    RANK() OVER(
        PARTITION BY EXTRACT(YEAR FROM sale_date) 
        ORDER BY AVG(total_sale) DESC
    ) as rank
FROM retail_sales
GROUP BY 1, 2
) as t1
WHERE rank = 1;
```

---

##  Business Recommendations

- Increase marketing efforts during peak months.
- Implement loyalty programs targeting top customers.
- Promote premium products during afternoon peak hours.
- Optimize inventory for top-performing categories.

---

##  How to Run This Project

1. Clone the repository
2. Create database `p1_retail_db`
3. Run table creation script
4. Import dataset
5. Execute analysis queries

---

## 👤 Author

**Aamir Iqbal**  
SQL Data Analyst | PostgreSQL | Data Analytics  

---

 If you found this project useful, feel free to star the repository!
