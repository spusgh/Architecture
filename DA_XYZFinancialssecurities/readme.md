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
## 📊 Data Modeling Diagrams

#### 🧭 1. Entity-Relationship Diagram (ERD)
![ERD Diagram](./ERD.png) <br/>
[ERD Mermaid Diagram](./ERD.mermaid)

Purpose: Visualize tables, attributes, and relationships <br/>
Use Cases: Database design, normalization, foreign key mapping <br/>
Tools: Mermaid.io, Lucidchart, DrawSQL

#### 🔄 2. Data Flow Diagram (DFD)
![Data Flow Diagram-Mortgage Lending & Servicing Aystem Architecture](./DataFlowDiagram-Mortgage%20Lending%20%26%20Servicing%20Aystem%20Architecture.png) <br/>
[DFD Level 0 High Level System Diagram](./DFDLevel0HighLevelSystemDiagram.mermaid) <br/>
[DFD Level 1 Detailed System Diagram](./DFDLevel1DetailedSystemDiagram.mermaid)<br/>
[DFD Level 2 Detailed ETL APIs Data Stores Diagram](./DFDLevel2DetailedETLAPIsDataStores.mermaid)

Purpose: Show how data moves between systems, processes, and stores Use Cases: System architecture, ETL design, integration planning Levels:<br/>
Level 0: High-level system overview<br/>
Level 1+: Detailed flows between components (e.g., loan origination → risk assessment → servicing)<br/>

#### 🏗️ 3. Star Schema / Dimensional Model
<a href="StarSchemaDimensionalModel.md" target="_blank">Star Schema Dimensional Model</a> <br/><br/>

[Star Schema Dimensional Model Mermaid Diagram](./StarSchemaDimensionalModel.mermaid)

Purpose: Design for analytics and reporting Use Cases: Data warehouse, BI dashboards Components:<br/>
Fact tables: Loans, Payments, Applications<br/>
Dimension tables: Customers, Products, Properties, Dates<br/>

#### 🧬 4. Data Lineage Diagram
<a href="DataLineageDiagram.md" target="_blank">Data Lineage</a> <br/><br/>

![Data Lineage Diagram](./DataLineageDiagram.png)
[Data Lineage Mermaid Diagram](./DataLineage.mermaid)

Purpose: Trace origin, transformation, and destination of data <br/>
Use Cases: Compliance, debugging, impact analysis <br/>
Example: CustomerID flows from Applications → Loans → Payments

#### 🛡️ 5. Data Governance Diagram
<a href="DataGovernanceDiagram.md" target="_blank">Data Governance</a> <br/><br/>

![Data Governance Diagram](./DataGovernanceDiagram.png) <br/>
[Data Governance Mermaid Diagram](./DataGovernance.mermaid)

Purpose: Map ownership, stewardship, and quality controls <br/>
Use Cases: Regulatory compliance, data quality management Includes:<br/>
- Sensitive fields (e.g., SSN, CreditScore)<br/>
- Steward roles<br/>
- Validation rules<br/>

#### 🧠 6. Conceptual, Logical, and Physical Data Models
<a href="LogicalPhysicalDataModels.md" target="_blank">Logical Physical Data Models</a> <br/><br/>

[Conceptual Data Models Diagram](./ConceptualDataModels.mermaid) <br/>
[Logical Data Models Diagram](./LogicalDataModel.mermaid) <br/>
[Physical Data Model Mermaid Diagram](./PhysicalDataModel.mermaid) <br/>

|Model Type	|Description	|Audience|
| :- |:- | :- |
|Conceptual	| High-level entities and relationships	| Business stakeholders|
|Logical	| Detailed attributes, keys, and relationships	| Data architects|
|Physical	| Actual implementation with data types and indexes	| DBAs, developers|

#### 📊 7. Dashboard Wireframes / BI Schema
<a href="MortgageBIDashboard.md" target="_blank">Mortgage BI Dashboard</a> <br/><br/>

![Loan Performance Over Time](loan_performance.png)
![Risk Classification Heatmap](risk_classification.png)
![Escrow Balance Trends](escrow_balance.png.png)

Purpose: Visualize how data supports KPIs and metrics <br/>
Use Cases: Reporting, executive dashboards Examples:<br/>
- Loan performance dashboard
- Risk classification heatmap
- Escrow balance trends

#### 🔐 8. Security & Access Control Diagram
<a href="SecurityAccessControl.md" target="_blank">Security Access Control</a> <br/><br/>

[Security Access Control Mermaid Diagram](./SecurityAccessControlDiagram.mermaid)

Purpose: Define roles, permissions, and access boundaries <br/>
Use Cases: Role-based access, audit planning Includes:
- Who can view/edit AuditLog, DocumentsRegistry
- Data masking for PII fields

#### 🔧 9. ETL Pipeline Diagram
<a href="ETLPipelineDiagram.md" target="_blank">Data ETL Pipeline</a> <br/><br/>

[ETL Pipeline Mermaid Diagram](./ETLPipelineDiagram.mermaid)

Purpose: Show extraction, transformation, and loading processes <br/>
Use Cases: Data engineering, scheduling, monitoring <br/>
Example: CapitalMarketData → Cleanse → Enrich → Load to DW

#### 🧭 10. Master Data Management (MDM) Architecture
<a href="MDMArchitectureDiagram.md" target="_blank">MDM Architecture</a> <br/><br/>

[MDM Architecture Mermaid Diagram](./MDMArchitectureDiagram.mermaid)

Purpose: Centralize and govern master entities <br/>
Use Cases: Golden record creation, deduplication <br/>
Entities: Customers, Products, Properties, Securities


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

