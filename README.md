# Sales Insights Data Analysis Project
![Power BI](https://img.shields.io/badge/Power%20BI-v2.139-yellow)
![MySQL](https://img.shields.io/badge/MySQL-v8.40-blue)


## Problem Statement

A hardware company that supplies computer hardware and peripheral devices is experiencing challenges in the following areas:

- `Sales Tracking:` Struggles to dynamically track sales performance in a rapidly growing market.  
- `On-Site Business Analysis:` Difficulty in managing and analyzing on-site business operations effectively.  
- `Cross-Reporting:` Inability to consolidate and analyze data scattered across multiple Excel records.  

### Purpose
The primary purpose of this project is:  
1. To unlock actionable sales insights for sales teams, enabling better decision-making.  
2. To automate data analysis and reduce manual time spent on data engineering tasks.  

### Key Challenges
1. *Sales Growth*: The company is unable to monitor and strategize for consistent sales growth.  
2. `*Declining Overall Sales*: The sales trends indicate a decline in overall performance, requiring in-depth analysis.  

---

## Instructions to Set Up MySQL on Your Local Computer

1. The SQL database dump is provided in the `db_dump.sql` file.  
2. Download the `db_dump.sql` file to your local computer.  
3. Follow the instructions in the tutorial video to import the database into your MySQL environment.  

---

## Data Analysis Using SQL

### Example Queries for Sales Analysis  

1. **Show all customer records**
```sql
   SELECT * FROM customers;
```
   
2. **Show total number of customers**
```sql
SELECT COUNT(*) FROM customers;
```
3.**Show transactions for the Chennai market
(Market code for Chennai is Mark001)** 
```sql
SELECT * FROM transactions WHERE market_code = 'Mark001';
```
4.**Show distinct product codes that were sold in Chennai**
```sql
SELECT DISTINCT product_code FROM transactions WHERE market_code = 'Mark001';
```
5. **Show transactions where the currency is US Dollars**
```sql
SELECT * FROM transactions WHERE currency = "USD";
```
6. **Show transactions in 2020
(Join with the date table)**
```sql
SELECT transactions.*, date.* 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020;
```
7. **Show total revenue in 2020**
```sql
SELECT SUM(transactions.sales_amount) AS total_revenue 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 AND (transactions.currency = "INR" OR transactions.currency = "USD");

```
8. **Show total revenue in January 2020**
```sql
SELECT SUM(transactions.sales_amount) AS total_revenue 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 AND date.month_name = "January" AND (transactions.currency = "INR" OR transactions.currency = "USD");
```
9. **Show total revenue in 2020 for Chennai**
```sql
SELECT SUM(transactions.sales_amount) AS total_revenue 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 AND transactions.market_code = "Mark001";
```


## Data Analysis Using Power BI

```bash
1. Formula to create norm_amount column

= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)
```

### Clone this repository 
```bash
git clone https://github.com/AviralTechie/Sales_Insight.git
```
