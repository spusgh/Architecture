# ETL Pipeline for Mortgage Lending Schema

This document outlines the ETL (Extract, Transform, Load) pipeline used to populate and maintain the mortgage lending database. The pipeline ensures data integrity, consistency, and readiness for analytics and operations.

---

## 🖼️ Diagram Overview

[ETL Pipeline Mermaid Diagram](./ETLPipelineDiagram.mermaid)

---

## 🔍 Extract

Data is sourced from various systems:

- **CRM System**: Customer profiles and contact details
- **Web Forms**: Loan applications submitted by users
- **Payment Gateway**: Transactional payment data
- **Risk Assessment Engine**: Credit scores and risk metrics

---

## 🔧 Transform

Data undergoes several transformation steps:

1. **Cleansing**: Remove duplicates, fix formatting issues
2. **Normalization**: Standardize formats (e.g., dates, addresses)
3. **Enrichment**: Add derived fields (e.g., loan-to-value ratio)
4. **Validation**: Apply business rules and schema checks

---

## 📦 Load

Transformed data is loaded into the following tables:

| Table             | Description                              |
|------------------|------------------------------------------|
| Customers         | Personal and contact information         |
| Applications      | Loan application details                 |
| Loans             | Approved loan records                    |
| Payments          | Payment history and schedules            |
| RiskAssessments   | Credit and risk evaluation data          |

---

## 🚀 Use Cases

- **Analytics**: Enable dashboards and reporting
- **Operations**: Support loan processing and servicing
- **Compliance**: Maintain audit trails and risk visibility

---

## 🛠️ Maintenance

- Scheduled nightly batch jobs
- Real-time ingestion for payment updates
- Monitoring via ETL dashboard

---

## 📬 Contact

For pipeline issues or enhancements, contact the Data Engineering Team.
