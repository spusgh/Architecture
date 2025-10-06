# XYZ Financials UML Diagrams

This repository contains modular PlantUML class diagrams for the XYZ Financials database schema. Each `.puml` file represents a distinct domain, making it easier to visualize relationships and maintain documentation.


![PlantUML diagrams for the XYZ Financials database schema](./XYZFinUML.puml) <br/>


## 📦 Modules

### 1. Customer & Application Domain

- Models customer profiles, addresses, and loan applications
- Shows relationships between customers, applications, and assigned loan officers
- Captures applicant metadata, employment, and credit details

```plantuml 
@startuml Customer_Application
class Customers {
  +CustomerID : int
  FirstName : nvarchar(50)
  LastName : nvarchar(50)
  ...
}

class CustomerAddresses {
  +AddressID : int
  CustomerID : int
  AddressType : nvarchar(20)
  ...
}

class Applications {
  +ApplicationID : int
  CustomerID : int
  ProductID : int
  OfficerID : int
  ...
}

class LoanOfficers {
  +OfficerID : int
  FirstName : nvarchar(50)
  LastName : nvarchar(50)
  ...
}

Customers --> CustomerAddresses : has
Customers --> Applications : submits
Applications --> LoanOfficers : assigned to

@enduml

```

### 2. Loan & Payment Domain
 
- Represents loan lifecycle, payments, term modifications, and servicing rights
- Highlights financial attributes like interest, escrow, and payment schedules
- Links loans to applications and customers

```plantuml

@startuml Loan_Payment
class Loans {
  +LoanID : int
  ApplicationID : int
  CustomerID : int
  ...
}

class Payments {
  +PaymentID : int
  LoanID : int
  PaymentDate : date
  ...
}

class LoanTermModifications {
  +ModificationID : int
  LoanID : int
  ModificationDate : date
  ...
}

class ServicingRights {
  +ServicingID : int
  LoanID : int
  ServicerName : nvarchar(100)
  ...
}

Loans --> Payments : generates
Loans --> LoanTermModifications : modified by
Loans --> ServicingRights : serviced by

@enduml


```


### 3. Property & Escrow Domain
 
- Details property attributes and escrow account management
- Includes escrow transactions and analysis dates
- Connects loans to collateral properties and escrow flows

```plantuml

@startuml Property_Escrow
class PropertyDetails {
  +PropertyID : int
  AddressLine1 : nvarchar(100)
  ...
}

class EscrowAccounts {
  +EscrowID : int
  LoanID : int
  CurrentBalance : decimal
  ...
}

class EscrowTransactions {
  +TransactionID : int
  EscrowID : int
  TransactionDate : date
  ...
}

Loans --> PropertyDetails : secured by
Loans --> EscrowAccounts : has
EscrowAccounts --> EscrowTransactions : records

@enduml


```


### 4. Documents & Audit Domain

- Tracks document registry for applications and audit logs across entities
- Captures approval status, upload metadata, and change history
- Useful for compliance, traceability, and governance

```plantuml

@startuml Documents_Audit
class DocumentsRegistry {
  +DocumentID : int
  ApplicationID : int
  DocumentType : nvarchar(100)
  ...
}

class AuditLog {
  +LogID : int
  EntityType : nvarchar(50)
  EntityID : int
  ...
}

Applications --> DocumentsRegistry : includes
AuditLog --> Applications : logs
AuditLog --> Loans : logs
AuditLog --> Customers : logs

@enduml


```


### 5. Risk & Capital Markets Domain

- Models risk assessments, defaults, foreclosures, and capital market data
- Includes credit scoring, DTI, LTV, and macroeconomic indicators
- Links loan performance to external market rates and risk classifications

```plantuml

@startuml Risk_CapitalMarkets
class RiskAssessments {
  +AssessmentID : int
  CustomerID : int
  ApplicationID : int
  ...
}

class CapitalMarketData {
  +MarketDataID : int
  DataDate : date
  Treasury10Y : decimal
  ...
}

class DefaultsForeclosures {
  +DefaultID : int
  LoanID : int
  DefaultDate : date
  ...
}

Applications --> RiskAssessments : evaluated by
Loans --> DefaultsForeclosures : may default
CapitalMarketData --> Loans : informs pricing

@enduml


```


### 6. Securities & Products Domain

- Represents securities, mortgage products, FINRA data, and product subtypes
- Includes CUSIP, coupon rates, maturity dates, and regulatory flags
- Connects loans to underlying financial instruments and product definitions

```plantuml

@startuml Securities_Products
class Securities {
  +SecurityID : int
  SecurityName : nvarchar(100)
  ...
}

class FINRA_FI {
  +PKID : tinyint
  Symbol : nvarchar(50)
  ...
}

class MortgageProducts {
  +ProductID : int
  ProductName : nvarchar(100)
  ...
}

class ProductSubtype {
  +PTID : int
  ProdType : nchar(50)
  ...
}

class InterestType {
  +ITID : int
  InterestTypeID : nchar(10)
  ...
}

Loans --> Securities : backed by
Applications --> MortgageProducts : requests
MortgageProducts --> ProductSubtype : categorized by
Securities --> FINRA_FI : maps to

@enduml


```


## 📜 License
This documentation is provided for internal architecture visualization and planning. No external redistribution without permission.
