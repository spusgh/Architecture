# Security & Access Control Diagram

This document outlines the access control model for the mortgage lending schema. It defines user roles, their permissions, and boundaries across key data entities.

---

## 🧑‍💼 Roles & Responsibilities

| Role             | Description                                      |
|------------------|--------------------------------------------------|
| Admin            | Full access to all tables and audit logs         |
| Compliance Officer | Read-only access to audit and risk data        |
| Loan Officer     | Access to customer, application, and loan data   |
| Risk Analyst     | Access to risk assessments and scoring models    |
| Servicing Team   | Access to loan servicing and payment data        |
| Customer Portal  | Limited access for customers to view applications and payments |

---

## 🔐 Access Matrix

| Table             | Admin | Compliance | Loan Officer | Risk Analyst | Servicing | Customer |
|-------------------|-------|------------|--------------|--------------|-----------|----------|
| Customers         | RW    | R          | RW           | R            | R         | R        |
| Applications      | RW    | R          | RW           | R            | R         | R        |
| Loans             | RW    | R          | RW           | R            | RW        | R        |
| Payments          | RW    | R          | R            | R            | RW        | R        |
| RiskAssessments   | RW    | R          | R            | RW           | R         |          |
| AuditLog          | RW    | R          |              |              |           |          |

---

## 🛡️ Implementation Tips

- Use role-based access control (RBAC)
- Mask sensitive fields (e.g., SSN, CreditScore) for non-admin roles
- Log all access to `AuditLog`
- Apply row-level security for customer portal access

---

## 📬 Contact

