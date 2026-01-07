# Business Requirement Document (BRD)
## AML Risk Scoring & Transaction Monitoring System

---

## 1. Background

Financial institutions are required to comply with Anti-Money Laundering (AML) and Counter Financing of Terrorism (CFT) regulations issued by regulators such as FATF, RBI, and OFAC. Increasing regulatory scrutiny and evolving financial crime typologies require banks to adopt a robust, risk-based AML monitoring framework.

---

## 2. Business Problem

The current AML monitoring approach faces the following challenges:

- Excessive false-positive alerts
- Limited detection of emerging money laundering patterns
- Poor explainability of alerts during audits
- Misalignment between alert volumes and investigation capacity

These challenges increase regulatory risk, operational cost, and investigator fatigue.

---

## 3. Business Objectives

| Objective ID | Objective |
|-------------|----------|
| BO-01 | Implement a risk-based AML monitoring framework |
| BO-02 | Improve detection of high-risk customers and transactions |
| BO-03 | Reduce false positives |
| BO-04 | Ensure explainability and auditability |
| BO-05 | Align alert volumes with investigation capacity |

---

## 4. Scope

### In Scope
- Customer AML risk assessment (KYC)
- Transaction monitoring (rule-based)
- Anomaly detection
- Risk integration
- Alert calibration and governance

### Out of Scope
- Case management workflows
- STR/SAR filing automation
- Real-time transaction streaming
- Investigator UI

---

## 5. Stakeholders

| Stakeholder | Responsibility |
|------------|---------------|
| Compliance Team | AML policy and thresholds |
| AML Investigators | Alert investigation |
| Risk Management | Model validation |
| Business Analysts | Requirements and logic |
| Technology Team | System implementation |
| Internal Audit | Control review |

---

## 6. Business Requirements

### BR-01: Customer Risk Assessment
The system shall assess inherent AML risk for customers based on:
- Country risk (FATF / OFAC)
- Sector risk
- PEP status
- Sanctions exposure
- Ownership opacity

---

### BR-02: Risk Categorization
The system shall assign each customer a risk category:
- Low
- Medium
- High

---

### BR-03: Explainability
The system shall store risk drivers explaining why a customer or transaction is classified as high risk.

---

### BR-04: Rule-Based Transaction Monitoring
The system shall monitor transactions for known AML typologies including:
- Structuring
- Rapid movement of funds
- Sanctions exposure
- Trade-based money laundering

---

### BR-05: Anomaly Detection
The system shall identify anomalous transaction behavior without relying on labeled fraud data.

---

### BR-06: Risk Integration
The system shall combine customer risk and transaction risk into a unified AML risk score.

---

### BR-07: Alert Generation
The system shall generate AML alerts based on configurable thresholds.

---

### BR-08: Alert Calibration
Alert thresholds shall be calibrated using risk score distributions to align with investigation capacity.

---

## 7. Non-Functional Requirements

| Category | Requirement |
|--------|------------|
| Scalability | Handle large transaction volumes |
| Performance | Near real-time processing |
| Explainability | Mandatory |
| Auditability | Full traceability |
| Configurability | Adjustable thresholds |

---

## 8. Success Metrics

| Metric | Target |
|------|-------|
| Alert Rate | ~5% |
| False Positives | Reduced |
| Audit Observations | Minimal |
| Investigator Efficiency | Improved |

---

## 9. Assumptions & Risks

### Assumptions
- Reliable customer and transaction data
- Defined AML investigation capacity

### Risks
- Poor data quality may impact accuracy
- Over-calibration may increase alerts
- Under-calibration may create regulatory gaps

---

## 10. Approval

This document is subject to approval by Compliance, Risk, and Senior Management.

