# Big-Bank-SQL-case-study
![Screenshot (31)](https://github.com/prashant9621/Big-Bank-SQL-case-study/assets/136049491/4a467464-e2d7-405c-843e-42cdc04000ba)


Objective
1-As a Financial analysts,we have been tasked to find out about our customers and their banking behavior.


2-Examine the accounts they hold and type of transactions they make to develop greater insights into your customers.



3-The Challenge is organised by steel data and dataset is download from their Website.


Q1-What are the names of all the customers who live in new york?
Ans-
select cocat(firstname," ",lastname) as name
from customers
where city="New york" ;
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


Insights-














