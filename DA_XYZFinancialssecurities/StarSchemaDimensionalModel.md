# 🌟 Star Schema / Dimensional Model for Mortgage Lending Analytics

This document outlines the dimensional model designed to support business intelligence and reporting for a mortgage lending and servicing platform. The schema is structured as a star schema, with centralized fact tables surrounded by descriptive dimension tables.

---

## 📘 Overview

The star schema enables efficient querying and aggregation of key metrics across loan origination, payments, applications, and customer profiles. It supports dashboards, KPIs, and ad hoc analysis for finance, risk, and operations teams.

---

## 🖼️ Diagram Overview

[Star Schema Dimensional Model Mermaid Diagram](./StarSchemaDimensionalModel.mermaid)

---

## 🧮 Fact Tables

### `FactLoans`
Captures loan-level metrics.

| Column            | Description                          |
|-------------------|--------------------------------------|
| LoanID            | Unique loan identifier               |
| CustomerID        | Foreign key to `DimCustomer`         |
| ProductID         | Foreign key to `DimProduct`          |
| PropertyID        | Foreign key to `DimProperty`         |
| SecurityID        | Foreign key to `DimSecurity`         |
| OriginationDateID | Foreign key to `DimDate`             |
| LoanAmount        | Approved loan amount                 |
| InterestRate      | Final interest rate offered          |
| MonthlyPayment    | Scheduled monthly payment            |
| RemainingBalance  | Current outstanding balance          |

---

### `FactPayments`
Captures individual loan payments.

| Column            | Description                          |
|-------------------|--------------------------------------|
| PaymentID         | Unique payment identifier            |
| LoanID            | Foreign key to `FactLoans`           |
| CustomerID        | Foreign key to `DimCustomer`         |
| PaymentDateID     | Foreign key to `DimDate`             |
| PaymentAmount     | Total payment made                   |
| PrincipalAmount   | Principal portion of payment         |
| InterestAmount    | Interest portion of payment          |
| EscrowAmount      | Escrow portion of payment            |

---

### `FactApplications`
Captures loan application data.

| Column            | Description                          |
|-------------------|--------------------------------------|
| ApplicationID     | Unique application identifier        |
| CustomerID        | Foreign key to `DimCustomer`         |
| ProductID         | Foreign key to `DimProduct`          |
| OfficerID         | Foreign key to `DimLoanOfficer`      |
| ApplicationDateID | Foreign key to `DimDate`             |
| LoanAmount        | Requested loan amount                |
| ApplicationFee    | Fee charged for application          |
| DTI               | Debt-to-income ratio                 |
| LTV               | Loan-to-value ratio                  |

---

## 🧭 Dimension Tables

### `DimCustomer`
Provides customer demographics and financial profile.

| Column         | Description             |
|----------------|-------------------------|
| CustomerID     | Unique customer ID      |
| FirstName      | First name              |
| LastName       | Last name               |
| SSN            | Social Security Number  |
| DateOfBirth    | Date of birth           |
| CreditScore    | Credit score            |
| AnnualIncome   | Annual income           |
| EmploymentStatus | Employment status     |

---

### `DimProduct`
Describes mortgage products.

| Column         | Description             |
|----------------|-------------------------|
| ProductID      | Unique product ID       |
| ProductName    | Name of the product     |
| ProductType    | Type (e.g., Fixed, ARM) |
| Term           | Loan term in months     |
| BaseInterestRate | Base rate offered     |
| MinCreditScore | Minimum credit score    |
| MaxLTV         | Maximum loan-to-value   |

---

### `DimProperty`
Provides property details.

| Column         | Description             |
|----------------|-------------------------|
| PropertyID     | Unique property ID      |
| AddressLine1   | Street address          |
| City           | City                    |
| State          | State                   |
| ZipCode        | ZIP code                |
| PropertyType   | Type (e.g., Condo, SFH) |
| YearBuilt      | Year built              |
| CurrentValue   | Latest appraised value  |

---

### `DimLoanOfficer`
Describes loan officers.

| Column         | Description             |
|----------------|-------------------------|
| OfficerID      | Unique officer ID       |
| FirstName      | First name              |
| LastName       | Last name               |
| BranchID       | Branch assignment       |
| HireDate       | Date hired              |
| CommissionRate | Commission percentage   |

---

### `DimDate`
Standard date dimension for time-based analysis.

| Column         | Description             |
|----------------|-------------------------|
| DateID         | Surrogate key           |
| FullDate       | Actual date             |
| Month          | Month name              |
| Quarter        | Quarter of year         |
| Year           | Year                    |

---

### `DimSecurity`
Provides details on financial securities.

| Column         | Description             |
|----------------|-------------------------|
| SecurityID     | Unique security ID      |
| SecurityName   | Name of the security    |
| CUSIP          | Unique identifier       |
| Issuer         | Issuing agency          |
| CouponRate     | Interest rate           |
| MaturityDate   | Date of maturity        |

---

## 🔗 Relationships

```text
FactLoans        → DimCustomer, DimProduct, DimProperty, DimDate, DimSecurity
FactPayments     → DimCustomer, DimDate, FactLoans
FactApplications → DimCustomer, DimProduct, DimLoanOfficer, DimDate

```


### 📈 Use Cases
Loan performance dashboards
Customer segmentation and risk scoring
Product profitability analysis
Payment delinquency tracking
Officer productivity and commission reporting