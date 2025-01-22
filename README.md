## Sales Insights Data Analysis Project

### Problem Statement
Problem Statement
A hardware company that supplies computer hardware and peripheral devices is experiencing challenges in the following areas:

* `Sales Tracking:` Struggles to dynamically track sales performance in a rapidly growing market.
* `On-Site Business Analysis:` Difficulty in managing and analyzing on-site business operations effectively.
* `Cross-Reporting:` Inability to consolidate and analyze data scattered across multiple Excel records.

`1. Purpose :` 
* `The primary purpose of this project is:`
1. To unlock actionable sales insights for sales teams, enabling better decision-making.
2. To automate data analysis and reduce manual time spent on data engineering tasks.

`2. Key Challenges`
1. `Sales Growth:` The company is unable to monitor and strategize for consistent sales growth.
2. `Declining Overall Sales:` The sales trends indicate a decline in overall performance, requiring in-depth analysis.

## Instructions to setup mysql on your local computer

1. SQL database dump is in db_dump.sql file above. Download `db_dump.sql` file to your local computer and import it as per instructions given in the tutorial video

### Data Analysis Using SQL

1. Show all customer records

```SELECT * FROM customers;```

2. Show total number of customers

    ```SELECT count(*) FROM customers;```

3. Show transactions for Chennai market (market code for chennai is Mark001

    ```SELECT * FROM transactions where market_code='Mark001';```

4. Show distrinct product codes that were sold in chennai

    ```SELECT distinct product_code FROM transactions where market_code='Mark001';```

5. Show transactions where currency is US dollars

    ```SELECT * from transactions where currency="USD"```

6. Show transactions in 2020 join by date table

    ```SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;```

7. Show total revenue in year 2020,

    ```SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";```
	
8. Show total revenue in year 2020, January Month,

    ```SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");```

9. Show total revenue in year 2020 in Chennai
    
`SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column

```= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)```



