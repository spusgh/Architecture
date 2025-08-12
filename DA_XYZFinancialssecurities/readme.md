# 🏦 Mortgage Lending & Servicing Data Schema

This repository contains the full relational database schema for a mortgage lending and servicing platform. It supports customer onboarding, loan origination, servicing, risk assessment, and capital market integration.

---

## 📘 Overview

This schema is designed to support:
- Loan applications and approvals
- Customer and property management
- Loan servicing and escrow tracking
- Risk assessments and compliance
- Integration with capital market data and securities

---

## 🧱 Data Architecture

### 🔹 Core Domains
| Domain               | Key Tables                                                                 |
|----------------------|----------------------------------------------------------------------------|
| Customer Management  | `Customers`, `CustomerAddresses`, `LoanOfficers`                          |
| Loan Lifecycle       | `Applications`, `Loans`, `Payments`, `LoanTermModifications`             |
| Servicing & Escrow   | `EscrowAccounts`, `EscrowTransactions`, `ServicingRights`                |
| Risk & Compliance    | `RiskAssessments`, `AuditLog`, `DocumentsRegistry`, `DefaultsForeclosures` |
| Product Catalog      | `MortgageProducts`, `ProductSubtype`, `InterestType`                     |
| Market Intelligence  | `CapitalMarketData`, `FINRA_FI`, `Securities`                            |
| Property Data        | `PropertyDetails`                                                        |

---

## 🧩 Entity Relationships

Refer to the ERD image for a visual representation of relationships between entities.

### 🔗 Key Relationships
- `Customers` ↔ `Applications` ↔ `Loans`
- `Loans` ↔ `Payments`, `EscrowAccounts`, `ServicingRights`
- `Applications` ↔ `DocumentsRegistry`, `RiskAssessments`
- `Loans` ↔ `PropertyDetails`, `MortgageProducts`, `Securities`
- `LoanOfficers` ↔ `Applications`
- `CapitalMarketData` and `FINRA_FI` provide external reference data

---

## 📂 Table Descriptions

### Customers
Stores personal and financial details of loan applicants.

### Applications
Captures loan application data including requested amount, purpose, and status.

### Loans
Represents approved loans with terms, balances, and payment schedules.

### Payments
Tracks individual loan payments including principal, interest, and escrow.

### EscrowAccounts & EscrowTransactions
Manages escrow balances and transactions for taxes, insurance, and PMI.

### RiskAssessments
Evaluates creditworthiness using credit score, DTI, and LTV metrics.

### MortgageProducts
Defines loan products with constraints like term, interest rate, and LTV limits.

### PropertyDetails
Stores real estate data including valuation, location, and tax information.

### AuditLog
Captures change history for compliance and traceability.

### CapitalMarketData & FINRA_FI
Provides market rates and security-level data for pricing and risk modeling.

---

## ✅ Data Quality & MDM

- **Master Data Domains**: Customer, Product, Property, Officer, Security
- **Quality Dimensions**: Completeness, Accuracy, Consistency, Timeliness, Uniqueness
- **MDM Features**: Golden records, hierarchy management, deduplication

---

## 🚀 Getting Started

1. **Database Setup**: Execute the provided SQL scripts to create tables.
2. **Data Ingestion**: Load external data into `CapitalMarketData`, `FINRA_FI`, etc.
3. **ETL Pipelines**: Build data flows for analytics and reporting.
4. **BI Integration**: Connect to tools like Power BI or Tableau for insights.

---

## 📈 Use Cases

- Loan origination and underwriting
- Customer risk profiling
- Escrow and servicing operations
- Regulatory compliance and audit
- Capital market rate benchmarking

---

