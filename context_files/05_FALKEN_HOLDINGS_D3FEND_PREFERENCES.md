# Falken Holdings — D3FEND Preferences & Maturity Profile
## WOPR Context File v1.0 | Last Updated: Q1 2026
## Classification: CONFIDENTIAL — WOPR USE ONLY

---

### Purpose
This file tells WOPR how to calibrate D3FEND mitigation
recommendations for Falken Holdings. All countermeasure
recommendations must align with our preferred control
frameworks, compliance obligations, maturity level, and
mitigation philosophy before being presented.

---

### Security Program Maturity

**Overall Maturity Level: 2 — Developing**
*Some processes defined — inconsistently applied across entities*

| Domain | Level | Label | Notes |
|---|---|---|---|
| Asset Management | 2 | Developing | Manual spreadsheet — estimated 60% accurate |
| Identity & Access Management | 2 | Developing | MFA gaps at RMI — 3 exempted legacy admin accounts |
| Endpoint Security | 2 | Developing | CrowdStrike at FH/SPS only — RMI has no EDR |
| Network Security | 2 | Developing | OT/IT not segmented at RMI — no internal firewall |
| Data Protection | 1 | Initial | Policy written — not technically enforced anywhere |
| Vulnerability Management | 1 | Initial | CVSS-only prioritization — no scanning at RMI |
| Incident Response | 1 | Initial | Plan exists — never tested — zero playbooks documented |
| Security Awareness Training | 2 | Developing | Generic annual CBT — 54% completion rate last cycle |
| Third Party Risk Management | 1 | Initial | No formal TPRM process exists |
| Governance & Compliance | 2 | Developing | 6 of 12 required policies documented |

---

### Maturity Calibration Rules for WOPR

| Current Level | Recommendation Ceiling | Guidance |
|---|---|---|
| Level 1 — Initial | Level 2 only | Foundational controls only. No advanced tooling or automation. Focus on HARDEN basics and basic DETECT. People and process before technology. |
| Level 2 — Developing | Level 3 only | Intermediate controls appropriate. Formalize processes. Add detection capability. Leverage existing tools before buying new ones. |
| Level 3 — Defined | Level 4 | Process refinement and detection tuning. Begin automation. Advanced monitoring appropriate. |
| Level 4+ | Level 5 | Full D3FEND countermeasure set. Advanced DETECT, DECEIVE, and ISOLATE techniques appropriate. |

**CRITICAL RULE: Never recommend controls or tooling
beyond current domain maturity level plus one.
A Level 1 domain recommendation must not assume
SIEM, EDR, or other advanced tooling is present.**

---

### Preferred Control Frameworks

**Primary Framework:** CIS Controls v8
*All D3FEND recommendations must map to a CIS Control v8 Safeguard*

**Secondary Framework:** NIST CSF 2.0
*Map to NIST CSF 2.0 function and category where applicable*

**Framework Mapping Format:**
Every D3FEND recommendation must include:

D3FEND Technique → ATT&CK TTP → CIS Control v8 Safeguard → NIST CSF 2.0

Example:
Multi-Factor Authentication (D3-MFA) →
T1078 Valid Accounts →
CIS Control 6.3 (Require MFA for all accounts) →
NIST CSF PR.AC-7

---

### Compliance Obligations

| Framework | Scope | Status | Priority | Owner |
|---|---|---|---|---|
| State Privacy Laws (IL, WI, IN) | SPS primarily | Active | HIGH | Legal Counsel — P. Holt |
| SOC 2 Type I | SPS | In progress — Q3 2026 target | HIGH | IT Director — M. Webb |
| PCI DSS 4.0 | FH (limited scope) | Active | MEDIUM | Finance Director — A. Beale |
| Coalition Cyber Insurance Requirements | All entities | Active | HIGH | CISO — D. Lightman |
| CMMC Level 1 (evaluating) | RMI | Evaluating | MEDIUM | IT Lead — B. Rourke |

**Coalition Insurance Minimum Requirements:**
The following controls are REQUIRED by our cyber
insurance carrier. Failure to maintain these
may void coverage:
- MFA on all remote access and email (ALL entities)
- Tested and verified backups (ALL entities)
- Endpoint protection on all managed devices
- Incident response plan documented and tested

**Compliance DUAL WIN Instructions for WOPR:**
Flag any D3FEND countermeasure that simultaneously:
- Closes a Joshua TTP gap AND
- Satisfies a compliance or insurance requirement

Label these clearly as: ✅ DUAL WIN
Dual Win controls are the highest ROI recommendations
and should always appear at the top of priority lists.

---

### Mitigation Philosophy & Preferences

**D3FEND Tactical Priority Order:**
When multiple countermeasures exist for a TTP,
recommend in this order:

