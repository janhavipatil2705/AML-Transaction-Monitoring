# AML Transaction Monitoring & Analysis

An exploratory data analysis project focused on understanding financial transaction patterns and investigating laundering-labelled transactions using the IBM Transactions for Anti-Money Laundering (AML) dataset.

**Project Domain:** Banking, Financial Services & FinTech (BFSI)  
**Project Type:** Data Analysis | Exploratory Data Analysis | Transaction Monitoring  
**Status:** In Progress

---

## 1. Project Overview

Money laundering involves moving illegally obtained funds through financial systems to make them appear legitimate. Financial institutions rely on transaction monitoring to identify unusual patterns and determine which transactions may require further investigation.

This project explores simulated financial transaction data to understand transaction behaviour, compare laundering-labelled and non-laundering transactions, and identify patterns that could be useful for further investigation.

The analysis begins with data understanding and exploratory data analysis using Python, followed by deeper investigation using SQL.

The objective is not to classify transactions as criminal activity based on individual attributes, but to explore the data, identify meaningful patterns, and understand where further investigation may be useful.

## 2. Business Problem

Financial institutions process large volumes of transactions, making it difficult to manually examine every transaction. Identifying unusual activity and prioritising transactions for further review is an important part of anti-money-laundering operations.

This project investigates the following questions:

- How frequently do laundering-labelled transactions occur?
- How do transaction amounts differ between laundering-labelled and non-laundering transactions?
- Are certain payment formats or currencies more frequently associated with laundering-labelled transactions?
- Do particular sending or receiving banks show higher laundering-labelled transaction activity?
- Are there repeated account-level transaction patterns?
- What additional insights can be uncovered through SQL-based analysis?

## 3. Dataset Information

**Dataset:** IBM Transactions for Anti-Money Laundering (AML) — HI-Small Transactions

