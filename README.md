Core Banking System Enhancement

Overview

This project automates the processing of banking transactions and updates customer profiles using Profile Scripting Language (PSL). It showcases how to handle transaction logs, adjust account balances, and maintain accurate customer records—key functionalities in core banking systems.

Features

Automated Profile Updates:

Adjust account balances based on transaction type (credit or debit).

Update the LastTransactionDate field for each customer.

Error Logging:

Identifies and logs errors for transactions with missing customer IDs or invalid data.

Efficient Design:

Processes data from CSV files and updates customer profiles in-memory for better performance.

Datasets

1. Transaction Dataset

File: small_transaction_data_with_currency.csv

Description: Contains 10,000 transactions in USD.

Fields:

TransactionID: Unique identifier for each transaction.

CustomerID: Associated customer's unique ID.

TransactionType: Type of transaction (credit or debit).

Amount: Transaction amount (in USD).

Currency: Currency type (all USD).

TransactionDate: Date of the transaction.

2. Customer Profile Dataset

File: small_customer_profiles.csv

Description: Contains 1,000 unique customer profiles.

Fields:

CustomerID: Unique identifier for each customer.

AccountBalance: Current balance in the customer's account (USD).

LastTransactionDate: Date of the last recorded transaction.

Workflow

High-Level Diagram

graph TD
    A[Transaction Dataset] -->|Load| B[Process Transactions]
    B -->|Match Customer Profiles| C[Update Profiles]
    C --> D[Save Updated Profiles]
    B --> E[Log Errors]

Process

Load Data:

Load transaction data from small_transaction_data_with_currency.csv.

Load customer profiles from small_customer_profiles.csv.

Process Transactions:

For each transaction:

Identify the corresponding customer profile.

Update the account balance and last transaction date.

Log errors for missing or invalid profiles.

Output Results:

Save updated customer profiles back to the file.

Generate a log file (transaction_logs.txt) detailing errors and status.

Setup and Execution

Prerequisites

PSL Interpreter: Ensure the Profile Scripting Language (PSL) interpreter is installed and configured.

Files:

Place small_transaction_data_with_currency.csv and small_customer_profiles.csv in the working directory.

Include the PSL script (process_transactions.psl) in the same directory.

Steps to Run

Execute the PSL script:

psl_interpreter process_transactions.psl

Monitor the outputs:

Updated customer profiles will be saved in updated_customer_profiles.csv.

Logs will be stored in transaction_logs.txt.

Outputs

Updated Customer Profiles:

File: updated_customer_profiles.csv

Description: Contains updated account balances and the last transaction date for each customer.

Transaction Logs:

File: transaction_logs.txt

Description: Logs details of processed transactions and any errors encountered.

Future Enhancements

Multi-Currency Support:

Extend the script to handle multiple currencies with exchange rate conversion.

Real-Time Processing:

Integrate the script with streaming platforms (e.g., Kafka) for real-time transaction updates.

Fraud Detection:

Add rules to flag suspicious transactions based on patterns or thresholds.
