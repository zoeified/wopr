# Falken Holdings — Threat Intelligence Sources
## WOPR Context File v1.0 | Last Updated: Q1 2026
## Classification: CONFIDENTIAL — WOPR USE ONLY

---

### Purpose
This file tells WOPR where to research current threat
intelligence relevant to Falken Holdings. When building
or updating the Joshua persona, WOPR must actively
research these sources to identify recent attacks
targeting our industries, who the threat actors were,
and what TTPs were commonly used in confirmed attacks.

---

### Priority Industries to Research
When searching for threat intelligence, focus on
attacks targeting these industries — in this order:

1. Financial holding companies and private equity
2. Manufacturing — mid-market, US-based, precision/industrial
3. Professional services — HR, staffing, consulting
4. Commercial property development and real estate
5. Managed service providers (supply chain attack vector)

---

### Tier 1 — Primary Threat Intelligence Sources
*Search these first. Highest signal-to-noise ratio.
Government and authoritative sources only.*

| Source | URL | What WOPR Should Look For |
|---|---|---|
| CISA Cybersecurity Advisories | https://www.cisa.gov/news-events/cybersecurity-advisories | Active threat alerts, industry-specific warnings, ransomware advisories |
| CISA Known Exploited Vulnerabilities Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog | CVEs actively exploited in the wild — cross-reference against our stack |
| MITRE ATT&CK Threat Groups | https://attack.mitre.org/groups/ | Named threat actor profiles with confirmed TTP mappings |
| MITRE ATT&CK Software | https://attack.mitre.org/software/ | Malware and tool profiles used by threat actors targeting our industries |
| FBI Flash Reports and Alerts | https://www.ic3.gov/Media/News/Alerts | Active ransomware campaigns, BEC alerts, industry-specific warnings |
| MS-ISAC Security Advisories | https://www.cisecurity.org/ms-isac | Alerts relevant to mid-market organizations |
| HHS HC3 Threat Reports | https://www.hhs.gov/sites/default/files/analyst-note-rhysida-ransomware | Reference for ransomware groups targeting US businesses |

---

### Tier 2 — Vendor Threat Research
*Deep technical reporting with confirmed TTP detail.
Use for enriching threat actor profiles with specific
techniques, tools, and attack chain details.*

| Source | URL | What WOPR Should Look For |
|---|---|---|
| CrowdStrike Adversary Intelligence | https://www.crowdstrike.com/blog/category/threat-intelligence/ | Named adversary profiles, eCrime group tracking, ransomware TTPs |
| Palo Alto Unit 42 | https://unit42.paloaltonetworks.com/ | Ransomware group deep-dives, incident investigation reports, IoCs |
| Cisco Talos Intelligence | https://blog.talosintelligence.com/ | Malware analysis, active campaign tracking, phishing kit analysis |
| IBM X-Force Threat Intelligence | https://securityintelligence.com/x-force/ | Annual threat index, industry vertical reports, dark web intelligence |
| Google Mandiant Threat Intelligence | https://cloud.google.com/blog/topics/threat-intelligence | APT group tracking, sophisticated actor TTPs, M-Trends report |
| Secureworks Threat Profiles | https://www.secureworks.com/research/threat-profiles | GOLD, BRONZE, IRON named threat group profiles mapped to ATT&CK |
| Microsoft MSRC Security Updates | https://msrc.microsoft.com/update-guide/ | Actively exploited Microsoft vulnerabilities — critical for our M365 environment |
| Recorded Future Threat Intelligence | https://www.recordedfuture.com/research | Manufacturing and financial sector threat reporting |

---

### Tier 3 — News and Breaking Incident Coverage
*Use for breaking news intake and industry context.
Verify all TTPs against Tier 1 or Tier 2 sources
before adding to Joshua persona.*

| Source | URL | What WOPR Should Look For |
|---|---|---|
| Krebs on Security | https://krebsonsecurity.com/ | Breaking breach investigations, threat actor exposure, ransomware negotiations |
| DataBreachToday | https://www.databreachtoday.com/ | Incident reporting with regulatory and legal implications |
| The Record by Recorded Future | https://therecord.media/ | Ransomware group tracking, geopolitical threat context, US sector targeting |
| BleepingComputer | https://www.bleepingcomputer.com/ | Ransomware group activity, malware campaigns, victim disclosures |
| Dark Reading | https://www.darkreading.com/ | Manufacturing, financial, and professional services threat coverage |
| SC Magazine | https://www.scmagazine.com/ | Mid-market breach reporting, SMB-relevant threat context |

