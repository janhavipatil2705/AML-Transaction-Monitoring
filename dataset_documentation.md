# Dataset Documentation

## 1. Dataset Overview

* **Dataset name:** IBM Transactions for Anti-Money Laundering (AML) — HI-Small Transactions
* **Source:** [Kaggle — IBM Transactions for Anti-Money Laundering](https://www.kaggle.com/datasets/ealtman2019/ibm-transactions-for-anti-money-laundering-aml)
* **Original source/repository:** [IBM AML-Data on GitHub](https://github.com/IBM/AML-Data)
* **Date downloaded:** 10 October 2026 *(update if you downloaded it on a different date)*
* **Purpose:** Analyse financial transaction patterns, compare transactions labelled as illicit with other transactions, investigate transaction activity over time, and identify patterns that may help prioritise anti-money-laundering investigations.

## 2. Dataset Structure

* **File name:** `HI-Small_Trans.csv`
* **Number of rows:** 5,078,345 transaction records
* **Number of columns:** 11
* **Time period:** September 2022; timestamps range from 1 September to 18 September 2022 in the published dataset.
* **Unit of observation:** One financial transaction per row.
* **Key fields:** Timestamp, From Bank, Account, To Bank, Account, Amount Received, Receiving Currency, Amount Paid, Payment Currency, Payment Format, Is Laundering.
* **Target/label column:** `Is Laundering` — indicates whether a transaction is labelled as laundering in the synthetic dataset.

## 3. Limitations

* The dataset is **fully synthetic**, generated using a simulated financial world. It is not real customer data and was not created by anonymising actual customer records.
* The data represents simulated financial transactions and may not capture the full complexity of real-world banking activity or money-laundering investigations.
* Transactions labelled as laundering should not be treated as proof of actual criminal activity.
* The `Is Laundering` class is highly imbalanced, with only a small proportion of transactions carrying the laundering label.
* The dataset covers a limited period, so findings cannot establish long-term trends or seasonality.
* Bank and account identifiers are simulated identifiers and should not be interpreted as real financial institutions or customers.
* Findings may depend on the assumptions used to generate the synthetic data; results should not automatically be generalised to real banks.
* The dataset is distributed under the Community Data License Agreement — Sharing, Version 1.0 (CDLA-Sharing-1.0), according to IBM's repository. Check the terms that apply to your downloaded copy before redistributing data.

## 4. Data dictionary
| Column Name | Meaning | Data Type |
|:---|:---|:---|
| Timestamp | Date and time when the transaction occurred. | Datetime |
| From Bank | Identifier of the bank sending the money. | Numeric |
| Account | Unique identifier of the account involved in the transaction. | Alphanumeric |
| To Bank | Identifier of the bank receiving the money. | Numeric |
| Account | Unique identifier of the receiving account. | Alphanumeric |
| Amount Received | Amount of money received by the destination account. | Float |
| Receiving Currency | Currency in which the money was received. | Text |
| Amount Paid | Amount of money paid by the sending account. | Float |
| Payment Currency | Currency in which the payment was made. | Text |
| Payment Format | Method or format used to make the payment, such as cheque or reinvestment. | Text |
| Is Laundering | Indicates whether the transaction was labelled as money laundering (1 = Yes, 0 = No). | Boolean / Binary |

## 5. Initial data-quality report
* Total records/rows: 1048575
* Total columns: 11
* Null values: 0
* Duplicate values: 2

## Dataset Size and Scope

* **Original dataset size:** 5,078,345 transactions, as reported on the Kaggle dataset page.
* **Rows in the local dataset:** 1,048,575, as verified using Python and Microsoft Excel.
* **Note:** The row count of the local file differs from the total reported on Kaggle. The reason for this discrepancy has not yet been verified.

All data-quality checks and analyses in this project are based on the local dataset unless otherwise stated.

