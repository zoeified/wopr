# ATT&CK Navigator JSON Layer Specification
## WOPR Context File v1.0
## Based on MITRE ATT&CK Navigator Layer Format v4.5
## ATT&CK Version: 16 | Navigator Version: 5.2.0
## Reference: https://github.com/mitre-attack/attack-navigator

---

### Purpose
This file tells WOPR exactly how to format an ATT&CK
Navigator JSON layer file. When asked to generate a
Navigator layer, WOPR must produce valid JSON matching
this specification exactly so it can be uploaded
directly to the Navigator without errors.

Navigator URL: https://mitre-attack.github.io/attack-navigator/

---

### Critical Formatting Rules

1. Output CLEAN VALID JSON ONLY
2. No markdown code fences around the JSON
3. No explanation text before or after the JSON
4. All techniqueIDs must follow exact format: "T####" or "T####.###"
5. All tactic values must use exact tactic ID strings (see list below)
6. Output must be paste-ready into a .json file
7. File must upload directly to Navigator without errors

---

### Complete Layer Structure — Annotated

```json
{
  "name": "Joshua — Falken Holdings Threat Persona",
  "versions": {
    "attack": "16",
    "navigator": "5.2.0",
    "layer": "4.5"
  },
  "domain": "enterprise-attack",
  "description": "Threat persona representing Joshua — a financially motivated ransomware affiliate and initial access broker targeting mid-market US holding companies in manufacturing, professional services, and property development.",
  "filters": {
    "platforms": [
      "Windows",
      "Linux",
      "Azure AD",
      "Office 365",
      "SaaS"
    ]
  },
  "sorting": 0,
  "layout": {
    "layout": "side",
    "showName": true,
    "showID": true,
    "showAggregateScores": false,
    "countUnscored": false,
    "aggregateFunction": "average",
    "expandedSubtechniques": "annotated"
  },
  "hideDisabled": false,
  "techniques": [
    {
      "techniqueID": "T1566",
      "tactic": "initial-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "Joshua's primary initial access vector. Spearphishing emails targeting Falken Holdings finance and HR staff at SPS. Lure themes include payroll updates, staffing platform notifications, and vendor invoices.",
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1566.001",
      "tactic": "initial-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "Malicious Office document attachments — macro-enabled Excel files disguised as vendor invoices targeting RMI accounting staff."
    },
    {
      "techniqueID": "T1566.002",
      "tactic": "initial-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "Spearphishing links — credential harvesting pages spoofing Microsoft 365 login targeting FH executive staff."
    },
    {
      "techniqueID": "T1078",
      "tactic": "initial-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "Valid accounts purchased from initial access brokers. RMI VPN and legacy local admin accounts are high-value targets due to weak MFA enforcement.",
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1078.002",
      "tactic": "persistence",
      "score": 1,
      "color": "#ff6666",
      "comment": "Domain accounts — RMI local Active Directory accounts with weak password policies are a primary target."
    },
    {
      "techniqueID": "T1133",
      "tactic": "initial-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "External remote services — RMI VPN with inconsistent MFA enforcement. Legacy RDP exposure on RMI manufacturing network."
    },
    {
      "techniqueID": "T1059",
      "tactic": "execution",
      "score": 1,
      "color": "#ff6666",
      "comment": "Command and scripting interpreter — PowerShell used extensively by Joshua for post-exploitation automation.",
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1059.001",
      "tactic": "execution",
      "score": 1,
      "color": "#ff6666",
      "comment": "PowerShell — used for enumeration, lateral movement preparation, and ransomware deployment at RMI."
    },
    {
      "techniqueID": "T1547",
      "tactic": "persistence",
      "score": 1,
      "color": "#ff6666",
      "comment": "Boot or logon autostart execution — Joshua establishes persistence via registry run keys to survive reboots.",
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1110",
      "tactic": "credential-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "Brute force — RMI legacy systems with no account lockout policy. Credential stuffing against Microsoft 365 using previously breached credential lists.",
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1003",
      "tactic": "credential-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "OS credential dumping — Mimikatz used to harvest credentials from RMI domain controllers. No EDR on RMI endpoints to detect.",
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1003.001",
      "tactic": "credential-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "LSASS memory dumping — primary credential harvesting technique at RMI due to absence of Credential Guard."
    },
    {
      "techniqueID": "T1021",
      "tactic": "lateral-movement",
      "score": 1,
      "color": "#ff6666",
      "comment": "Remote services — SMB and RDP lateral movement within RMI flat network. No internal segmentation firewall to impede movement.",
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1021.001",
      "tactic": "lateral-movement",
      "score": 1,
      "color": "#ff6666",
      "comment": "RDP — used to move laterally across RMI manufacturing network. Multiple systems allow RDP with domain credentials."
    },
    {
      "techniqueID": "T1083",
      "tactic": "discovery",
      "score": 1,
      "color": "#ff6666",
      "comment": "File and directory discovery — Joshua enumerates RMI file server to locate manufacturing IP and FH financial documents."
    },
    {
      "techniqueID": "T1057",
      "tactic": "discovery",
      "score": 1,
      "color": "#ff6666",
      "comment": "Process discovery — used to identify security tools and AV presence before deploying ransomware payload."
    },
    {
      "techniqueID": "T1041",
      "tactic": "exfiltration",
      "score": 1,
      "color": "#ff6666",
      "comment": "Exfiltration over C2 channel — Joshua exfiltrates M&A documents and SPS PII before encryption. Double extortion leverage."
    },
    {
      "techniqueID": "T1567",
      "tactic": "exfiltration",
      "score": 1,
      "color": "#ff6666",
      "comment": "Exfiltration to cloud storage — MEGA.nz and similar file sharing services used to stage stolen data. No DLP to detect.",
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1486",
      "tactic": "impact",
      "score": 1,
      "color": "#ff6666",
      "comment": "Data encrypted for impact — ransomware deployment targeting RMI file servers and OT-adjacent systems. Estimated $2.1M operational impact over 25-day recovery.",
      "showSubtechniques": false
    },
    {
      "techniqueID": "T1490",
      "tactic": "impact",
      "score": 1,
      "color": "#ff6666",
      "comment": "Inhibit system recovery — Joshua deletes Volume Shadow Copies to prevent recovery. No immutable backup exists at Falken Holdings."
    },
    {
      "techniqueID": "T1489",
      "tactic": "impact",
      "score": 1,
      "color": "#ff6666",
      "comment": "Service stop — security services and backup agents terminated before ransomware deployment. No SIEM to alert on service termination."
    }
  ],
  "gradient": {
    "colors": [
      "#ffffff",
      "#ff6666"
    ],
    "minValue": 0,
    "maxValue": 1
  },
  "legendItems": [
    {
      "label": "Joshua TTP — Confirmed",
      "color": "#ff6666"
    }
  ],
  "metadata": [],
  "links": [],
  "showTacticRowBackground": true,
  "tacticRowBackground": "#dddddd",
  "selectTechniquesAcrossTactics": false,
  "selectSubtechniquesWithParent": false
}
```

