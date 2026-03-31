# Falken Holdings — Data Classification Register
## WOPR Context File v1.0 | Last Updated: Q1 2026
## Classification: CONFIDENTIAL — WOPR USE ONLY

---

### Purpose
This register tells WOPR what data Falken Holdings
handles, how it is classified, and how sensitive it
is to the organization. This context must inform
threat persona targeting, crown jewel prioritization,
D3FEND mitigation recommendations, and board
reporting outputs.

---

### Classification Tiers

| Tier | Label | Color Code | Description | Example |
|---|---|---|---|---|
| 1 | Public | Green | Approved for public release | Marketing materials, job postings |
| 2 | Internal | Yellow | General internal use only | Project plans, internal memos |
| 3 | Confidential | Orange | Sensitive business data — limited distribution | Vendor contracts, employee records |
| 4 | Restricted | Red | Highest sensitivity — tightly controlled, need-to-know only | M&A documents, client PII, manufacturing IP |

---

### Data Inventory by Classification

#### TIER 4 — RESTRICTED
*Loss, exposure, or encryption would be catastrophic to the business*
*These are the primary targets for Joshua*

| Data Type | Entity | Volume | Primary Location | Regulatory Concern | IP Concern | Joshua Target Priority |
|---|---|---|---|---|---|---|
| M&A strategy, deal memos, acquisition pipeline | FH | ~2,400 documents | Azure SharePoint — FH restricted site | High — securities implications | High — competitive intelligence | CRITICAL |
| Partner equity and investment records | FH | ~800 documents | Azure SharePoint + local CFO workstation | High — financial fraud risk | High | CRITICAL |
| SPS candidate and client PII database | SPS | 14,200+ records | Azure SQL Database | High — IL/WI/IN privacy law | Low | CRITICAL |
| RMI precision manufacturing process docs | RMI | ~1,100 documents | On-premises file server — unencrypted | Low | High — primary competitive differentiator | CRITICAL |
| OT system configurations and network diagrams | RMI | ~300 documents | On-premises — IT lead laptop | Low | High — attacker reconnaissance value | HIGH |
| Consolidated financial statements | FH | Annual + quarterly | Azure SharePoint + QuickBooks | High | Medium | HIGH |
| Executive compensation and equity agreements | FH | ~45 documents | Azure SharePoint — C-suite only | High | Low | HIGH |
| Payroll and HR records — all entities | ALL | ~520 employee records | ADP + Azure | High — identity theft risk | Low | HIGH |

---

#### TIER 3 — CONFIDENTIAL
*Loss or exposure would be significantly damaging*

| Data Type | Entity | Volume | Primary Location | Regulatory Concern | IP Concern | Notes |
|---|---|---|---|---|---|---|
| SPS client contracts and SOW documents | SPS | ~340 active contracts | Azure SharePoint | Medium | Medium | Client confidentiality obligations |
| FPG property development plans | FPG | ~180 active projects | On-premises file server | Low | Medium | Competitive intelligence risk |
| Vendor and supply chain contracts | ALL | ~200 contracts | Mixed — email and SharePoint | Medium | Low | Third party risk exposure |
| IT architecture and network diagrams | ALL | ~60 documents | IT Director laptop + SharePoint | Low | High | Attacker reconnaissance value |
| Security policies and procedures | ALL | 6 documented policies | SharePoint | Low | High | Should never be public |
| RMI supplier pricing and sourcing agreements | RMI | ~85 documents | On-premises + email | Low | Medium | Competitive sensitivity |
| Employee performance and disciplinary records | ALL | ~520 records | ADP | Medium | Low | Insider threat relevance |

---

#### TIER 2 — INTERNAL
*Loss or exposure would be disruptive but manageable*

| Data Type | Entity | Primary Location | Notes |
|---|---|---|---|
| Internal project plans and timelines | ALL | SharePoint / email | |
| General business communications | ALL | Microsoft 365 email | |
| Approved vendor lists | ALL | SharePoint | |
| Training records and completion logs | ALL | SharePoint / LMS | |
| Non-sensitive financial reports | ALL | SharePoint | |
| Facilities and property records | FPG | On-premises | |

---

#### TIER 1 — PUBLIC
*Approved for external release — no protection required*

| Data Type | Entity | Notes |
|---|---|---|
| Marketing materials and brochures | ALL | |
| Press releases | FH | Board-approved only |
| Job postings | ALL | Posted to external job boards |
| Public-facing website content | FH, SPS, FPG | |

---

### IP vs. Regulatory Sensitivity Matrix
*Use this to calibrate Joshua's motivation and TTP selection*

```
                    LOW IP CONCERN          HIGH IP CONCERN
                  ┌─────────────────────┬─────────────────────┐
HIGH REGULATORY   │ SPS Client PII      │ M&A Strategy Docs   │
CONCERN           │ Payroll / HR Records│ Partner Equity Data │
                  │ Financial Records   │                     │
                  │                     │                     │
                  │ Focus: Compliance   │ Focus: BOTH         │
                  │ controls, breach    │ Compliance AND      │
                  │ notification        │ espionage modeling  │
                  ├─────────────────────┼─────────────────────┤
LOW REGULATORY    │ Internal Comms      │ RMI Manufacturing IP│
CONCERN           │ Project Plans       │ OT Configurations   │
                  │ Vendor Lists        │ IT Architecture Docs│
                  │                     │                     │
                  │ Focus: Integrity    │ Focus: Espionage,   │
                  │ and availability    │ insider threat,     │
                  │ over confid.        │ data exfiltration   │
                  └─────────────────────┴─────────────────────┘
```

---

### Data Location Risk Summary
*For WOPR gap analysis — these locations represent the highest exposure*

| Location | Entity | Classification Held | Security Status | Risk Level |
|---|---|---|---|---|
| RMI on-premises file server | RMI | Restricted + Confidential | Unencrypted — no EDR — no DLP | CRITICAL |
| IT Director laptop | FH | Confidential | Encrypted — no DLP monitoring | HIGH |
| CFO workstation | FH | Restricted | Encrypted — no DLP — no PAM | HIGH |
| Azure SharePoint — FH restricted site | FH | Restricted | MFA protected — no DLP configured | MEDIUM-HIGH |
| Azure SQL Database — SPS | SPS | Restricted | Encrypted at rest — limited access logging | MEDIUM |
| Microsoft 365 email — all entities | ALL | Mixed tiers | Safe Links partial — no DLP — DMARC not enforced | HIGH |
| ADP payroll system | ALL | Restricted | Third party managed — SSO not integrated | MEDIUM |
| QuickBooks Enterprise — RMI | RMI | Confidential | On-premises — no cloud backup — local admin access | HIGH |

---

### Instructions for WOPR
When building a threat persona or gap analysis
for Falken Holdings:

1. Always prioritize TTPs that provide access
   to Tier 4 — Restricted data assets
2. Weight Joshua's motivation using the IP vs.
   Regulatory Sensitivity Matrix above
3. The RMI on-premises file server is the
   single highest-risk data location —
   flag in every threat modeling output
4. Map D3FEND mitigations to the highest
   tier data assets first
5. Any TTP that provides direct path to
   M&A documents or RMI manufacturing IP
   should be flagged as CRITICAL PRIORITY
6. SPS PII exposure carries regulatory
   penalty risk — flag compliance
   implications in executive outputs
7. The unencrypted RMI file server is an
   immediate finding — include in every
   board-level output regardless of TTP
