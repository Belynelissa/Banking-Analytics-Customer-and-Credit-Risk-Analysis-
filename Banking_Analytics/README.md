# Banking Analytics | Customer Value, Transaction Behaviour & Credit Risk

## Engagement context

This banking analytics work was presented to paying clients to demonstrate how customer, account, transaction and lending data can be brought together to support better commercial and risk decisions.

The public version uses simulated data. Client data and identifying information are not published; the sample dataset allows the analytical approach and SQL workflows to be reviewed without exposing confidential records.

## The business challenge

Banks and financial service providers hold information across customer profiles, accounts, transactions and loan portfolios. When these datasets are considered separately, it can be difficult for decision-makers to see how customer value, product usage and credit exposure relate.

This analysis brings those perspectives together to help answer practical questions:

- Which customer groups hold the largest account balances?
- Where are customers concentrated geographically and by income segment?
- Which transaction channels are most frequently used, and which handle higher average transaction values?
- How is the loan book distributed across repayment statuses?
- Where is defaulted loan exposure concentrated?
- How do loan size and customer income segments relate to observed default patterns?
- Which customers may warrant closer review based on the available indicators?

## What the analysis covers

### 1. Customer value and segmentation
- Customer distribution by region and income band.
- Account balances aggregated at customer level.
- Balance-based customer deciles to identify the highest-balance segment.
- Comparison of average account balances across income groups.

**Decision support:** inform customer relationship prioritisation, segment-level engagement and further investigation of customer value.

### 2. Transaction behaviour and channel usage
- Transaction volumes by channel.
- Average transaction amount by channel.
- Distinct customer reach across channels.
- Transaction activity compared across income segments.

**Decision support:** support channel performance reviews and help identify where customer usage patterns may justify service or engagement improvements.

### 3. Loan portfolio and credit risk
- Loan counts and amounts by status.
- Historical default share within the sample.
- Default rates by customer income segment and loan-size band.
- Defaulted loan amounts and exposure shares by income segment.
- Customer-level summaries combining loan exposure and observed transaction activity.

**Decision support:** help management examine portfolio composition, identify concentrations for further review and focus credit-risk investigations.

## Analytical approach

The work uses a relational MySQL database with four core entities:

| Table | Business information |
|---|---|
| `customers` | Customer profile, region and annual income |
| `accounts` | Account type and recorded balance |
| `transactions` | Transaction amount, date and channel |
| `loans` | Loan amount, interest rate, dates and status |

The SQL workflow includes:
- Database and relational table creation with primary and foreign keys.
- CSV data loading and staging.
- Multi-table joins and aggregations.
- Common Table Expressions (CTEs).
- Window functions, including `NTILE()`, for customer deciles.
- Conditional segmentation using `CASE`.
- Portfolio, channel and customer-level analysis.

## Business value

The analysis demonstrates a practical way to turn disconnected banking records into a more connected view of customer value, channel activity and lending exposure. It can help decision-makers:

- Direct attention towards valuable customer segments.
- Review channel usage and customer engagement patterns.
- Identify concentrations in loan exposure and observed defaults.
- Prioritise questions for deeper credit and portfolio investigation.
- Establish a repeatable SQL foundation for management reporting.

These are decision-support applications, not claims of measured cost savings, increased revenue or reduced defaults. Realised outcomes would depend on the institution's data, policies and actions taken after the analysis.

## Data, interpretation and limitations

- All data in this public repository is simulated and is not a representation of any client's actual records or performance.
- The analysis is based on the fields and sample records supplied in this repository; results should not be treated as representative of a real bank or lending portfolio.
- A recorded default status is a historical status in the sample, not a predictive credit-risk model.
- Transaction activity is not the same as verified loan repayment or disposable cash flow. Transaction-to-loan comparisons should be treated as exploratory indicators, not proof of repayment capacity.
- Account balances are not equivalent to customer profitability or bank revenue. Profitability analysis would require additional information such as fees, funding costs, operating costs and product margins.
- Any operational or credit decision should be validated against the institution's definitions, source systems and governance requirements.

## Tools

- MySQL 8.0
- SQL
- Visual Studio Code
- Git and GitHub

## Repository contents

- `Setup.sql` — creates the database and relational tables.
- `staging_load.sql` — loads the sample CSV files and updates the customer income field.
- `analysis_querries.sql` — contains the customer, transaction and credit-risk analysis queries.
- `customers_1000.csv`, `accounts_1000.csv`, `transactions_10000.csv`, `loans_1000.csv` — simulated sample data.
- `customers_annual_income.csv` — simulated customer income data.
- `SQL.pptx` — supporting presentation material.

---

**The focus is not simply writing SQL queries. It is connecting customer, transaction and lending information to the business questions that matter to management.**
