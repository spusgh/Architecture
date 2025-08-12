# Mortgage BI Dashboards

This project outlines Business Intelligence dashboards and schema design for a mortgage management system. It includes wireframes and schema diagrams for visualizing loan performance, risk classification, and escrow trends.

---

## 📊 Dashboards Overview

### 1. Loan Performance Dashboard
- **Metrics**: Total loan volume, average interest rate, approval rate
- **Visuals**:
  - Line chart: Loan volume over time
  - Bar chart: Interest rate by loan type
  - Pie chart: Loan purpose distribution
  - Map: Geographic distribution of loans
	
### ✅ (2) Python Dashboard Mockup Using Plotly
generated three visualizations:

📈 Loan Performance Over Time (loan_performance.png)

💰 Escrow Balance Trends (escrow_balance.png)

🔥 Risk Classification Distribution (risk_classification.png)

### 📊 Summary Metrics
- Average Loan Performance: ~92.5%
- Total Escrow Balance: ~$1.3 million
- Risk Classification Breakdown:
	- Low: 8
	- Medium: 9
	- High: 7

### 3. Risk Classification Heatmap
- **Metrics**: Default rate, credit score bands, loan-to-value ratio
- **Visuals**:
  - Heatmap: Default rate by credit score and LTV
  - Scatter plot: Credit score vs interest rate
  - Table: Risk tiers and thresholds

### 4. Escrow Balance Trends
- **Metrics**: Escrow balance, disbursement frequency, tax/insurance payments
- **Visuals**:
  - Area chart: Escrow balance over time
  - Stacked bar: Disbursements by category
  - Line chart: Monthly escrow inflow/outflow

---

## 🗂️ BI Schema Design

### Fact Table: `FactMortgage`
- MortgageID
- CustomerID
- PropertyID
- LoanOfficerID
- LoanAmount
- InterestRate
- TermYears
- StartDate
- EscrowBalance
- DefaultFlag

### Dimensions:
- `DimCustomer`: Name, Age, CreditScore, Income, EmploymentStatus
- `DimProperty`: Address, City, State, AppraisedValue
- `DimLoanOfficer`: Name, Branch, Region
- `DimDate`: DateKey, Month, Quarter, Year
- `DimRiskTier`: TierName, MinScore, MaxScore, RiskLevel

---

## 🛠️ Implementation Notes
- Designed for Power BI, Tableau, or Looker
- Daily ETL refresh recommended
- Index foreign keys for performance
- Use calculated columns for risk tier classification

---

## 📌 Use Cases
- Monitor loan growth and approval trends
- Identify high-risk borrower segments
- Track escrow balances for compliance
