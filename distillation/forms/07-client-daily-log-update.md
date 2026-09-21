# Form: Client Daily Log Update

## Source
- File: `Client Daily Log Update.txt` (converted from `.docx`)
- Format: txt (static table, no JS/logic)

## Field / Section Inventory (verbatim)
- Client Name
- (CU) Date
- Staff Name
- (CU) Shift: ☐ AM ☐ PM ☐ Overnight
- Details of Shift
- (CU) General Overview
- (CU) Health Information
- (CU) Community or In-House Programming
- (CU) Cultural-Based Activities
- Hygiene During Shift
- Incidents and/or Follow Through
- (CU) Follow Through (notes)
- (CU) Completed Hygiene Routines: ☐ Bathing/Showering ☐ Brushed Teeth ☐ Flossed Teeth ☐ Hair - Brushed or Combed ☐ Hair - Washed ☐ Shaving ☐ Other: ___
- (CU) Cross Reference Information: ☐ Contact Note ☐ Noteworthy Event ☐ Critical Incident ☐ Follow Through

## Computed / Derived Fields & Formulas
None.

## Structural Issues Found
- **Six of the fourteen fields carry an unexplained "(CU)" prefix**: (CU) Date, (CU) Shift, (CU) General Overview, (CU) Health Information, (CU) Community or In-House Programming, (CU) Cultural-Based Activities, (CU) Follow Through (notes), (CU) Completed Hygiene Routines, (CU) Cross Reference Information — nine occurrences total, not applied consistently even within this one form (e.g. "Client Name," "Staff Name," "Details of Shift," "Hygiene During Shift," "Incidents and/or Follow Through" have no prefix while closely related fields do).
- "Hygiene During Shift" (unprefixed, free text) and "(CU) Completed Hygiene Routines" (prefixed, checkbox list) are two separate fields covering the same topic with no stated relationship between them.
- "Incidents and/or Follow Through" (unprefixed, free text) and "(CU) Follow Through (notes)" (prefixed, free text) likewise appear to duplicate each other with no distinction given in the form.
- "(CU) Cross Reference Information" checklist (Contact Note / Noteworthy Event / Critical Incident / Follow Through) is a flag list with no linked-record field — it indicates a cross-reference exists but not which specific record.

## Discovery-Doc Open-Issue Cross-Check
> "The '(CU)' prefix on Daily Log fields is unexplained. This means needs to be defined so it can be correctly labelled in the portal."
**CONFIRMED.** No definition, legend, or footnote for "(CU)" appears anywhere in the file. (The discovery doc's own answer resolves this as "Client Update" and recommends dropping the abbreviation entirely — that resolution is not verifiable against this source file, since the file itself gives zero explanation.)

## Cross-References
- "(CU) Cross Reference Information" options overlap heavily with Client Noteworthy Update's "Cross Reference" checklist (Daily Log / Contact Note / Critical Incident Report / Medication Log / Discharge Summary / Other) — the two forms use different option sets for what appears to be the same cross-referencing concept.

## Notes
This form has the highest prefix-inconsistency of any in the set and the most internal field duplication (Hygiene During Shift vs. Completed Hygiene Routines; Incidents/Follow Through vs. Follow Through notes).
