# Falken Holdings — Company Profile
## WOPR Context File v1.0 | Last Updated: Q1 2026
## Classification: CONFIDENTIAL — WOPR USE ONLY

---

### Organization Overview

| Field | Detail |
|---|---|
| **Company Name** | Falken Holdings, LLC |
| **Type** | Mid-market financial holding company |
| **Headquarters** | Milwaukee, Wisconsin |
| **Secondary Offices** | Chicago, IL; Indianapolis, IN |
| **Employee Count** | ~520 across all entities |
| **Annual Revenue** | $85M–$120M (consolidated) |
| **Fiscal Year End** | December 31 |
| **Website** | falkenholdingsllc.com (internal only) |
| **Years in Operation** | 18 years |
| **Ownership Structure** | Privately held — 3 managing partners |

---

### Portfolio Companies

| Entity | Industry | Employees | Location | IT Integration |
|---|---|---|---|---|
| Falken Property Group (FPG) | Commercial property development | 85 | Milwaukee, WI | Partial — shared email only |
| Ridgeline Manufacturing, Inc. (RMI) | Precision metal parts manufacturing | 280 | Indianapolis, IN | Standalone — legacy systems |
| Summit Professional Services (SPS) | HR consulting and staffing | 155 | Chicago, IL | Full — integrated with FH |

---

### Technology Environment

| Component | Detail |
|---|---|
| **Infrastructure Model** | Hybrid — Azure cloud + on-premises servers |
| **Cloud Platform** | Microsoft Azure (FH and SPS) |
| **On-Premises** | RMI — Windows Server 2016/2019, aging hardware |
| **Identity Provider** | Entra ID (FH and SPS) — local AD (RMI and FPG) |
| **Email Platform** | Microsoft 365 (all entities) |
| **Endpoint OS** | Windows 10/11 (FH, SPS, FPG) — Windows 7/10 mixed (RMI) |
| **Endpoint Count** | ~430 managed endpoints + ~60 unmanaged RMI floor devices |
| **OT/IoT Present** | YES — RMI has PLCs and SCADA-adjacent manufacturing systems |
| **Remote Workforce** | ~35% remote or hybrid (primarily FH and SPS) |
| **Key SaaS Applications** | Microsoft 365, Salesforce (SPS), Procore (FPG), QuickBooks Enterprise (RMI) |
| **Network Connectivity** | MPLS between FH and SPS — RMI connected via site-to-site VPN |

---

### Regulatory & Compliance Obligations

| Obligation | Scope | Status | Notes |
|---|---|---|---|
| State Privacy Laws (IL, WI, IN) | All entities | Active | SPS holds significant PII for staffing clients |
| SOC 2 Type I (in progress) | SPS only | In progress | Client contractual requirement — target Q3 2026 |
| PCI DSS 4.0 | FH (limited) | Active | Credit card processing for property deposits |
| OSHA / EHS Regulations | RMI | Active | Manufacturing safety recordkeeping |
| Cyber Insurance Requirements | All entities | Active | Coalition Insurance — MFA and backup required |
| CMMC Level 1 (potential) | RMI | Evaluating | One DOD subcontractor client relationship |

---

### Security Program Maturity

| Domain | Maturity Level | Notes |
|---|---|---|
| Asset Management | 2 | Manual spreadsheet — estimated 60% accurate |
| Identity & Access Management | 2 | MFA gaps at RMI — legacy admin accounts |
| Endpoint Security | 2 | EDR not deployed at RMI |
| Network Security | 2 | OT/IT not segmented at RMI |
| Data Protection | 2 | Policy written — not technically enforced |
| Vulnerability Management | 1 | CVSS-only prioritization — no scanning at RMI |
| Incident Response | 1 | Plan exists — never tested — no playbooks |
| Security Awareness Training | 2 | Generic annual CBT — low completion |
| Third Party Risk | 1 | No formal TPRM process |
| Governance & Compliance | 2 | 6 of 12 required policies documented |
| **Overall Program Maturity** | **2 — Developing** | |

---

### Organizational Security Stakeholders

| Role | Name | Entity | Notes |
|---|---|---|---|
| CISO (Fractional) | David Lightman | All entities | Primary security advisor |
| Executive Sponsor | Dr. Stephen Falken | Falken Holdings | Founder and managing partner — engaged but not technical |
| Operations Director | Jennifer Cross | Falken Holdings | Day-to-day operations — budget gatekeeper |
| IT Director | Marcus Webb | Falken Holdings / SPS | Manages FH and SPS IT — limited RMI visibility |
| Plant Manager / IT Lead | Bobby Rourke | RMI | Informal IT role — no security background |
| Legal Counsel | Patricia Holt | Falken Holdings | External GC — engaged on compliance matters |
| Finance Director | Alan Beale | Falken Holdings | McKittrick archetype — skeptical of security ROI |

---

### Crown Jewels
*The following assets represent the highest-value targets for an adversary.
These should be the primary reference for threat persona targeting and D3FEND prioritization.*

| Priority | Asset | Location | Classification | Business Impact if Compromised |
|---|---|---|---|---|
| 1 | Investment strategy and M&A pipeline documents | Azure SharePoint (FH) | Restricted | Catastrophic — competitive and financial ruin |
| 2 | SPS client PII database — 14,000+ staffing candidates | Azure SQL (SPS) | Restricted | Regulatory penalties, client loss, litigation |
| 3 | RMI precision manufacturing process documentation | On-premises file server (RMI) | Restricted | Loss of competitive IP — primary differentiator |
| 4 | Consolidated financial records and partner equity data | Azure (FH) | Restricted | Fraud, litigation, partner disputes |
| 5 | RMI OT/SCADA-adjacent manufacturing systems | On-premises (RMI) | Restricted | Operational shutdown — $85K/day downtime cost |
| 6 | FPG property development plans and client contracts | On-premises (FPG) | Confidential | Project delays, client trust damage |
| 7 | Employee and payroll records (all entities) | ADP + Azure (FH) | Restricted | Identity theft, regulatory penalties |

---

### Business Context for Threat Modeling

| Factor | Detail |
|---|---|
| **Active M&A Activity** | Yes — evaluating two acquisition targets in 2026 |
| **Third Party Dependencies** | High — SPS relies on 12+ staffing platform integrations |
| **Supply Chain Complexity** | Medium — RMI sources from 6 primary vendors, 2 international |
| **Recent Security Incidents** | Phishing attempt Q4 2025 — no compromise confirmed but investigated |
| **Near-Misses** | RMI employee clicked phishing link — saved by ISP-level block |
| **Highest Business Impact Scenario** | Ransomware encrypting RMI manufacturing systems during peak production — estimated $2.1M impact over 25 days |
| **Cyber Insurance Coverage** | $5M limit — $100K retention — Coalition Insurance |
| **Board Risk Appetite** | Low tolerance for operational disruption — moderate tolerance for data risk (not fully informed) |
