# WOPR: War Operation Plan Response
### Supporting Resource for *WarGames for Defenders: Playing Threats with MITRE ATT&CK Navigator*
### [CypherCon 2026](https://cyphercon.com)

---

> *"A strange game. The only winning move is to know how it's played."*

---

## Purpose

This repository contains the WOPR context files, prompts, and reference materials demonstrated live at CypherCon 2026 during the talk **WarGames for Defenders: Playing Threats with MITRE ATT&CK Navigator**.

WOPR (War Operation Plan Response) is an AI-assisted threat intelligence engine built as a Claude Project. It takes organizational context as input and produces threat personas, ATT&CK Navigator layers, D3FEND gap analyses, and security program outputs calibrated to a specific client environment.

Everything in this repository is designed to be adapted for your own organization. The Falken Holdings files are fictional demo files. Replace them with your own context and the workflow remains identical.

---

## The Big Idea

> **Build your Joshua before Joshua builds you.**

Once you have a threat persona grounded in real adversary behavior, every security program decision has a north star:

- Which vulnerabilities actually matter?
- What belongs in the risk register?
- What should the pentest team test next?
- What scenario should the tabletop exercise rehearse?
- What do you show the board?

Joshua answers all of it.

---

## Repository Contents

```
WOPR/
│
├── README.md                                  ← You are here
├── WOPR_CLAUDE_PROJECT_INSTRUCTIONS.md        ← Claude Project setup instructions
│
├── prompts/
│   ├── PROMPT_01_BUILD_JOSHUA.md              ← Persona builder prompt
│   ├── PROMPT_02_NAVIGATOR_JSON.md            ← ATT&CK Navigator JSON generator prompt
│   └── PROMPT_03_D3FEND_MITIGATIONS.md        ← D3FEND gap analysis prompt
│
└── context_files/
    ├── 01_FALKEN_HOLDINGS_COMPANY_PROFILE.md
    ├── 02_FALKEN_HOLDINGS_DATA_CLASSIFICATION_REGISTER.md
    ├── 03_FALKEN_HOLDINGS_THREAT_INTEL_SOURCES.md
    ├── 04_ATTACK_NAVIGATOR_JSON_SPECIFICATION.md
    ├── 05_FALKEN_HOLDINGS_D3FEND_PREFERENCES.md
    └── 06_FALKEN_HOLDINGS_CONTROL_REGISTRY.md
```

---

## The WOPR Setup

**WOPR** is built as a **Claude Project**, a persistent AI workspace loaded with organizational context files that allow the AI to produce threat-informed outputs calibrated to a specific client environment.

### How to Build Your Own WOPR

**Step 1: Create a Claude Project**
- Go to claude.ai
- Create a new Project
- Name it: `WOPR [Client Name]`

**Step 2: Add the Project Instructions**
- Open the Project settings
- Copy the full contents of `WOPR_CLAUDE_PROJECT_INSTRUCTIONS.md`
- Paste into the Project Instructions field
- Save

**Step 3: Load the Context Files**
Upload the following files to the Project knowledge base:
1. Company Profile
2. Data Classification Register
3. Threat Intelligence Sources
4. ATT&CK Navigator JSON Specification
5. D3FEND Preferences & Maturity Profile
6. Control Registry *(if available, this triggers Gap Analysis mode)*

**Step 4: Run the Three Prompts in Sequence**

| Prompt | Output |
|---|---|
| PROMPT_01: Build Joshua | Threat Persona Profile (Technical + Executive) |
| PROMPT_02: Generate JSON | ATT&CK Navigator Layer File (.json) |
| PROMPT_03: D3FEND Mitigations | Gap Analysis Mitigation Plan + Program Health Heat Map |

**Step 5: Upload JSON to ATT&CK Navigator**
- Navigate to https://mitre-attack.github.io/attack-navigator
- Select Open Existing Layer and choose Upload from Local
- Upload the JSON file from Prompt 2
- Run the gap analysis subtract function against your controls coverage layer

---

## The Falken Holdings Demo Environment

The fictional client used in this talk is **Falken Holdings**, a mid-market financial holding company with portfolio companies in property development, manufacturing, and professional services.

