# Banking Console Application

# Overview
The Bank Management System is a console-based application written in Python. It allows admin users to manage multiple bank accounts, while customer users can access their own accounts to deposit, withdraw, and view transaction histories. The system stores data persistently using JSON files.  

## Features
 ### Admin Capabilities
- Create new bank accounts
-	Display all existing accounts
-	Deposit to or withdraw from any account
-	View transaction history of any account
-	Create customer login associated with an account
-	Delete accounts and associated users
-	Save user and account data to files
### Customer Capabilities
-	Deposit money to their own account
-	Withdraw money from their own account
-	View their transaction history

## Main Classes and Functions
1. Account Class
Represents individual bank accounts.
  #### Attributes:
   -	acc_id: Unique ID for the account
   -	name: Account holder’s name
   -	balance: Current balance in the account
   -	transactions: List of transaction tuples
   -	accounts: Class-level list storing all accounts
  #### Methods:
   -	deposit(amount)
   -	withdraw(amount)
   -	display_info()
   -	to_dict() and from_dict() for JSON serialization
   -	save_to_file() and load_from_file() to handle persistent storage
2. User Class
Represents system users (admin or customer).
 Attributes:
  -	username: User login name
  -	password: User password
  -	role: Either “admin” or “customer”
  -	account_id: Linked account ID (for customers)
  -	users: Class-level list storing all users
 Methods:
  -	to_dict() and from_dict() for JSON operations
  -	save_to_file() and load_from_file() to handle persistent storage
3. Helper Functions
 -	find_account_by_id(acc_id) – Finds an account by ID
 -	login() – Prompts login and returns a matching user object
 
### User Interfaces
##### Admin Menu
Displayed to users with role = “admin”
1. Create Account
2. Display All Accounts
3. Deposit
4. Withdraw
5. View Transaction History
6. Save Data
7. Create Customer User
8. Delete Account
9. Exit
Customer Menu
Displayed to users with role = “customer”
1. Deposit
2. Withdraw
3. View Transaction History
4. Exit
 
### Data Storage
##### accounts.json
Stores a list of account dictionaries with fields:
{
  "acc_id": "A101",
  "name": "John Doe",
  "balance": 500.0,
  "transactions": [["Deposit", 500.0]]
}
users.json
Stores a list of user dictionaries:
{
  "username": "john",
  "password": "pass123",
  "role": "customer",
  "account_id": "A101"
}
 
#### Initialization
Upon first run:
-	Loads data from JSON files
-	If no admin user is found, creates default admin (admin / admin123)
 
#### Execution Flow
1.	Load data from files
2.	Authenticate user via login()
3.	Display appropriate menu based on role
4.	Handle selected actions and update data
5.	Save updates to files using save_to_file()
 
#### Limitations
-	No encryption for passwords
-	No input validation (e.g., negative deposit)
-	Single-session memory (no multi-threading or multi-user concurrency)
 
#### Future Enhancements
-	Add GUI using Tkinter or Flask
-	Implement password hashing
-	Add transaction timestamps
-	Integrate SQL or NoSQL databases for better scalability
-	Add email notification for transactions
 
## Conclusion
This Python-based Bank Management System offers a modular, extendable framework for managing simple banking operations in a local environment. It is ideal for educational purposes and as a foundation for larger projects.