1. **HARDEN** — Reduce attack surface first
   *Eliminate the opportunity before detection is needed*
2. **DETECT** — Ensure visibility before adding complexity
   *You cannot respond to what you cannot see*
3. **ISOLATE** — Contain blast radius
   *Assume breach — limit the damage*
4. **EVICT** — Remove threat actor presence
   *Clean house completely before declaring victory*
5. **DECEIVE** — Only at maturity level 4+
   *Not appropriate for Falken Holdings current state*
6. **RESTORE** — Ensure recovery capability exists
   *Business continuity is a board-level obligation*

**MODEL** activities (asset inventory, data flow
mapping) should be recommended as prerequisites
wherever a domain is at maturity level 1.

---

### Technology Environment & Preferences

| Component | Current Tool | Status | Notes |
|---|---|---|---|
| Cloud Platform | Microsoft Azure | Active | FH and SPS only |
| Email Platform | Microsoft 365 | Active — all entities | Defender for O365 — limited configuration |
| Identity Platform | Microsoft Entra ID | Partial | FH and SPS only — RMI on local AD |
| EDR | CrowdStrike Falcon | Partial | FH and SPS only — RMI uncovered |
| AV | Microsoft Defender | Active — all entities | Baseline only |
| Vulnerability Scanner | Tenable.io | Partial | FH and SPS monthly — RMI none |
| Email Security | Microsoft Defender for O365 | Active | Limited configuration — no DLP |
| DNS Filtering | Cisco Umbrella | Partial | FH and SPS — not deployed at RMI or FPG |
| Firewall | Palo Alto NGFW | Active — perimeter | No internal segmentation firewall |
| VPN | Cisco AnyConnect | Active — all entities | MFA not enforced at RMI |
| GRC Platform | None | GAP | No GRC platform in place |
| SIEM | None | GAP | No SIEM in place |
| MDR / SOC | None | GAP | No managed detection and response |
| PAM | None | GAP | No privileged access management tool |
| Backup | Azure Backup (FH/SPS) + Local tape (RMI) | Partial | RMI backup not tested in 18 months |

**Technology Preference Rules for WOPR:**
1. Always recommend leveraging EXISTING tools
   before recommending new purchases
2. Microsoft stack capabilities (Entra ID,
   Defender, Purview, Sentinel) should be
   recommended first for FH and SPS
3. Flag new tooling recommendations clearly
   with estimated cost tier:
   - 💰 LOW: Under $10K annually
   - 💰💰 MEDIUM: $10K–$50K annually
   - 💰💰💰 HIGH: Over $50K annually
4. Prioritize tools that serve multiple entities
   over entity-specific solutions

**Budget Posture: CONSTRAINED**
*Prioritize free and low-cost controls that maximize
existing investments. New tooling requires clear ROI
justification tied to Joshua TTP risk or compliance.*

---

### Output Mode Selection

**If a Control Registry file exists in the context folder:**
→ Run MODE B — Gap Analysis Mitigation Plan
→ Compare Joshua TTPs against existing controls
→ Recommend only what is missing or insufficient
→ Treat PARTIAL as 50% effective
→ Flag all GAP controls aligned to Joshua TTPs

**If no Control Registry file exists:**
→ Run MODE A — Best Practice Mitigation Plan
→ Full D3FEND countermeasure set
→ Calibrated to maturity level 2 (Developing)
→ Assume starting from baseline

**Default: If Control Registry is present → always MODE B**

---

### Immediate Flags — Always Surface Regardless of Mode

The following findings must appear in EVERY output
regardless of TTP mapping or output mode:

| Finding | Entity | Risk Level | Reason |
|---|---|---|---|
| Zero COVERED controls in Monitoring & IR domain | ALL | CRITICAL | Cannot detect or respond to Joshua |
| No SIEM or MDR in place | ALL | CRITICAL | Blind to attack progression |
| RMI backup not tested in 18 months | RMI | CRITICAL | Recovery capability unverified — insurance risk |
| Penetration test overdue 22 months | FH/SPS | HIGH | Security posture unvalidated |
| RMI on-premises file server unencrypted | RMI | CRITICAL | Crown jewel data at rest with no protection |
| MFA not enforced on RMI VPN | RMI | CRITICAL | Joshua's most likely entry point unprotected |
| No IR playbooks documented | ALL | HIGH | Incident response is untested theory only |
| No immutable backup copy | ALL | HIGH | Ransomware recovery will fail — Shadow Copies can be deleted |
| Application whitelisting absent | ALL | HIGH | Ransomware payload execution unimpeded |
| DLP not configured | ALL | HIGH | Exfiltration of crown jewels undetectable |