**Source:** [Kaggle – IBM Transactions for Anti-Money Laundering](https://www.kaggle.com/datasets/ealtman2019/ibm-transactions-for-anti-money-laundering-aml)

**Original Repository:** [IBM AML-Data on GitHub](https://github.com/IBM/AML-Data)

The dataset contains simulated financial transactions generated using a synthetic financial world. It is designed to support research and analysis related to anti-money laundering.

### Dataset Details

| Attribute | Details |
|---|---|
| Dataset file | `HI-Small_Trans.csv` |
| Original dataset size | 5,078,345 transactions |
| Local working dataset | 1,048,575 transactions |
| Number of columns | 11 |
| Time period | 1 September – 18 September 2022 |
| Unit of observation | One financial transaction per row |
| Target column | `Is Laundering` |

**Dataset scope:** The original dataset documentation reports 5,078,345 transactions. However, the local dataset currently used for this project contains 1,048,575 rows, verified using both Python and Microsoft Excel. The reason for this difference has not yet been established. All current analysis is based on the local working dataset unless otherwise specified.

For detailed source information, column descriptions, and dataset limitations, refer to [`dataset_documentation.md`](dataset_documentation.md).

## 4. Tools & Technologies

| Tool / Technology | Purpose |
|---|---|
| Python | Data analysis and exploration |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Jupyter Notebook | Interactive analysis |
| SQL | Planned transaction-level investigation |
| GitHub | Project documentation and version control |

## 5. Project Workflow

### Phase 1 – Dataset Understanding & Documentation
- Identified the dataset source and original repository.
- Examined the dataset structure and available variables.
- Documented the data dictionary and column descriptions.
- Recorded dataset limitations and scope.
- Inspected the local working dataset.

### Phase 2 – Data Quality Assessment
- Checked dataset dimensions and data types.
- Examined missing values.
- Checked for duplicate records.
- Analysed the distribution of the target variable.
- Documented the initial data-quality findings.

### Phase 3 – Exploratory Data Analysis (Python)
- Analysed laundering-labelled and non-laundering transaction distributions.
- Explored transaction amount distributions.
- Identified potential outliers using the Interquartile Range (IQR) method.
- Compared transaction amounts across the two target classes.
- Examined payment formats and currency distributions.
- Investigated bank-wise and account-level activity.
- Used visualizations to understand transaction patterns.

### Phase 4 – SQL Analysis (Planned)
The next stage will focus on deeper investigation using SQL.

Planned areas include:
- Laundering-label distribution across payment formats and currencies.
- Bank-wise transaction activity and laundering-label counts.
- Account-level transaction frequency and repeated activity.
- Transaction amount comparisons.
- Time-based transaction trends.
- Identification of patterns that may deserve further investigation.

## 6. Initial Data Quality Findings

The following results were obtained from the local working dataset.

| Metric | Result |
|---|---:|
| Total records | 1,048,575 |
| Total columns | 11 |
| Missing values | 0 |
| Duplicate records | 2 |
| Laundering-labelled transactions | 615 |
| Non-laundering transactions | 1,047,960 |
| Laundering-label share | 0.0586% |

The dataset is highly imbalanced, with approximately **1 in every 1,705 transactions** carrying the laundering label.

This imbalance is important when interpreting the analysis. For example, overall accuracy alone would not be sufficient for evaluating a potential classification model because a model could achieve high accuracy simply by predicting the majority class.

## 7. Key Findings from Exploratory Data Analysis

The initial EDA revealed several patterns worth investigating further.

### 1. Significant Class Imbalance

Only approximately **0.0586%** of the analysed transactions are labelled as laundering, while the remaining transactions are labelled as non-laundering.

This highlights the highly imbalanced nature of the dataset and the importance of examining the minority class carefully.

### 2. Transaction Amount Outliers

The IQR method identified a considerable number of observations above the upper outlier boundaries for both Amount Received and Amount Paid.

Approximately 18.82% of Amount Received observations and 18.80% of Amount Paid observations were identified as upper-end outliers.

These values require further investigation. A high transaction amount alone does not establish suspicious activity.

### 3. Differences in Transaction Amounts

The boxplot analysis showed higher median transaction amounts for laundering-labelled transactions compared with non-laundering transactions.

This suggests that transaction value may be worth investigating further alongside other transaction characteristics.

### 4. Payment Format and Currency Distribution

Reinvestment and Cheque were among the most frequently observed payment formats in the analysed data.

USD and Euro were also among the most frequently observed receiving currencies.

Further investigation is needed to understand whether particular payment formats or currencies have a higher proportion of laundering-labelled transactions, rather than simply having higher overall transaction counts.

### 5. Bank and Account-Level Activity

The initial analysis showed differences in laundering-labelled transaction counts across banks.

Bank 70 had the highest observed count on the sending side, while Bank 12 had the highest observed count on the receiving side.

Some sender accounts also appeared repeatedly in the transaction records. These observations provide a starting point for more detailed account-level and bank-level investigation.

### Overall Observation

The initial analysis highlights significant class imbalance, differences in transaction amounts, and variations in payment, currency and bank activity.

These findings help identify areas for further investigation, but they should not be interpreted as proof of money laundering.

## 8. Repository Structure

```text
AML-Transaction-Monitoring/
│
├── AML EDA.ipynb
│   └── Python-based exploratory data analysis
│
├── dataset_documentation.md
│   └── Dataset overview, data dictionary and limitations
│
├── README.md
│   └── Project overview and documentation
│
└── sql_analysis.sql
    └── SQL-based transaction investigation (planned)
```

*The repository structure will be updated as additional analysis files are added.*

## 9. Limitations

- The dataset is fully synthetic and does not contain actual customer transaction records.
- The local working dataset contains 1,048,575 records, whereas the original dataset documentation reports 5,078,345 records.
- The reason for the difference in dataset size has not yet been verified.
- The dataset covers a limited period from September 2022 and cannot establish long-term trends or seasonality.
- Bank and account identifiers represent simulated entities, not actual financial institutions or customers.
- Laundering labels represent the dataset's simulated classifications and are not proof of real-world criminal activity.
- Statistical outliers should not automatically be considered suspicious transactions.
- Findings from synthetic data should not be directly generalised to real-world banking systems.

## 10. Future Scope

The project can be extended through the following activities:

- Conduct deeper transaction-level analysis using SQL.
- Investigate repeated account activity and transaction flows.
- Examine bank-wise and account-wise laundering-label distributions.
- Analyse transaction patterns across payment formats and currencies.
- Explore transaction activity over time.
- Build an interactive Power BI dashboard for transaction monitoring.
- Explore rule-based anomaly detection and potential risk indicators.

## 11. Conclusion

This project explores how data analytics can be used to understand financial transaction behaviour and support anti-money-laundering investigations.

Through dataset documentation, data-quality assessment and exploratory analysis in Python, the initial stage focuses on understanding the structure of the data and identifying patterns that deserve closer attention.

The next stage will use SQL to investigate these patterns in greater detail and develop a more comprehensive view of transaction activity.

---

**Author:** Janhavi Patil  
**Domain:** Data Analytics | BFSI | Anti-Money Laundering

[View GitHub Repository](https://github.com/janhavipatil2705/AML-Transaction-Monitoring)
