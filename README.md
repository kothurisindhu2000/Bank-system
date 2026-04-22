# 🏦 Banking Management System (CLI-Based)

## 📌 Overview
This project is a console-based Banking Management System developed in Python. It enables administrators to manage multiple bank accounts and customer users, while customers can securely access and operate their own accounts.

The system uses JSON-based persistent storage and includes enhanced features such as auto-generated account IDs, validation rules, role-based access control, and email-based OTP authentication (2FA).

---

## 🚀 Key Features

### 🔐 Security & Authentication
- Username & Password login
- Email-based OTP verification (2FA)
- OTP expiration and retry limit
- Mandatory email configuration for login

---

### 🧾 Account Management
- Auto-generated unique Account IDs (e.g., ACC1001)
- Create and delete accounts
- Deposit and withdraw funds
- View transaction history

---

### 👨‍💼 Admin Capabilities
- Manage all accounts
- View all customer data
- Create customer users with linked accounts
- Delete accounts and associated users
- Save system data

---

### 👤 Customer Capabilities
- Access only their own account
- Deposit and withdraw funds
- View personal transaction history

---

### ⚙️ Data Persistence
- Data stored in:
  - accounts.json
  - users.json
- Automatic load and save functionality

---

## System Architecture

### 1. Account Class
Represents bank accounts.

Attributes:
- acc_id – Unique account ID  
- name – Account holder name  
- balance – Current balance  
- transactions – Transaction history  

Methods:
- deposit(), withdraw()
- display_info()
- to_dict() / from_dict()
- save_to_file() / load_from_file()

---

### 2. User Class
Represents system users.

Attributes:
- username
- password
- role (admin / customer)
- account_id
- email (used for OTP)

Methods:
- JSON serialization methods
- File persistence methods

---

### 3. Core Functions
- login() – Authenticates user + OTP verification  
- verify_otp() – Handles OTP generation, expiry, and validation  
- generate_account_id() – Auto ID generation  
- find_account_by_id() – Account lookup  

---

## 🖥️ User Interface

### Admin Menu
1. Create Account  
2. Display All Accounts  
3. Deposit  
4. Withdraw  
5. View Transaction History  
6. Save Data  
7. Create Customer User  
8. Delete Account  
9. Exit  

---

### Customer Menu
1. Deposit  
2. Withdraw  
3. View Transaction History  
4. Exit  

---

## 📁 Data Format

### accounts.json
json {   "acc_id": "ACC1001",   "name": "John Doe",   "balance": 500.0,   "transactions": [["Deposit", 500.0]] } 

### users.json
json {   "username": "john",   "password": "pass123",   "role": "customer",   "account_id": "ACC1001",   "email": "john@example.com" } 

---

## ⚙️ Setup Instructions (IMPORTANT)

This application uses email-based OTP authentication.

### To run the project:

1. Enable 2-Step Verification in your Gmail account  
2. Generate a Google App Password  
3. Configure environment variables:

bash BANK_APP_EMAIL=your_email@gmail.com BANK_APP_EMAIL_PASSWORD=your_app_password 

OR configure in launch.json:

json "env": {   "BANK_APP_EMAIL": "your_email@gmail.com",   "BANK_APP_EMAIL_PASSWORD": "your_app_password" } 

⚠️ Without this configuration, login will fail.

---

## 🔄 Execution Flow
1. Load data from JSON files  
2. User login (username + password)  
3. OTP sent to registered email  
4. OTP verification  
5. Role-based menu displayed  
6. Perform operations  
7. Save updates  

---

## ⚠️ Limitations
- Passwords are stored in plain text (no hashing)
- CLI-based (no graphical interface)
- No multi-user concurrency
- Depends on external email configuration

---

## 🔮 Future Enhancements
- Password hashing (security improvement)
- GUI (Tkinter / Web app)
- Database integration (SQL/NoSQL)
- Transaction timestamps
- SMS/email notifications for transactions

---

## 📌 Conclusion
This project demonstrates a secure and modular CLI banking system with real-world concepts such as 2FA authentication, role-based access control, and persistent storage. It serves as a strong foundation for building scalable financial application.