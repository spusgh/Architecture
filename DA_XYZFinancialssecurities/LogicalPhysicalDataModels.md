# Mortgage Data Models

This repository contains three levels of data modeling for a mortgage management system:

## 1. Conceptual Data Model
- High-level overview of entities and their relationships
- Focuses on business concepts without technical details
- Useful for discussions with stakeholders and domain experts

### 🧠 Conceptual Data Model
---

#### 🖼️ Diagram Overview

![Conceptual Data Models Diagram](./ConceptualDataModels.mermaid)

Entities and Relationships:
A Customer can apply for multiple Mortgages<br/>
Each Mortgage is linked to one Property<br/>
A Mortgage has many Payments<br/>
A LoanOfficer manages many Mortgages<br/>

[Customer]───<applies for>───[Mortgage]───<secured by>───[Property]
     │                              │
     └────<managed by>────[LoanOfficer]
                                │
                        └────<has>────[Payment]


## 2. Logical Data Model
- Expands on the conceptual model with attributes, primary keys, and foreign keys
- Normalized structure for efficient data storage
- Platform-independent design

### 📐 Logical Data Model
---

#### 🖼️ Diagram Overview

![Logical Data Models Diagram](./LogicalDataModel.mermaid)

| Entity | Attributes |
| :--- | :--- |
|Customer	| CustomerID (PK), Name, Email, Phone, SSN |
|Mortgage	| MortgageID (PK), CustomerID (FK), PropertyID (FK), LoanOfficerID (FK), Amount, InterestRate, TermYears, StartDate |
|Property	| PropertyID (PK), Address, City, State, ZipCode, AppraisedValue |
|Payment	| PaymentID (PK), MortgageID (FK), DueDate, PaymentDate, AmountPaid |
|LoanOfficer	| LoanOfficerID (PK), Name, Email, Branch |


## 3. Physical Data Model
- SQL DDL scripts for implementing the schema in a relational database
- Includes data types, constraints, indexes, and table definitions
- Tailored for PostgreSQL (can be adapted to other RDBMS)
- Supports data integrity and performance optimization
- Facilitates data migration and ETL processes
- Includes sample data for testing and validation
- Supports data governance and compliance requirements
- Provides a foundation for reporting and analytics
- Ensures scalability and maintainability
- Supports integration with external systems
- Includes documentation for developers and data engineers

### 🏗️ Physical Data Model
---

#### 🖼️ Diagram Overview

![Physical Data Models Diagram](./PhysicalDataModel.mermaid)

```sql
CREATE TABLE Customer (
    CustomerID SERIAL PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100),
    Phone VARCHAR(20),
    SSN VARCHAR(11) UNIQUE
);

CREATE TABLE Property (
    PropertyID SERIAL PRIMARY KEY,
    Address VARCHAR(200),
    City VARCHAR(50),
    State VARCHAR(2),
    ZipCode VARCHAR(10),
    AppraisedValue DECIMAL(12,2)
);

CREATE TABLE LoanOfficer (
    LoanOfficerID SERIAL PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100),
    Branch VARCHAR(100)
);

CREATE TABLE Mortgage (
    MortgageID SERIAL PRIMARY KEY,
    CustomerID INT REFERENCES Customer(CustomerID),
    PropertyID INT REFERENCES Property(PropertyID),
    LoanOfficerID INT REFERENCES LoanOfficer(LoanOfficerID),
    Amount DECIMAL(12,2),
    InterestRate DECIMAL(5,2),
    TermYears INT,
    StartDate DATE
);

CREATE TABLE Payment (
    PaymentID SERIAL PRIMARY KEY,
    MortgageID INT REFERENCES Mortgage(MortgageID),
    DueDate DATE,
    PaymentDate DATE,
    AmountPaid DECIMAL(10,2)
);
```
---

## Entities Overview

- **Customer**: Mortgage applicants and borrowers
- **Mortgage**: Loan details including amount, interest rate, and term
- **Property**: Real estate associated with the mortgage
- **Payment**: Scheduled and actual payments made toward the mortgage
- **LoanOfficer**: Staff responsible for managing customer applications

---

## Usage

- Use the conceptual model for stakeholder alignment
- Use the logical model for database design and validation
- Use the physical model to deploy the schema in your database

