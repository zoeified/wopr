# PROMPT 02 — Generate the ATT&CK Navigator JSON Layer
## WOPR | WarGames for Defenders | CypherCon 2026
## https://github.com/zoeified/wopr

---

## Purpose
This prompt instructs WOPR to convert the Joshua threat persona
into a valid ATT&CK Navigator JSON layer file that can be uploaded
directly to the Navigator and visualized as a heat map.

## Prerequisites
The following must be complete before running this prompt:
- PROMPT_01 output (Joshua persona) must exist in the conversation
- Context file 04 — ATT&CK Navigator JSON Specification must be loaded

## How to Use
1. Run PROMPT_01 first in the same conversation
2. Copy the prompt below and paste it as the next message
3. WOPR will output clean JSON — copy the entire JSON block
4. Save as a .json file (e.g. `joshua-falken-holdings.json`)
5. Upload to ATT&CK Navigator:
   - Navigate to https://mitre-attack.github.io/attack-navigator
   - Select Open Existing Layer → Upload from Local
   - Select your saved .json file
6. Your Joshua heat map will appear on the Navigator matrix

---

## THE PROMPT

```
Using the Joshua threat persona you just built and the ATT&CK Navigator
JSON Specification in your context files, generate a complete Navigator
layer JSON file for Falken Holdings.

Requirements:
- Use ATT&CK version 16 and layer format 4.5
- Domain: enterprise-attack
- Include all TTPs identified in the Joshua persona
- Include both parent techniques and relevant subtechniques
- For every technique include:
    - techniqueID in correct format (T#### or T####.###)
    - tactic using correct tactic ID string
    - score (1 for confirmed TTP, 0 for possible but unconfirmed)
    - color (#ff6666 for confirmed TTPs)
    - comment explaining why Joshua uses this technique against
      Falken Holdings specifically — reference our crown jewels
      and data classification register where relevant

Set the layer name to:
"Joshua — Falken Holdings Threat Persona"

Set the description to a one sentence summary of Joshua's
primary motivation and target profile.

Output clean valid JSON only.
No explanation before or after the JSON.
No markdown code fences around the JSON.
The output must be paste-ready into a .json file and
uploadable directly to ATT&CK Navigator without errors.
```

---

## Expected Output

WOPR will produce a single block of clean JSON matching the
ATT&CK Navigator layer format v4.5. The file will include:

- Layer metadata (name, version, domain, description)
- Platform filters matching Falken Holdings environment
- Technique entries for all Joshua TTPs with:
  - Correct ATT&CK technique IDs
  - Correct tactic IDs
  - Red color coding (#ff6666) for confirmed techniques
  - Falken Holdings-specific analyst comments on every technique
- Gradient and legend configuration
- Layout settings optimized for presentation

---

## Gap Analysis — Next Step in Navigator

Once your Joshua layer is uploaded to Navigator, follow these
steps to run the gap analysis:

**Step 1 — Create a Controls Coverage Layer**
- In Navigator, create a new layer
- Manually highlight techniques that your current controls address
- Score covered techniques as 1, partial as 0.5, gaps as 0
- Save this as your controls coverage layer

**Step 2 — Run the Subtract Function**
- Select Create Layer from Other Layers
- Set Score Expression: `a - b`
  Where a = Joshua layer, b = Controls coverage layer
- Set colors: Red for positive scores (gaps), Green for negative (covered)

**Step 3 — Read the Result**
- Red squares = Joshua uses this TTP and you have no coverage
- Yellow squares = Partial coverage
- Green squares = Covered
- These red squares become your priority remediation list

---

## Scoring Convention Reference

| Score | Meaning | Color |
|---|---|---|
| +1 | Joshua uses it — not covered | Red #ff6666 |
| 0 | Overlap — addressed in controls | Yellow #ffcc00 |
| -1 | Covered — not in Joshua's playbook | Green #66cc66 |

---

## Adapting for Your Organization

To use this prompt for a real client engagement:
1. Update the layer name to reflect your client name
2. Ensure PROMPT_01 was run with your client's context files
3. The JSON output will automatically reflect whatever TTPs
   WOPR identified in the persona — no manual editing required
4. Upload the file to a local Navigator instance if your
   client data is sensitive — do not use the public GitHub Pages
   hosted Navigator for client-specific layers

---

## Next Step
Once you have the Navigator heat map visible → proceed to **PROMPT_03**
to generate D3FEND mitigation recommendations against the gap analysis.
