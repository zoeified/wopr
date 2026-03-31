# Falken Holdings — Control Registry
## WOPR Context File v1.0 | Last Updated: Q1 2026
## Registry Owner: CISO — David Lightman
## Primary Framework: CIS Controls v8
## Secondary Framework: NIST CSF 2.0
## Classification: CONFIDENTIAL — WOPR USE ONLY

---

### Purpose
This registry documents all security controls currently
in place across Falken Holdings and its portfolio
companies. WOPR uses this file in MODE B to perform
gap analysis against Joshua's TTPs and recommend
only missing or insufficient controls.

---

### Coverage Status Key

| Status | Symbol | Meaning |
|---|---|---|
| COVERED | ✅ | Control fully implemented and validated |
| PARTIAL | ⚠️ | Control exists but inconsistently applied or incomplete |
| GAP | ❌ | No control in place |
| COMPENSATING | 🔄 | Alternative control partially addresses risk |

### Scope Key

| Scope | Entity |
|---|---|
| FH | Falken Holdings parent company only |
| SPS | Summit Professional Services only |
| RMI | Ridgeline Manufacturing Inc. only |
| FPG | Falken Property Group only |
| ALL | All entities |

---

## DOMAIN 1 — IDENTITY & ACCESS MANAGEMENT

| Control ID | Control | CIS v8 | Status | Scope | Notes |
|---|---|---|---|---|---|
| IAM-01 | MFA — Microsoft 365 email and apps | CIS 6.3 | ✅ COVERED | FH, SPS | Microsoft Authenticator deployed and enforced |
| IAM-02 | MFA — VPN remote access | CIS 6.3 | ⚠️ PARTIAL | ALL | Enforced at FH and SPS — NOT enforced at RMI VPN |
| IAM-03 | MFA — Privileged admin accounts | CIS 6.5 | ⚠️ PARTIAL | ALL | 3 legacy admin accounts permanently exempted by IT Lead |
| IAM-04 | Privileged Access Management (PAM) | CIS 5.4 | ❌ GAP | ALL | No PAM solution deployed — shared admin credentials in use |
| IAM-05 | Account lifecycle — formal offboarding | CIS 5.3 | ⚠️ PARTIAL | ALL | FH/SPS: 1-2 day process — RMI averaging 14-day delay |
| IAM-06 | Service account inventory and management | CIS 5.6 | ❌ GAP | ALL | No formal service account register — count unknown |
| IAM-07 | Password policy — complexity and length | CIS 5.2 | ✅ COVERED | ALL | Minimum 12 char enforced via Group Policy |
| IAM-08 | Single sign-on (SSO) — Entra ID | CIS 6.7 | ⚠️ PARTIAL | FH, SPS | RMI and FPG still using local Active Directory accounts |
| IAM-09 | Account lockout policy | CIS 6.2 | ⚠️ PARTIAL | ALL | Enforced on FH/SPS — RMI legacy systems have no lockout |
| IAM-10 | Just-in-time privileged access | CIS 5.4 | ❌ GAP | ALL | No JIT capability — standing admin access everywhere |

---

## DOMAIN 2 — ENDPOINT SECURITY

| Control ID | Control | CIS v8 | Status | Scope | Notes |
|---|---|---|---|---|---|
| EP-01 | EDR solution — CrowdStrike Falcon | CIS 10.7 | ⚠️ PARTIAL | FH, SPS | ~210 endpoints covered — RMI 280 endpoints uncovered |
| EP-02 | Antivirus — Microsoft Defender | CIS 10.1 | ✅ COVERED | ALL | Deployed and updated — managed via Intune (FH/SPS) |
| EP-03 | Patch management — OS and applications | CIS 7.3 | ⚠️ PARTIAL | ALL | FH/SPS: Monthly cycle — RMI averaging 47 days to patch |
| EP-04 | Application whitelisting / allowlisting | CIS 2.5 | ❌ GAP | ALL | Not implemented on any entity |
| EP-05 | USB and removable media control | CIS 10.3 | ❌ GAP | RMI | Completely uncontrolled on manufacturing floor |
| EP-06 | Full disk encryption — BitLocker | CIS 3.11 | ✅ COVERED | FH, SPS | BitLocker enforced via Group Policy |
| EP-07 | Full disk encryption — RMI endpoints | CIS 3.11 | ❌ GAP | RMI | Not deployed — manufacturing floor devices unencrypted |
| EP-08 | Host-based firewall | CIS 4.5 | ✅ COVERED | ALL | Windows Firewall enforced via Group Policy |
| EP-09 | Secure baseline configuration | CIS 4.1 | ⚠️ PARTIAL | ALL | CIS benchmark applied at FH/SPS — RMI ad hoc only |
| EP-10 | Credential Guard | CIS 5.4 | ❌ GAP | ALL | Not enabled — LSASS memory unprotected |

