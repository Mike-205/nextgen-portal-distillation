# Form: Client Noteworthy Update

## Source
- File: `Client Noteworthy Update.txt` (converted from `.docx`)
- Format: txt (static table, no JS/logic)

## Field / Section Inventory (verbatim)
**Client Information**
- Client Name
- Client ID / File Number
- Date of Update
- Time of Update (From ___ To ___)
- Staff Name
- Program / Unit

**Type of Noteworthy Update** (checkbox list):
☐ Significant Progress ☐ Critical Insight or Disclosure ☐ Unusual Behavior ☐ Positive Milestone ☐ Emotional or Behavioral Shift ☐ Change in Routine or Engagement ☐ Safety-Related Concern (Non-Critical) ☐ Other: ___

- Description of the Event / Observation ("Include facts only – what was observed, heard, or disclosed. Use neutral, descriptive language.")
- Context or Circumstances Surrounding the Update
- Client's Response / Emotional State
- Immediate Actions Taken by Staff (if applicable)

**Follow-Up Needed** (checkbox list):
☐ Internal Team Follow-Up ☐ Clinical / Mental Health Check-In ☐ Family / Guardian Contact ☐ Safety Planning ☐ No Follow-Up Required ☐ Other: ___
- "Describe next steps (who will do what, when):" free text

**Cross Reference (if applicable)** (checkbox list):
☐ Daily Log ☐ Contact Note ☐ Critical Incident Report ☐ Medication Log ☐ Discharge Summary ☐ Other: ___

- Staff Signature / Date

## Computed / Derived Fields & Formulas
None.

## Structural Issues Found
- The title says "Client **Noteworthy Update**" but the "Type of Noteworthy Update" checklist item reading "Safety-Related Concern (Non-Critical)" is the only field on the entire form that gestures at the noteworthy-vs-incident boundary — there is no decision rule, threshold, or link to a Critical Incident Report anywhere in the fields themselves (the "Cross Reference" checklist includes "Critical Incident Report" as an option, meaning the form assumes a separate incident record may already exist, but provides no mechanism to create one from here).

## Discovery-Doc Open-Issue Cross-Check
> "The Noteworthy Update to Incident Report escalation path is undefined. A clear decision rule needs to be written before either form is built into the portal."
**CONFIRMED.** The form contains no escalation logic, no threshold, and no automatic linkage — only a passive "Critical Incident Report" checkbox in the Cross Reference list, consistent with the discovery doc's claim.

## Cross-References
- "Cross Reference" checklist (Daily Log / Contact Note / Critical Incident Report / Medication Log / Discharge Summary / Other) overlaps with, but does not match, Client Daily Log Update's "(CU) Cross Reference Information" checklist (Contact Note / Noteworthy Event / Critical Incident / Follow Through) — different option sets for what both forms call "cross reference."
- "Program / Unit" here vs. "Program / Service Area" on Case Note and "Program" elsewhere — a third variant term for the same concept.

## Notes
No "Discharge Summary" form or field exists anywhere else in this 19-file set, despite being listed as a cross-reference option here — the discovery doc separately confirms a Discharge Form/Checklist exists as agency process (Q5) but no such form file was provided in this set.
