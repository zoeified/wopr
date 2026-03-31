# PROMPT 01 — Build the Joshua Threat Persona
## WOPR | WarGames for Defenders | CypherCon 2026
## https://github.com/zoeified/wopr

---

## Purpose
This prompt instructs WOPR to research current threat intelligence
and build a named threat actor persona for your organization.
The output is used as the foundation for all subsequent WOPR prompts.

## Prerequisites
The following context files must be loaded into your Claude Project
before running this prompt:
- 01 — Company Profile
- 02 — Data Classification Register
- 03 — Threat Intelligence Sources

## How to Use
1. Open your WOPR Claude Project
2. Confirm all prerequisite context files are loaded
3. Copy the prompt below and paste it into the conversation
4. Review the output — both the Technical Brief and Executive Summary
5. Save the output — it becomes the input for PROMPT_02

---

## THE PROMPT

```
Using the context files provided — Company Profile, Data Classification
Register, and Threat Intelligence Sources — research current threats
targeting my organization and build a threat actor persona.

I am the CISO of Falken Holdings.

Research the threat intelligence sources identified in my context file.
Focus on:
- Recent attacks targeting property development, manufacturing,
  and professional services
- Active ransomware groups and APT actors targeting mid-market
  US holding companies
- TTPs commonly used in confirmed attacks against my industries

Based on your research, build a threat actor persona named Joshua.

Include:
- Threat actor type and motivation
- Industries and organization profiles they target
- Why Falken Holdings is an attractive target
- What Joshua is after — reference my Data Classification Register
  for crown jewel mapping
- Preferred initial access techniques
- Full attack chain narrative (step by step)
- Top 10-15 TTPs with ATT&CK technique IDs
- Likely tools and malware families used

Format your response in two sections:

1. TECHNICAL BRIEF — for my security team
   Full detail. Include ATT&CK technique IDs for every TTP.
   Map each TTP to the specific Falken Holdings asset or
   entity most at risk.

2. EXECUTIVE SUMMARY — for leadership and the board
   No jargon. Business impact language only.
   Answer three questions:
   - Who is Joshua?
   - What does Joshua want from us specifically?
   - What happens to us if Joshua succeeds?
```

---

## Expected Output

WOPR will produce a two-section threat persona profile:

**Technical Brief** — A detailed adversary profile including:
- Threat actor classification and motivation
- Industry targeting rationale
- Crown jewel mapping to your data classification register
- Full attack chain narrative with ATT&CK technique IDs
- Tools and malware families associated with this actor type

**Executive Summary** — A board-ready narrative including:
- Plain language description of the adversary
- Business impact framing tied to your specific crown jewels
- Consequence narrative if the attack succeeds

---

## Adapting for Your Organization

To use this prompt for a real client engagement:
1. Replace all Falken Holdings references with your client name
2. Update the industry focus to match your client's verticals
3. Ensure your Company Profile and Data Classification Register
   context files reflect the real client environment
4. The persona name Joshua is fictional — rename as appropriate
   for your engagement context

---

## Next Step
Once you have the Joshua persona output → proceed to **PROMPT_02**
to generate the ATT&CK Navigator JSON layer.