---

### Valid Tactic IDs
*Use these exact strings in the tactic field*

| Tactic ID | Display Name |
|---|---|
| reconnaissance | Reconnaissance |
| resource-development | Resource Development |
| initial-access | Initial Access |
| execution | Execution |
| persistence | Persistence |
| privilege-escalation | Privilege Escalation |
| defense-evasion | Defense Evasion |
| credential-access | Credential Access |
| discovery | Discovery |
| lateral-movement | Lateral Movement |
| collection | Collection |
| command-and-control | Command and Control |
| exfiltration | Exfiltration |
| impact | Impact |

---

### Gap Analysis Layer Scoring Convention
*Use this when generating the gap analysis layer
using the Navigator subtract function*

| Score | Meaning | Color |
|---|---|---|
| +1 | Joshua uses this TTP — not tested or covered | Red #ff6666 |
| 0 | Overlap — TTP addressed in controls or assessment | Yellow #ffcc00 |
| -1 | Covered or tested — not in Joshua's confirmed playbook | Green #66cc66 |

Score expression for gap analysis layer:
Layer A (Joshua Persona) MINUS Layer B (Controls Coverage)
Where A = Joshua Persona Layer
Where B = Control Registry Coverage Layer

---

### WOPR Output Instructions
When generating a Navigator JSON layer:
1. Always use ATT&CK version 16 and layer format 4.5
2. Include techniqueID and tactic for every entry
3. Add a Falken Holdings-specific comment on EVERY technique
4. Reference crown jewels and data classification in comments
5. Include both parent techniques and key subtechniques
6. Output clean valid JSON only — no markdown fences
7. Validate all techniqueIDs match ATT&CK format before output
8. The JSON must be uploadable to Navigator with zero errors
