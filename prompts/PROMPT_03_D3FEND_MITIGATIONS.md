# PROMPT 03 — D3FEND Mitigation Recommendations
## WOPR | WarGames for Defenders | CypherCon 2026
## https://github.com/zoeified/wopr

---

## Purpose
This prompt instructs WOPR to generate D3FEND-mapped mitigation
recommendations against Joshua's confirmed TTPs. If a Control Registry
is loaded, WOPR runs a gap analysis and recommends only what is missing
or insufficient. If no Control Registry is present, WOPR produces a
best practice mitigation plan calibrated to your maturity level.

## Prerequisites
The following must be complete before running this prompt:
- PROMPT_01 output (Joshua persona) must exist in the conversation
- PROMPT_02 gap analysis results (red squares) must be identified
- Context file 05 — D3FEND Preferences & Maturity Profile must be loaded
- Context file 06 — Control Registry (optional — triggers Gap Analysis mode)

## How to Use
1. Complete PROMPT_01 and PROMPT_02 in the same conversation
2. Identify the red squares from your Navigator gap analysis
3. Copy the prompt below and paste it as the next message
4. Review both the Technical and Executive output versions
5. Use the Program Health Heat Map as your board slide

---

## THE PROMPT

```
Using the Joshua threat persona, the Navigator gap analysis results,
and the context files provided, generate a D3FEND mitigation
recommendation report for Falken Holdings.

---

STEP 1 — CHECK FOR CONTROL REGISTRY

If a Control Registry file exists in the context folder:
- Run in MODE B — Gap Analysis Mitigation Plan
- Cross-reference every Joshua TTP against existing controls
  in the registry
- Treat PARTIAL controls as 50% effective
- Treat GAP controls aligned to Joshua TTPs as critical priority
- Flag the following immediately regardless of TTP mapping:
    - Any domain with zero COVERED controls
    - Any backup not tested in over 12 months
    - Any penetration test overdue beyond 12 months
    - Any IR plan not tested in over 2 years
- Recommend only what is missing or insufficient
  Do not recommend controls already marked COVERED

If no Control Registry file exists in the context folder:
- Run in MODE A — Best Practice Mitigation Plan
- Recommend full D3FEND countermeasure set
- Calibrate recommendations to maturity level defined
  in the D3FEND Preferences file
- Assume starting from baseline

---

STEP 2 — APPLY D3FEND PREFERENCES

Before generating any recommendations, read the D3FEND Preferences
and Maturity Profile and apply the following:

- Never recommend controls beyond current maturity level plus one
- Map every recommendation to our primary control framework
- Flag any recommendation that satisfies both a Joshua TTP gap
  AND a compliance or insurance requirement
  Label these: DUAL WIN
- Prefer existing technology stack over new tooling
- Apply budget posture to all new tool recommendations
  Label cost tier clearly:
    LOW: Under $10K annually
    MEDIUM: $10K-$50K annually
    HIGH: Over $50K annually

---

STEP 3 — FOR EACH UNMITIGATED TTP

1. STATE THE THREAT
   - ATT&CK Technique ID and name
   - How Joshua uses this against Falken Holdings specifically
   - Which crown jewel assets are at risk
   - Which entity carries the highest exposure (FH / RMI / FPG / SPS)

2. MAP TO D3FEND and NIST CSF
   Provide countermeasures across relevant tactical categories:
   - MODEL: What must we understand or inventory first?
   - HARDEN: How do we reduce attack surface?
   - DETECT: What do we monitor and alert on?
   - ISOLATE: How do we contain the threat?
   - EVICT: How do we remove the threat?
   - RESTORE: How do we recover?

3. PRIORITIZE EACH COUNTERMEASURE
   - IMMEDIATE: Within 30 days
   - SHORT TERM: 30-90 days
   - STRATEGIC: 90+ days

4. CONNECT TO THE SECURITY PROGRAM
   For each countermeasure identify which program element it informs:
   - Control Register update
   - Policy or Plan update
   - IR Plan playbook addition
   - Tabletop exercise scenario
   - Awareness training topic
   - Board reporting metric

---

STEP 4 — FORMAT OUTPUT

Produce two versions of all recommendations:

TECHNICAL VERSION
Full countermeasure detail for the security team.
Include D3FEND technique IDs, framework control mappings,
and implementation guidance.

EXECUTIVE VERSION
One paragraph per TTP cluster. Business risk language only.
No jargon. Answer three questions for every cluster:
- What could Joshua do to us?
- What are we missing?
- What will it cost to fix it?

---

STEP 5 — PROGRAM HEALTH SUMMARY

Close with two outputs:

1. PRIORITY ACTION LIST
   Top 10 immediate actions ranked by:
   - Joshua TTP alignment
   - Crown jewel exposure
   - Compliance or insurance impact Including (NIST CSF)
   - Implementation effort

2. PROGRAM HEALTH HEAT MAP
   A table with Joshua's top TTPs across the left column
   and our security program areas across the top row:

   Program Areas:
   Risk Register | Asset Classification | Control Register |
   Policies & Plans | IR Plan | Tabletop | Vuln Management |
   Awareness Training | Board Reporting

   Mark each cell:
   COVERED — Control in place and validated
   PARTIAL — Control exists but insufficient
   GAP — No control in place
   DUAL WIN — Closes Joshua gap AND compliance requirement

   This heat map is the board slide.
   Format it so it can be read in 30 seconds.
```