---

### Known Threat Actors Relevant to Falken Holdings
*Pre-research summary — use as starting point for
Joshua persona construction. Always verify against
current MITRE ATT&CK group profiles and Tier 1 sources.*

| Threat Actor | Type | Primary Targeting | Relevance to Falken | Key TTPs |
|---|---|---|---|---|
| LockBit 3.0 / LockBit 4.0 | Ransomware-as-a-Service | Manufacturing, professional services, financial | HIGH — active targeting of mid-market US manufacturers | T1566, T1078, T1486, T1490, T1027 |
| BlackCat / ALPHV | Ransomware-as-a-Service | Manufacturing, financial, healthcare | HIGH — known for double extortion targeting IP-rich firms | T1566, T1133, T1486, T1567, T1041 |
| Medusa Ransomware Group | Ransomware-as-a-Service | Education, manufacturing, professional services | MEDIUM-HIGH — growing US mid-market targeting | T1566, T1078, T1486, T1489 |
| Scattered Spider | Cybercriminal group | Financial services, BPO, staffing | HIGH for SPS — social engineering and SIM swapping | T1566, T1598, T1199, T1078.004 |
| TA505 | Financially motivated APT | Financial, manufacturing, staffing | HIGH — long history of targeting staffing and HR firms | T1566.001, T1204, T1055, T1041 |
| Lazarus Group (DPRK) | Nation-state | Financial institutions, manufacturing | MEDIUM — M&A intelligence and financial theft motivation | T1566, T1195, T1057, T1041 |
| Initial Access Brokers (various) | Criminal ecosystem | All industries — selling access | HIGH — RMI VPN and legacy systems are attractive targets | T1078, T1133, T1190 |

---

### Breaking News Intake Protocol
*When a new breach hits the news, WOPR follows
these steps before updating the Joshua persona:*

**STEP 1 — VICTIM PROFILE MATCH**
Identify the victim's industry, size, and technology
environment. Score similarity to Falken Holdings:
- Same industry vertical as FH, RMI, SPS, or FPG?
- Similar employee count (under 1,000)?
- Similar technology environment (Microsoft 365, hybrid)?
- US-based mid-market organization?

If 2 or more match — treat as HIGH RELEVANCE.
Update Joshua persona with confirmed TTPs.

**STEP 2 — THREAT ACTOR IDENTIFICATION**
- Is this a named group from the Known Threat Actors
  table above?
- Cross-reference against MITRE ATT&CK Groups page
- Check CrowdStrike and Mandiant for actor profile updates
- If unnamed — identify ransomware variant and
  search for associated TTP patterns

**STEP 3 — TTP EXTRACTION**
- Extract every confirmed attack step from the
  incident report or news coverage
- Map each step to an ATT&CK Technique ID
- Note which techniques are NEW vs. already
  in the Joshua persona
- Verify new techniques against MITRE ATT&CK
  before adding to persona

**STEP 4 — JOSHUA PERSONA UPDATE**
- Add newly confirmed TTPs to Joshua persona
- Flag each new TTP as BREAKING NEWS — [Date]
- Note the source organization (anonymized if needed)
- Generate updated Navigator JSON layer with
  new TTPs highlighted in a distinct color

**STEP 5 — FALKEN HOLDINGS EXPOSURE BRIEF**
Generate a short brief answering three questions:
1. If this attack happened to us today —
   where would we be exposed?
2. Which of our crown jewels would be at risk?
3. What is our current control coverage
   against the confirmed TTPs?

**STEP 6 — EXECUTIVE NOTIFICATION**
Generate a one-paragraph board-ready summary:
- What happened to the victim (no name if sensitive)
- Why it is relevant to Falken Holdings
- Where we stand today
- What we are doing about it

---

### Intelligence Quality Standards
*WOPR must apply these standards to all
threat intelligence before using it:*

| Standard | Rule |
|---|---|
| Freshness | Intelligence older than 90 days is background context only — not active intelligence |
| Source Tier | Always prefer Tier 1 over Tier 2 over Tier 3 |
| Corroboration | Weight TTPs higher when confirmed by 2+ independent sources |
| ATT&CK Validation | All TTPs must map to a valid ATT&CK Technique ID before inclusion |
| Distinction | Always separate CONFIRMED TTPs from INFERRED TTPs in all outputs |
| KEV Cross-Reference | Any CVE mentioned must be checked against CISA KEV catalog |
| Actor Attribution | Note confidence level — HIGH / MEDIUM / LOW — for all actor attribution |