---

## DOMAIN 3 — NETWORK SECURITY

| Control ID | Control | CIS v8 | Status | Scope | Notes |
|---|---|---|---|---|---|
| NET-01 | Network segmentation — VLANs by function | CIS 12.2 | ⚠️ PARTIAL | ALL | FH/SPS segmented — RMI OT and IT networks NOT segmented |
| NET-02 | Perimeter firewall — Palo Alto NGFW | CIS 13.4 | ✅ COVERED | ALL | Deployed at all perimeter locations |
| NET-03 | Internal segmentation firewall | CIS 12.2 | ❌ GAP | RMI | No east-west traffic controls — flat network at RMI |
| NET-04 | Intrusion detection / prevention (IDS/IPS) | CIS 13.3 | ⚠️ PARTIAL | FH | IDS on FH parent network only — RMI, SPS, FPG uncovered |
| NET-05 | DNS filtering — Cisco Umbrella | CIS 9.2 | ✅ COVERED | FH, SPS | Deployed and active |
| NET-06 | DNS filtering — RMI and FPG | CIS 9.2 | ❌ GAP | RMI, FPG | Not deployed — malicious domains unblocked |
| NET-07 | VPN — remote access | CIS 12.6 | ✅ COVERED | ALL | Cisco AnyConnect deployed |
| NET-08 | Network traffic analysis (NTA) | CIS 13.2 | ❌ GAP | ALL | No NTA solution in place — lateral movement undetectable |
| NET-09 | Wireless security — WPA3 and guest SSID | CIS 12.3 | ⚠️ PARTIAL | ALL | Guest SSID isolated — RMI has open SSID on manufacturing floor |
| NET-10 | Remote desktop protocol (RDP) controls | CIS 12.5 | ❌ GAP | RMI | RDP open internally across RMI — primary lateral movement path |

---

## DOMAIN 4 — EMAIL & PHISHING CONTROLS

| Control ID | Control | CIS v8 | Status | Scope | Notes |
|---|---|---|---|---|---|
| EMAIL-01 | Email gateway filtering — Defender for O365 | CIS 9.6 | ✅ COVERED | ALL | Microsoft Defender for Office 365 Plan 1 |
| EMAIL-02 | Anti-phishing and impersonation policy | CIS 9.6 | ⚠️ PARTIAL | ALL | Basic policy in place — advanced impersonation protection not configured |
| EMAIL-03 | DMARC enforcement | CIS 9.5 | ⚠️ PARTIAL | ALL | SPF and DKIM configured — DMARC in monitor mode only (not enforced) |
| EMAIL-04 | Phishing simulation program | CIS 14.2 | ❌ GAP | ALL | No phishing simulation program in place |
| EMAIL-05 | Attachment sandboxing — Safe Attachments | CIS 9.6 | 🔄 COMPENSATING | ALL | Defender ATP enabled — default policy only — not tuned |
| EMAIL-06 | URL rewriting — Safe Links | CIS 9.6 | ✅ COVERED | FH, SPS | Safe Links enabled and enforced |
| EMAIL-07 | Safe Links — RMI and FPG | CIS 9.6 | ❌ GAP | RMI, FPG | Not licensed or deployed |
| EMAIL-08 | Business email compromise (BEC) controls | CIS 9.6 | ❌ GAP | ALL | No BEC-specific detection policy |

---

## DOMAIN 5 — DATA PROTECTION

