# Banking System Console Application

## Overview

This is a simple menu-based console application that simulates a basic banking system for managing customer accounts and transactions. The application is developed using Core Java, MySQL, and JDBC. 

## Features

1. **Account Management:**
   - Add new customer accounts
   - View account details
   - Update account information
   - Close accounts

2. **Transaction Management:**
   - Deposit funds into an account
   - Withdraw funds from an account
   - Transfer funds between accounts
   - View transaction history for an account

## Database Schema

### Customer Table
| Column        | Type         |
|---------------|--------------|
| customer_id   | INT          |
| name          | VARCHAR(100) |
| email         | VARCHAR(100) |
| phone_number  | VARCHAR(15)  |

### Account Table
| Column        | Type         |
|---------------|--------------|
| account_id    | INT          |
| customer_id   | INT          |
| account_type  | VARCHAR(50)  |
| balance       | DECIMAL(10,2)|

### Transaction Table
| Column           | Type         |
|------------------|--------------|
| transaction_id   | INT          |
| account_id       | INT          |
| transaction_type | VARCHAR(50)  |
| amount           | DECIMAL(10,2)|
| transaction_date | TIMESTAMP    |

## Setup Instructions

### Prerequisites

1. Java Development Kit (JDK) 8 or higher
2. MySQL Server
3. Eclipse IDE (or any preferred Java IDE)
4. MySQL Connector/J (JDBC driver for MySQL)

### Steps

1. **Create the Database**
   - Open your MySQL client and execute the following SQL commands to create the database and tables:
     ```sql
     CREATE DATABASE banking_system;

     USE banking_system;

     CREATE TABLE Customer (
         customer_id INT AUTO_INCREMENT PRIMARY KEY,
         name VARCHAR(100),
         email VARCHAR(100),
         phone_number VARCHAR(15)
     );

     CREATE TABLE Account (
         account_id INT AUTO_INCREMENT PRIMARY KEY,
         customer_id INT,
         account_type VARCHAR(50),
         balance DECIMAL(10, 2),
         FOREIGN KEY (customer_id) REFERENCES Customer(customer_id)
     );

     CREATE TABLE Transaction (
         transaction_id INT AUTO_INCREMENT PRIMARY KEY,
         account_id INT,
         transaction_type VARCHAR(50),
         amount DECIMAL(10, 2),
         transaction_date TIMESTAMP,
         FOREIGN KEY (account_id) REFERENCES Account(account_id)
     );
     ```

2. **Open the Project in Eclipse**
   - Download and extract the provided source code.
   - Open Eclipse IDE.
   - Import the project by selecting `File -> Import -> General -> Existing Projects into Workspace`, then select the root directory of the extracted source code.

3. **Configure Database Connection**
   - Open the `DBConnection.java` file located in the `src/db` package.
   - Update the database URL, username, and password:
     ```java
     private static final String URL = "jdbc:mysql://localhost:3306/banking_system";
     private static final String USER = "your_username";
     private static final String PASSWORD = "your_password";
     ```

4. **Add MySQL Connector/J to Project**
   - Download the MySQL Connector/J from the official website.
   - In Eclipse, right-click on your project, go to `Build Path` -> `Configure Build Path`.
   - Under the `Libraries` tab, click `Add External JARs` and select the MySQL Connector/J JAR file you downloaded.

5. **Run the Application**
   - Locate `Main.java` in the `src` folder.
   - Right-click on `Main.java` and select `Run As -> Java Application`.

## Usage

After running the application, you will see a menu with options to manage accounts and transactions. Follow the prompts to:

1. Add new customer accounts
2. View account details
3. Update account information
4. Close accounts
5. Deposit funds into an account
6. Withdraw funds from an account
7. Transfer funds between accounts
8. View transaction history for an account

### Example Commands

1. **Add Customer**:
   - Enter customer name: John Doe
   - Enter customer email: john@example.com
   - Enter customer phone number: 123-456-7890

2. **Add Account**:
   - Enter customer ID: 1
   - Enter account type (Savings/Checking): Savings
   - Enter initial balance: 1000.00

3. **Deposit Funds**:
   - Enter account ID: 1
   - Enter amount to deposit: 500.00

4. **View Transaction History**:
   - Enter account ID: 1

## Troubleshooting

If you encounter issues:

- Ensure your MySQL server is running.
- Verify the database URL, username, and password in `DBConnection.java`.
- Ensure MySQL Connector/J is added to the project build path.

For further assistance, consult the project documentation or reach out to the project maintainers.

