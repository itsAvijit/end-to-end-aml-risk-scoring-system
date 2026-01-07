# Functional Specification Document (FSD)
## AML Risk Scoring & Transaction Monitoring System

---

## 1. Purpose

This document defines the **functional design, business logic, and processing rules** for the AML Risk Scoring and Transaction Monitoring System.  
The solution is designed to support a **risk-based AML framework** aligned with FATF 40 Recommendations and RBI AML/KYC Master Directions.

---

## 2. Scope

### In Scope
- Customer AML risk scoring (KYC layer)
- Rule-based transaction monitoring
- Anomaly detection using unsupervised analytics
- Risk integration and alert generation
- Alert calibration and governance

### Out of Scope
- Case management workflows
- STR/SAR filing automation
- Real-time transaction processing
- Investigator user interface

---

## 3. Functional Overview

The system applies a **layered AML control framework**:



Customer Risk Scoring (KYC)
↓
Rule-Based Transaction Monitoring
↓
Anomaly Detection
↓
Transaction Risk Consolidation
↓
Customer + Transaction Risk Integration
↓
Calibrated AML Alerts



---

## 4. Customer Risk Scoring (KYC Layer)

### 4.1 Objective
To assess the **inherent AML risk** of customers prior to transaction behavior.

---

### 4.2 Inputs

| Attribute | Description |
|--------|-------------|
| Country | Customer country of operation |
| FATF Flag | FATF high-risk jurisdiction indicator |
| OFAC Flag | Sanctions country indicator |
| Sanctions Flag | Customer sanctions exposure |
| Sector | Industry classification |
| Sector Risk | Low / Medium / High |
| PEP Flag | Politically Exposed Person |
| Ownership Opacity | Beneficial ownership transparency |

---

### 4.3 Functional Logic
- Each risk attribute contributes to a weighted customer risk score
- Severe risks (sanctions, OFAC, PEP) carry higher weights
- Risk drivers are captured for explainability

---

### 4.4 Outputs
- `customer_risk_score`
- `customer_risk_category` (Low / Medium / High)
- `risk_drivers`

---

## 5. Rule-Based Transaction Monitoring

### 5.1 Objective
To detect **known AML typologies** using transparent, regulator-approved rules.

---

### 5.2 Inputs

| Attribute | Description |
|--------|-------------|
| Amount | Transaction value |
| Transaction Type | Payment / Transfer / Trade |
| Client Country | Origin country |
| Counterparty Country | Destination country |
| FATF Flag | High-risk geography |
| OFAC Match Flag | Sanctions exposure |
| Structuring Flag | Smurfing indicator |
| Rapid Movement Flag | Layering indicator |
| Trade Mispricing Flag | TBML indicator |

---

### 5.3 Functional Logic
- Each triggered typology contributes to a transaction risk score
- Sanctions exposure triggers maximum risk
- Multiple flags compound risk

---

### 5.4 Outputs
- `transaction_risk_score`
- `transaction_alert_flag`

---

## 6. Anomaly Detection

### 6.1 Objective
To identify **unknown or emerging suspicious patterns** not covered by predefined rules.

---

### 6.2 Functional Approach
- Unsupervised anomaly detection
- Learns normal transaction behavior
- Flags statistically rare or unusual activity

---

### 6.3 Business Rules
- Anomaly detection supplements rule-based monitoring
- Anomaly risk is weighted lower than confirmed AML typologies

---

### 6.4 Outputs
- `anomaly_flag`
- Anomaly-based risk uplift

---

## 7. Transaction Risk Consolidation

### 7.1 Objective
To combine known and unknown risk signals.

---

### 7.2 Functional Logic
- Rule-based risk reflects confirmed typologies
- Anomaly risk reflects suspicious deviations
- Combined into `final_transaction_risk_score`

---

### 7.3 Outputs
- `final_transaction_risk_score`
- `final_transaction_alert`

---

## 8. Customer & Transaction Risk Integration

### 8.1 Objective
To evaluate transaction behavior **in customer context**.

---

### 8.2 Functional Logic
- Customer risk weighted at 60%
- Transaction risk weighted at 40%
- High-risk customers receive enhanced monitoring

---

### 8.3 Outputs
- `final_aml_risk_score`
- `final_aml_alert`

---

## 9. Alert Calibration & Governance

### 9.1 Objective
To balance:
- Risk coverage
- Operational investigation capacity
- Regulatory expectations

---

### 9.2 Functional Logic
- Risk score distribution analyzed
- Alert threshold set at ~95th percentile
- Target alert rate ~5%

---

### 9.3 Outputs
- Calibrated AML alerts
- Documented threshold rationale

---

## 10. Explainability & Audit Controls

| Control | Description |
|------|-------------|
| Risk Drivers | Stored for all alerts |
| Rule Traceability | Flag-level explanations |
| Threshold Documentation | Quantile-based |
| Reproducibility | Deterministic scoring logic |

---

## 11. Non-Functional Requirements

| Category | Requirement |
|-------|-------------|
| Scalability | Large transaction volumes |
| Performance | Near real-time scoring |
| Explainability | Mandatory |
| Auditability | Full traceability |
| Configurability | Adjustable weights and thresholds |

---

## 12. Assumptions & Dependencies

### Assumptions
- Customer and transaction data are available
- AML policies are approved by Compliance

### Dependencies
- Regulatory inputs
- Investigation capacity definition
- Periodic model review

---

## 13. Acceptance Criteria

- Explainable AML alerts generated
- Alert volumes within approved range
- Compliance and Risk sign-off obtained
- Audit review passed without major findings

---

## 14. Version Control

| Version | Description |
|-------|-------------|
| 1.0 | Initial functional specification |

