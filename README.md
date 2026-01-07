# End-to-End AML Risk Scoring & Transaction Monitoring System

## Overview
This project implements a **bank-grade, risk-based Anti-Money Laundering (AML) framework** that integrates:

- Customer KYC risk assessment  
- Rule-based transaction monitoring  
- Unsupervised anomaly detection (Isolation Forest)  
- Customer–transaction risk integration  
- Quantile-based alert calibration  

The solution is designed in alignment with:
- **FATF 40 Recommendations**
- **RBI AML / KYC Master Directions**
- Risk-Based Approach (RBA)

All datasets used are **synthetically generated** and contain no real customer information.

---

## Business Problem
Financial institutions face challenges such as:
- Excessive false-positive AML alerts  
- Limited detection of emerging laundering patterns  
- Poor explainability during audits  
- Misalignment between alert volumes and investigation capacity  

This project demonstrates a **layered AML risk engine** that balances:
- Regulatory compliance  
- Risk coverage  
- Operational efficiency  

---

## Solution Architecture

Customer Risk (KYC)  
↓  
Rule-Based Transaction Monitoring  
↓  
Anomaly Detection (Isolation Forest)  
↓  
Transaction Risk Consolidation  
↓  
Customer + Transaction Risk Integration  
↓  
Quantile-Calibrated AML Alerts  

---

## Key Components

### 1. Customer Risk Scoring (KYC Layer)
Risk factors considered:
- FATF / OFAC country risk  
- Sector risk (NGO, import–export, defense, etc.)  
- Politically Exposed Persons (PEPs)  
- Sanctions exposure  
- Ownership opacity  

**Outputs**
- Customer risk score  
- Risk category (Low / Medium / High)  
- Explainable risk drivers  

---

### 2. Rule-Based Transaction Monitoring
Detects known AML typologies:
- Sanctions transactions  
- FATF high-risk jurisdictions  
- Structuring (smurfing)  
- Rapid movement (layering)  
- Trade-based money laundering (TBML)  

**Outputs**
- Transaction risk score  
- Transaction alert flag  

---

### 3. Anomaly Detection
- Uses **Isolation Forest**
- Unsupervised (no labeled fraud data required)
- Detects unknown or emerging suspicious patterns  

**Purpose**
- Complements rule-based monitoring
- Reduces blind spots

---

### 4. Risk Integration
- Customer risk weighted at **60%**
- Transaction risk weighted at **40%**
- Context-aware AML risk scoring  

---

### 5. Alert Calibration
- Alert thresholds set using **risk score quantiles**
- Final alert rate calibrated to **~5%**
- Aligns with real-world AML investigation capacity  

---

## Key Results
- High-risk customers prioritized for EDD  
- Transaction alerts kept operationally manageable  
- Explainable, regulator-ready AML alerts  
- Full audit trail of scoring logic and thresholds  

---

## Regulatory Alignment
- FATF 40 Recommendations  
- RBI AML / KYC Master Directions  
- Risk-Based Approach (RBA)  
- Explainability & auditability by design  

---

## Repository Structure
- `data/` – Synthetic datasets  
- `notebooks/` – Step-by-step AML pipeline  
- `docs/` – BRD, FSD, regulatory mappings, case studies  
- `outputs/` – Scored datasets and alerts  

---

## Disclaimer
This project is for **educational and demonstration purposes only**.  
No real customer or transaction data is used.

---

## Author
**Avijit Saha**  
Banking & Risk Analytics Professional