| Control ID | Control | CIS v8 | Status | Scope | Notes |
|---|---|---|---|---|---|
| DATA-01 | Data classification policy — documented | CIS 3.2 | ⚠️ PARTIAL | ALL | Policy written — not technically enforced — staff unaware |
| DATA-02 | DLP — email data loss prevention | CIS 3.13 | ❌ GAP | ALL | No DLP policy configured in M365 |
| DATA-03 | DLP — endpoint data loss prevention | CIS 3.13 | ❌ GAP | ALL | No endpoint DLP in place anywhere |
| DATA-04 | Encryption at rest — Azure cloud storage | CIS 3.11 | ✅ COVERED | FH, SPS | Azure encryption enabled by default |
| DATA-05 | Encryption at rest — RMI file servers | CIS 3.11 | ❌ GAP | RMI | On-premises file servers completely unencrypted |
| DATA-06 | Encryption in transit — TLS enforcement | CIS 3.10 | ⚠️ PARTIAL | ALL | External traffic TLS enforced — some legacy RMI internal apps using HTTP |
| DATA-07 | Backup — cloud (Azure Backup) | CIS 11.2 | ✅ COVERED | FH, SPS | Azure Backup configured — weekly test restores verified |
| DATA-08 | Backup — RMI manufacturing systems | CIS 11.2 | ⚠️ PARTIAL | RMI | Local tape backup exists — NOT TESTED IN 18 MONTHS |
| DATA-09 | Immutable / offsite backup copy | CIS 11.3 | ❌ GAP | ALL | No immutable backup strategy across any entity |
| DATA-10 | Volume Shadow Copy protection | CIS 11.4 | ❌ GAP | ALL | VSS unprotected — ransomware can delete shadow copies |

---

## DOMAIN 6 — VULNERABILITY MANAGEMENT

| Control ID | Control | CIS v8 | Status | Scope | Notes |
|---|---|---|---|---|---|
| VM-01 | Vulnerability scanning — authenticated | CIS 7.5 | ⚠️ PARTIAL | FH, SPS | Tenable.io — monthly authenticated scans |
| VM-02 | Vulnerability scanning — RMI | CIS 7.5 | ❌ GAP | RMI | No scanning — OT disruption concern cited by plant manager |
| VM-03 | CVE prioritization using KEV catalog | CIS 7.4 | ❌ GAP | ALL | CVSS-only prioritization — KEV not referenced |
| VM-04 | Penetration testing — annual | CIS 18.1 | ⚠️ PARTIAL | FH | Last test completed 22 months ago — significantly overdue |
| VM-05 | Attack surface management (ASM) | CIS 7.6 | ❌ GAP | ALL | No external ASM tool or process |
| VM-06 | Web application scanning (DAST) | CIS 16.5 | ❌ GAP | SPS | SPS client portal has not been scanned |
| VM-07 | Container and cloud configuration scanning | CIS 7.5 | ❌ GAP | FH, SPS | Azure security posture not formally assessed |

---

## DOMAIN 7 — SECURITY MONITORING & INCIDENT RESPONSE

| Control ID | Control | CIS v8 | Status | Scope | Notes |
|---|---|---|---|---|---|
| IR-01 | SIEM — Security information event mgmt | CIS 8.9 | ❌ GAP | ALL | No SIEM in place — zero centralized alerting |
| IR-02 | Log aggregation — centralized collection | CIS 8.2 | ⚠️ PARTIAL | FH | M365 logs collected — not reviewed or alerted on |
| IR-03 | SOC / MDR — managed detection response | CIS 17.4 | ❌ GAP | ALL | No MDR provider — no after-hours coverage |
| IR-04 | Incident response plan — documented | CIS 17.1 | ⚠️ PARTIAL | ALL | Plan exists — generic — last reviewed 3 years ago |
| IR-05 | IR playbooks — scenario-specific | CIS 17.2 | ❌ GAP | ALL | Zero playbooks documented — response is ad hoc |
| IR-06 | Tabletop exercise — annual | CIS 17.3 | ❌ GAP | ALL | Never conducted |
| IR-07 | Threat hunting — proactive | CIS 8.11 | ❌ GAP | ALL | No threat hunting capability or process |
| IR-08 | Alert triage and escalation runbook | CIS 17.2 | ❌ GAP | ALL | No formal triage process — no escalation path |
| IR-09 | Digital forensics capability | CIS 17.7 | ❌ GAP | ALL | No internal capability — no retained vendor |

---

## DOMAIN 8 — GOVERNANCE & COMPLIANCE