Falken Holdings is a composite persona designed to represent the realistic security posture of a mid-market organization with:
- A recently acquired manufacturing subsidiary not yet integrated into the security program
- Significant crown jewel data spread across hybrid infrastructure
- A security program at maturity level 2 (Developing): real effort, real gaps
- Zero coverage in the Monitoring & IR domain

> **Important:** Falken Holdings is entirely fictional. Any resemblance to real organizations is coincidental. All context files contain fabricated data for demonstration purposes only.

---

## Joshua: The Threat Persona

**Joshua** is the adversary profile built live during this talk. Named after the AI from the 1983 film *WarGames*, Joshua represents a financially motivated ransomware affiliate and initial access broker with confirmed TTPs targeting mid-market US holding companies in manufacturing, professional services, and property development.

Joshua's confirmed TTPs include:
- **Initial Access:** Phishing (T1566), Valid Accounts (T1078), External Remote Services (T1133)
- **Credential Access:** OS Credential Dumping (T1003), Brute Force (T1110)
- **Lateral Movement:** Remote Services via RDP (T1021.001)
- **Exfiltration:** Exfiltration to Cloud Storage (T1567)
- **Impact:** Data Encrypted for Impact (T1486), Inhibit System Recovery (T1490)

---

## Joshua Applied to Your Security Program

| Program Area | How Joshua Informs It |
|---|---|
| Vulnerability Management | Joshua picks what gets patched first. KEV and TTP alignment replaces CVSS-only prioritization. |
| Risk Assessment | Joshua is the named threat in every risk register entry, with likelihood grounded in evidence. |
| Policies & Procedures | Joshua exposes the gap between what the policy says and what the control actually enforces. |
| Pentest / Purple / Red Team | Joshua is the scope. Every engagement tests confirmed adversary TTPs against your environment. |
| IR Plan & Tabletop Exercises | Joshua is the scenario. Rehearse his exact attack chain before the real thing happens. |
| Board Reporting | Joshua is the story. One heat map replaces forty pages of CVSS findings. |
| Phishing & Awareness Training | Joshua picks the curriculum. Lure themes are built from confirmed initial access TTPs. |

---

## Your Monday Morning Action

You do not need a budget approval to start.

1. Go to **attack.mitre.org/groups**
2. Search for one confirmed threat group targeting your industry
3. Read their profile
4. Map three of their TTPs to your environment
5. Ask honestly: *do we have coverage?*

That is the beginning of building your Joshua.

---

## Tools Referenced

All tools used in this demonstration are **free and publicly available.**

| Tool | URL | Purpose |
|---|---|---|
| MITRE ATT&CK | https://attack.mitre.org | Adversary TTP knowledge base |
| ATT&CK Navigator | https://mitre-attack.github.io/attack-navigator | Threat visualization and gap analysis |
| MITRE D3FEND | https://d3fend.mitre.org | Defensive countermeasure mapping |
| CISA KEV Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog | Actively exploited vulnerability prioritization |
| Claude (Anthropic) | https://claude.ai | WOPR: AI-assisted threat persona builder |

---

## About the Speaker

**Thomas Freeman**
Director | Ghostscale
vCISO Advisor | Cybersecurity Educator | Leadership Coach

🔗 [ghostscale.com](https://ghostscale.com)
🔗 [kcs.coach](https://kcs.coach)
🔗 [LinkedIn](https://linkedin.com/in/thomasfreeman)

---

## License

The content in this repository is shared for educational purposes.
All MITRE ATT&CK and D3FEND content is used in accordance with MITRE's open licensing terms.
Falken Holdings context files are fictional and may be freely adapted for your own demonstrations.

---

## Acknowledgments

- **MITRE Corporation** for ATT&CK, Navigator, and D3FEND
- **CISA** for the KEV catalog and threat advisories
- **John Badham** for directing *WarGames* in 1983 and accidentally creating the best metaphor for threat-informed defense ever put on film

---

*"The only winning move is to know how it's played."*


*"If you know the enemy and know yourself, you need not fear the result of a hundred battles."*
*— Sun Tzu*

*Build your Joshua before Joshua builds you.*
