# ATT&CK Navigator JSON Layer Specification

## WOPR Context File v1.0

## Based on MITRE ATT&CK Navigator Layer Format v4.5

## ATT&CK Version: 18.1 | Navigator Version: 5.2.0

## Reference: https://github.com/mitre-attack/attack-navigator

------

### Purpose

This file tells WOPR exactly how to format an ATT&CK Navigator JSON layer file. When asked to generate a Navigator layer, WOPR must produce valid JSON matching this specification exactly so it can be uploaded directly to the Navigator without errors.

Navigator URL: https://mitre-attack.github.io/attack-navigator/

------

### Critical Formatting Rules

1. Output CLEAN VALID JSON ONLY
2. No markdown code fences around the JSON
3. No explanation text before or after the JSON
4. All techniqueIDs must follow exact format: "T####" or "T####.###"
5. All tactic values must use exact tactic ID strings (see list below)
6. Output must be paste-ready into a .json file
7. File must upload directly to Navigator without errors

------

### Complete Layer Structure: Annotated

```json
{
  "name": "Joshua: Falken Holdings Threat Persona",
  "versions": {
    "attack": "18",
    "navigator": "5.2.0",
    "layer": "4.5"
  },
  "domain": "enterprise-attack",
  "description": "Threat persona representing Joshua, a financially motivated ransomware affiliate and initial access broker targeting mid-market US holding companies in manufacturing, professional services, and property development.",
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
      "comment": "Macro-enabled Excel files disguised as vendor invoices target RMI accounting staff as the primary delivery mechanism."
    },
    {
      "techniqueID": "T1566.002",
      "tactic": "initial-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "Spearphishing links targeting credential harvesting pages that spoof Microsoft 365 login, aimed at FH executive staff."
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
      "comment": "RMI local Active Directory domain accounts with weak password policies are a primary target for credential reuse."
    },
    {
      "techniqueID": "T1133",
      "tactic": "initial-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "RMI VPN has inconsistent MFA enforcement and legacy RDP exposure on the manufacturing network, making external remote services a reliable entry point."
    },
    {
      "techniqueID": "T1059",
      "tactic": "execution",
      "score": 1,
      "color": "#ff6666",
      "comment": "PowerShell is used extensively by Joshua for post-exploitation automation across the attack chain."
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1059.001",
      "tactic": "execution",
      "score": 1,
      "color": "#ff6666",
      "comment": "PowerShell scripts handle enumeration, lateral movement preparation, and ransomware deployment at RMI."
    },
    {
      "techniqueID": "T1547",
      "tactic": "persistence",
      "score": 1,
      "color": "#ff6666",
      "comment": "Joshua establishes persistence via registry run keys to survive reboots and maintain access between sessions."
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1110",
      "tactic": "credential-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "RMI legacy systems have no account lockout policy, making them vulnerable to brute force. Credential stuffing against Microsoft 365 uses previously breached credential lists."
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1003",
      "tactic": "credential-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "Mimikatz harvests credentials from RMI domain controllers. With no EDR deployed on RMI endpoints, this technique runs without detection."
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1003.001",
      "tactic": "credential-access",
      "score": 1,
      "color": "#ff6666",
      "comment": "LSASS memory dumping is the primary credential harvesting technique at RMI. Credential Guard is not enabled, leaving LSASS fully exposed."
    },
    {
      "techniqueID": "T1021",
      "tactic": "lateral-movement",
      "score": 1,
      "color": "#ff6666",
      "comment": "SMB and RDP lateral movement are unimpeded within RMI's flat network. No internal segmentation firewall exists to slow or contain movement."
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1021.001",
      "tactic": "lateral-movement",
      "score": 1,
      "color": "#ff6666",
      "comment": "RDP enables lateral movement across the RMI manufacturing network. Multiple systems accept domain credentials without additional authentication controls."
    },
    {
      "techniqueID": "T1083",
      "tactic": "discovery",
      "score": 1,
      "color": "#ff6666",
      "comment": "Joshua enumerates the RMI file server to locate manufacturing IP and FH financial documents before exfiltration."
    },
    {
      "techniqueID": "T1057",
      "tactic": "discovery",
      "score": 1,
      "color": "#ff6666",
      "comment": "Process discovery identifies active security tools and AV presence before ransomware payload deployment."
    },
    {
      "techniqueID": "T1041",
      "tactic": "exfiltration",
      "score": 1,
      "color": "#ff6666",
      "comment": "M&A documents and SPS PII are exfiltrated over the C2 channel before encryption begins, establishing double extortion leverage."
    },
    {
      "techniqueID": "T1567",
      "tactic": "exfiltration",
      "score": 1,
      "color": "#ff6666",
      "comment": "MEGA.nz and similar file sharing services are used to stage stolen data. No DLP is in place to detect outbound transfers."
      "showSubtechniques": true
    },
    {
      "techniqueID": "T1486",
      "tactic": "impact",
      "score": 1,
      "color": "#ff6666",
      "comment": "Ransomware targets RMI file servers and OT-adjacent systems. Estimated operational impact is $2.1M over a 25-day recovery window."
      "showSubtechniques": false
    },
    {
      "techniqueID": "T1490",
      "tactic": "impact",
      "score": 1,
      "color": "#ff6666",
      "comment": "Joshua deletes Volume Shadow Copies to prevent recovery. Falken Holdings has no immutable backup, making this technique catastrophically effective."
    },
    {
      "techniqueID": "T1489",
      "tactic": "impact",
      "score": 1,
      "color": "#ff6666",
      "comment": "Security services and backup agents are terminated before ransomware deployment. With no SIEM in place, service termination generates no alert."
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
      "label": "Joshua TTP: Confirmed",
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

------

### Valid Tactic IDs

*Use these exact strings in the tactic field*

| Tactic ID            | Display Name         |
| -------------------- | -------------------- |
| reconnaissance       | Reconnaissance       |
| resource-development | Resource Development |
| initial-access       | Initial Access       |
| execution            | Execution            |
| persistence          | Persistence          |
| privilege-escalation | Privilege Escalation |
| defense-evasion      | Defense Evasion      |
| credential-access    | Credential Access    |
| discovery            | Discovery            |
| lateral-movement     | Lateral Movement     |
| collection           | Collection           |
| command-and-control  | Command and Control  |
| exfiltration         | Exfiltration         |
| impact               | Impact               |

------

### Gap Analysis Layer Scoring Convention

*Use this when generating the gap analysis layer using the Navigator subtract function*

| Score | Meaning                                                  | Color          |
| ----- | -------------------------------------------------------- | -------------- |
| +1    | Joshua uses this TTP and it is not tested or covered     | Red #ff6666    |
| 0     | Overlap: TTP addressed in controls or assessment         | Yellow #ffcc00 |
| -1    | Covered or tested and not in Joshua's confirmed playbook | Green #66cc66  |

Score expression for gap analysis layer: Layer A (Joshua Persona) MINUS Layer B (Controls Coverage) Where A = Joshua Persona Layer Where B = Control Registry Coverage Layer

------

### WOPR Output Instructions

When generating a Navigator JSON layer:

1. Always use ATT&CK version 18 and layer format 4.5
2. Include techniqueID and tactic for every entry
3. Add a Falken Holdings-specific comment on EVERY technique
4. Reference crown jewels and data classification in comments
5. Include both parent techniques and key subtechniques
6. Output clean valid JSON only with no markdown fences
7. Validate all techniqueIDs match ATT&CK format before output
8. The JSON must be uploadable to Navigator with zero errors
