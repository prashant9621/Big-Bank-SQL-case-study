
# Big-Bank-SQL-case-study

**Objective:**
As a Financial Analyst, we have been tasked to find out about our customers and their banking behavior.

## Task 1: Examine Customer Information
1. Examine the accounts they hold and the type of transactions they make to develop greater insights into your customers.

**Data Source:**
The Challenge is organized by Steel Data, and the dataset is available for download from their [website](https://www.steeldata.com/dataset).

### Question 1:
What are the names of all the customers who live in New York?

**SQL Query:**
```sql
SELECT CONCAT(firstname, " ", lastname) AS name
FROM customers
WHERE city = "New York";


### Question 2: 
What is the total number of accounts in the accounts table?

**SQL Query:**
```sql
SELECT COUNT(*) AS total_accounts
FROM accounts;
Question 3:
What is the total balance of all checking accounts?
SELECT SUM(balance) AS total_balance
FROM accounts
WHERE accounttype = "checking";
Question 4:
What is the total balance of all accounts associated with customers who live in Los Angeles?
SELECT SUM(balance) AS total_balance
FROM accounts a 
INNER JOIN customers c ON c.customerid = a.customerid
WHERE c.city = "Los Angeles";
Question 5:
Which branch has the highest total balance across all of its accounts?
SELECT b.branchname, SUM(balance) AS total_balance
FROM accounts a
INNER JOIN branches b USING(branchid)
GROUP BY 1
ORDER BY 2 DESC
LIMIT 1;
Question 6:
Which customer has the highest total balance across all of their accounts, including savings and checking accounts?
SELECT CONCAT(firstname, " ", lastname) AS full_name,
SUM(balance) AS total_balance
FROM accounts a 
INNER JOIN customers c USING (customerid)
WHERE a.accounttype IN ("savings", "checking")
GROUP BY 1
ORDER BY 2 DESC
LIMIT 1;
📌 Important Insights

👫 John Doe and Jane Doe are customers who lived in New York.

🏦 There are a total of 16 customer accounts in the accounts table.

💰 The total balance of all Checking accounts is $31,000.

💰 The total balance of all accounts associated with customers who live in Los Angeles is $75,000.

🏦 The Uptown branch has the highest average account balance.

💼 Micheal Lee has the highest current balance in his account.

🏦 North Beach branch has the highest total balance account across all of its accounts.

📊 The Main and South Bay branches have the highest number of transactions.






























