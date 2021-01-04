# Salesforce CPQ and Billing Finance Transaction to NetSuite Demo
## Overview
This GitHub repository contains the artifacts for the Salesforce CPQ and Billing to NetSuite Demo.
The purpose of this repository is to help Salesforce CPQ and Billing customers get a head start on setting up the following integrations:
* Salesforce Billing objects (Invoice, Credit Note, Payments) to Salesforce Finance Transactions
* Salesforce Finance Transactions to NetSuite

[Read more about Finance Transactions in Salesforce Billing](https://help.salesforce.com/articleView?id=blng_finance_logging_intro.htm&type=5)

## Scenarios supported by these MuleSoft projects:
1. Post Invoices w/ Lines from Salesforce Billing (including taxes)
2. Post Standalone Payments against an Account
3. Post Credits w/ Lines from Salesforce Billing (including taxes)

![Overview](images/Salesforce_FinTran_to_NetSuite.gif)

## Description of the MuleSoft projects included in this repository:
### Scenario 1 projects (Post Invoices w/ Lines from Salesforce Billing (with taxes):
#### invoice-to-finance-transaction
This project will be triggered when Invoices are “Posted” in Salesforce Billing.  When this happens, a set of new  FinanceTransactions will be created: One for the posted Invoice (with a reference entity type of “Invoice”), plus additional FinanceTransactions for each of the Invoice Lines (with a reference entity type of “Invoice line”) within the Invoice.

#### finance-transaction-invoice-to-netsuite
This project will be triggered whenever a new FinanceTransaction record of reference entity type “Invoice” is created.  It will then create a corresponding Invoice in NetSuite based on the Salesforce Billing Invoice along with it’s associated Invoice Lines based on the products available in the NetSuite product catalog (Inventory Items as they are called in NetSuite), NetSuite accounting period, and tax rate.

**Note:** The products corresponding to the invoice lines need to be available in the NetSuite product catalog (Inventory Items as they are called in NetSuite). Otherwise, the Invoice creation will fail.
The account related to the invoice needs to be present in NetSuite for successful Invoice creation.

### Scenario 2 projects (Post Standalone Payments against an Account):
#### payment-to-finance-transaction
This project will be triggered when Salesforce Billing Payments are “Posted”.  When this happens, a new  FinanceTransaction will be created with a reference entity type of “Payment”.

#### finance-transaction-payments-to-netsuite
This project will be triggered whenever a new FinanceTransaction record of reference entity type “Payment” is created.  It will then create a corresponding “Customer Payment” in NetSuite based on the Salesforce Billing Payment.

**Note:** The account related to the payment needs to be present in NetSuite for successful payment creation.

### Scenario 3 projects (Post Credits w/ Lines from Salesforce Billing (with taxes):
#### credit-note-to-finance-transaction
This project will be triggered when Credit Notes are “Posted” in Salesforce Billing.  When this happens, a set of new  FinanceTransactions will be created: One for the posted Credit Note (with a reference entity type of “Credit memo”), plus additional FinanceTransactions for each of the Credit Note Lines (with a reference entity type of “Credit memo line”) within the Credit Note.

#### finance-transaction-credit-memo-to-netsuite
This project will be triggered whenever a new FinanceTransaction record of reference entity type “Credit memo” is created.  It will then create a corresponding Credit Memo in NetSuite based on the Salesforce Billing Credit Note along with it’s associated Credit Note Lines based on the products available in the NetSuite product catalog (Inventory Items as they are called in NetSuite), NetSuite accounting period, and tax rate.

**Note:**
The products corresponding to the credit note lines need to be available available in the NetSuite product catalog (Inventory Items as they are called in NetSuite). Otherwise, the Credit Memo creation will fail.
The account related to the Credit Note needs to be present in NetSuite for successful Credit Memo creation.