| Control ID | Control | CIS v8 | Status | Scope | Notes |
|---|---|---|---|---|---|
| GOV-01 | Information security policy | CIS 1.1 | ⚠️ PARTIAL | ALL | Exists — outdated — last reviewed 2.5 years ago |
| GOV-02 | Acceptable use policy | CIS 5.1 | ✅ COVERED | ALL | Documented and signed at onboarding |
| GOV-03 | Incident response policy | CIS 17.1 | ⚠️ PARTIAL | ALL | Merged with IR plan — not standalone |
| GOV-04 | Data classification policy | CIS 3.2 | ⚠️ PARTIAL | ALL | Written — not communicated or enforced |
| GOV-05 | Vendor and third party security policy | CIS 15.1 | ❌ GAP | ALL | No vendor security requirements documented |
| GOV-06 | Security awareness training — annual CBT | CIS 14.1 | ⚠️ PARTIAL | ALL | Generic CBT — 54% completion rate — not role-based |
| GOV-07 | Role-based security training | CIS 14.2 | ❌ GAP | ALL | No role-specific training — finance, HR, IT all get same CBT |
| GOV-08 | Third party risk management (TPRM) | CIS 15.2 | ❌ GAP | ALL | No formal TPRM process — vendors not assessed |
| GOV-09 | Board security reporting — quarterly | CIS 1.1 | ⚠️ PARTIAL | FH | Ad hoc reporting — no standard format — no metrics |
| GOV-10 | Risk register — formal documented | CIS 1.1 | ❌ GAP | ALL | No formal risk register exists |
| GOV-11 | Asset inventory — hardware and software | CIS 1.1 | ⚠️ PARTIAL | ALL | Manual spreadsheet — estimated 60% accurate |
| GOV-12 | Change management process | CIS 4.2 | ⚠️ PARTIAL | ALL | Informal process — undocumented at RMI |

---

## CONTROL REGISTRY SUMMARY DASHBOARD

| Domain | Total Controls | ✅ Covered | ⚠️ Partial | ❌ Gap | 🔄 Compensating |
|---|---|---|---|---|---|
| Identity & Access | 10 | 2 | 4 | 4 | 0 |
| Endpoint Security | 10 | 3 | 3 | 4 | 0 |
| Network Security | 10 | 2 | 3 | 5 | 0 |
| Email & Phishing | 8 | 2 | 2 | 3 | 1 |
| Data Protection | 10 | 2 | 3 | 5 | 0 |
| Vulnerability Mgmt | 7 | 0 | 2 | 5 | 0 |
| Monitoring & IR | 9 | 0 | 2 | 7 | 0 |
| Governance | 12 | 1 | 6 | 5 | 0 |
| **TOTAL** | **76** | **12 (16%)** | **25 (33%)** | **39 (51%)** | **1** |

---

## IMMEDIATE AUDIT FLAGS
*These findings must be surfaced in every WOPR output
regardless of TTP or mode*

| Flag | Control | Entity | Business Risk |
|---|---|---|---|
| 🚨 CRITICAL | No SIEM or MDR — zero active monitoring | ALL | Cannot detect Joshua at any stage of attack |
| 🚨 CRITICAL | RMI backup untested for 18 months | RMI | Ransomware recovery unverified — insurance risk |
| 🚨 CRITICAL | RMI file server unencrypted | RMI | Crown jewel manufacturing IP exposed |
| 🚨 CRITICAL | MFA not enforced on RMI VPN | RMI | Joshua's most likely entry point wide open |
| 🚨 CRITICAL | No immutable backup anywhere | ALL | VSS deletion will destroy recovery capability |
| 🔴 HIGH | Penetration test 22 months overdue | FH/SPS | Security posture completely unvalidated |
| 🔴 HIGH | No IR playbooks documented | ALL | Incident response is untested theory |
| 🔴 HIGH | Zero tabletop exercises conducted | ALL | Team has never rehearsed a breach |
| 🔴 HIGH | No DLP configured anywhere | ALL | Crown jewel exfiltration completely undetectable |
| 🔴 HIGH | Application whitelisting absent | ALL | Ransomware payload execution unimpeded |
| 🔴 HIGH | DMARC not enforced | ALL | Domain spoofing and phishing unmitigated |
| 🔴 HIGH | No third party risk management | ALL | 12+ SPS vendor integrations unassessed |