---

## Expected Output

WOPR will produce the following in a single response:

**MODE B (Gap Analysis) or MODE A (Best Practice)**
- Per-TTP threat statement tied to Falken Holdings crown jewels
- D3FEND countermeasures across all relevant tactical categories
- Priority rating for each countermeasure (Immediate / Short Term / Strategic)
- Program area connection for each recommendation
- DUAL WIN flags for controls that satisfy multiple objectives
- Cost tier labels for any new tooling recommendations

**Technical Version** — Full detail for the security team

**Executive Version** — Board-ready business language

**Priority Action List** — Top 10 ranked immediate actions

**Program Health Heat Map** — The board slide

---

## Understanding the Output Modes

| Mode | When It Runs | What It Produces |
|---|---|---|
| MODE A | No Control Registry in context | Full best practice mitigation plan from baseline |
| MODE B | Control Registry present in context | Gap analysis — recommends only what is missing |

Mode B is the more powerful output for an active engagement.
Mode A is useful for prospect conversations or early assessments
where no control inventory exists yet.

---

## Using the Program Health Heat Map

The Program Health Heat Map is designed to be your board slide.
It answers the question every executive is actually asking:

*"Where are we exposed and what are we doing about it?"*

Export the table from WOPR and present it alongside the
ATT&CK Navigator heat map from PROMPT_02. Together they tell
a complete story:

- Navigator heat map = Here is what Joshua is going to do
- Program Health Heat Map = Here is where we stand against it
- Priority Action List = Here is what we are doing about it

---

## Adapting for Your Organization

To use this prompt for a real client engagement:
1. Replace all Falken Holdings references with your client name
2. Ensure your client's Control Registry is loaded if available
3. Update the D3FEND Preferences file to reflect your client's
   actual maturity level, framework, and technology stack
4. The DUAL WIN flag is particularly valuable for clients with
   active compliance obligations — highlight these in every output

---

## The Complete WOPR Workflow

| Step | Prompt | Output |
|---|---|---|
| 1 | PROMPT_01 — Build Joshua | Threat Persona Profile |
| 2 | PROMPT_02 — Generate JSON | ATT&CK Navigator Layer File |
| 3 | Upload to Navigator | Visual Heat Map |
| 4 | Run Gap Analysis | Red Square Exposure Map |
| 5 | PROMPT_03 — D3FEND | Mitigation Plan + Program Health Heat Map |
