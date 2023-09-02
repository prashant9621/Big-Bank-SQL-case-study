# Big-Bank-SQL-case-study
![Screenshot (31)](https://github.com/prashant9621/Big-Bank-SQL-case-study/assets/136049491/4a467464-e2d7-405c-843e-42cdc04000ba)


**Objective:**
As a Financial Analyst, we have been tasked to find out about our customers and their banking behavior.

**Task 1: Examine Customer Information**
1. Examine the accounts they hold and the type of transactions they make to develop greater insights into your customers.

**Data Source:**
The Challenge is organized by Steel Data, and the dataset is available for download from their [website](https://www.steeldata.com/dataset).

**Question 1:**
What are the names of all the customers who live in New York?

**SQL Query:**
```sql
SELECT CONCAT(firstname, " ", lastname) AS name
FROM customers
WHERE city = "New York";







![Screenshot (32)](https://github.com/prashant9621/Big-Bank-SQL-case-study/assets/136049491/21f9849b-5a11-43af-a6cd-cfb6a0d1ef90)





Q2-What is the total number of accounts in the accounts table?



ans
select count(*) as total_accounts
from accounts;




Q3-What is the total balance of all checkig accounts?




ans-
select sum(balance) as total_balance
from accounts where accounttype="checking" ;





Q4-what is the total balance of all accounts associated with customers who live in los angeles?





ans-
select sum(balance) as total_balance
from accounts a 
inner join customers c on c.customerid=a.customerid
where c.city="Los angeles" ;






Q5-which branch has the highest total balance across all of its accounts?




ans-
select b.branchname,sum(balance) as total_balance
from accounts a
inner join branches b using(branchid)
group by 1 order by2 desc limit 1 ;







Q6-which customer has the highest total alance across all of their accounts,including savings and checking accounts?





ans-
select concat(firstname," ",lastname) as full name
sum(balance) as total_balance
from accounts a 
inner join customers c using (customerid)
where a.accounttype in ("savings","checking")
group by 1 order by 2 desc limit 1;



![Screenshot (34)](https://github.com/prashant9621/Big-Bank-SQL-case-study/assets/136049491/3f7bb3d6-7fc3-4ce0-bcc5-19622b4ce13b)







Insights


![WhatsApp Image 2023-09-01 at 11 07 48 PM](https://github.com/prashant9621/Big-Bank-SQL-case-study/assets/136049491/674d7416-2aba-447a-8a88-59168f048b2f)















