# Sales Insights Data-Analysis-project

# Data Analysis Using SQL

1. Show all customer records

      SELECT * FROM customers;

2. Show total number of customers

      SELECT count(*) FROM customers;

3. Show transactions for Chennai market (market code for chennai is Mark001

      SELECT * FROM transactions where market_code='Mark001';

4. Show distrinct product codes that were sold in chennai

      SELECT distinct product_code FROM transactions where market_code='Mark001';

5. Show transactions where currency is US dollars

      SELECT * from transactions where currency="USD"

6. Show transactions in 2020 join by date table

     SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

7. Show total revenue in year 2020,

     SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

8. Show total revenue in year 2020, January Month,

     SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

9. Show total revenue in year 2020 in Chennai

     SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

   #Data Analysis Using Power BI (ETL)

Now, I'm integrating MySQL Source in Power BI tool and building dashboard

-> Removing unnecessary

-> debugging errors

1. Formula to create norm_amount column
     = Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)

2. Merging Two tables sales transactions  and sales transactions (2)

3. Formula to calculate Revenue
     = SUM('sales transactions'[Normalise_sales_amount])

4. Formula to calculate Sales Qty
     = SUM('sales transactions'[sales_qty])

5. Formula to calculate Total Profit Margin
    = SUM('sales transactions'[profit_margin])
