# Salesforce CPQ and Billing Finance Transaction to NetSuite Demo
## Overview
This GitHub repository contains the artifacts for the Salesforce CPQ and Billing to NetSuite Demo.
The purpose of this repository is to help Salesforce CPQ and Billing customers get a head start on setting up the following integrations:
* Salesforce Billing objects (Invoice, Credit Note, Payments) to Salesforce Finance Transactions
* Salesforce Finance Transactions to NetSuite

## Scenarios supported by these MuleSoft projects:
1. Post Invoices w/ Lines from Salesforce Billing (including taxes)
2. Post Standalone Payments against an Account
3. Post Credits w/ Lines from Salesforce Billing (including taxes)

![Overview](images/Salesforce_FinTran_to_NetSuite.gif)

## Description of the MuleSoft projects included in this repository:
### Scenario 1 projects (Post Invoices w/ Lines from Salesforce Billing (with taxes):
#### 1. invoice-to-financial-transaction
This project will be triggered when Salesforce Invoices are changed to a “Posted” status.  When this happens, a set of new  FinanceTransactions will be created: One for the posted Invoice (with a reference entity type of “Invoice”), plus additional FinanceTransactions for each of the Invoice Lines (with a reference entity type of “Invoice line”).

#### 2. financial-transaction-invoice-to-netsuite
This project will be triggered whenever a new FinanceTransaction record of reference entity type “Invoice” is created.  It will then create a corresponding Invoice in NetSuite based on the Salesforce Invoice along with it’s associated Invoice Lines based on the products available in the NetSuite product catalog (Inventory Items as they are called in NetSuite), NetSuite accounting period, and tax rate.

### Scenario 2 projects (Post Standalone Payments against an Account):
#### 1. payment-to-financial-transaction
Description goes here

#### 2. financial-transaction-payments-to-netsuite
Description goes here

### Scenario 3 projects (Post Credits w/ Lines from Salesforce Billing (with taxes):
#### 1. credit-note-to-finance-transaction
Description goes here

#### 2. financial-transaction-credit-memo-to-netsuite
Description goes here

### Other projects:
#### 8. salesforce-cpq-netsuite-gartner

## How to get access to these projects
