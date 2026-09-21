# Form: Incident Report Requirements

## Source
- File: `incident-report.txt` (already plain text, not converted from docx)
- Format: txt

## Field / Section Inventory (verbatim)
**General Reporting Rule** (prose, not fields):
- "When to Notify: Children and Family Services (CFS) must be notified within 24 hours of any incidents."
- "Serious Incidents: When an incident meets the threshold of a 'serious incident,' CFS must be notified immediately."

**Section 1: Child or Youth's Information**
- Name: Last Name of Child or Youth, First Name
- Identifying Data: Date of Birth (yyyy-mm-dd), Child's I.D. Number
- Case Management: Child Intervention Practitioner (CIP), CIP Office
- CFS Status (check all that apply): ☐ CAG ☐ TGO ☐ CAY ☐ PGO ☐ ICO ☐ SFP

**Section 2: Facility Information**
- Agency/Caregiver Identification: Name of Agency/Program/Foster Caregivers/Kinship Caregivers, License #/Caregiver ID (if applicable)
- Type of Facility (check all that apply): ☐ Foster Care ☐ Kinship Care ☐ ILS/SIL/TSIL ☐ Community Group Care ☐ Agency Campus-based Treatment Centre ☐ Ministry Campus-based Treatment Centre ☐ Personalized Community Care ☐ Secure Services/PSECA Confinement ☐ PSECA (Voluntary) ☐ 'Other' (must specify)
- Location Details: Facility/Caregiver Address, City or Town, Province (pre-filled AB), Postal Code

**File ends here — no Section 3 onward.**

## Computed / Derived Fields & Formulas
None.

## Structural Issues Found
- **File terminates immediately after Section 2's Postal Code field.** No "what happened" narrative field, no date/time of incident, no witnesses, no actions taken, no notifications-made log, no signature/sign-off block exists anywhere in the file — this is the only form in the set with no description-of-event field at all.
- CFS Status codes (CAG, TGO, CAY, PGO, ICO, SFP) are given as bare acronyms with no legend/definition in the file.
- "Type of Facility" list mixes program-model categories (Foster Care, Kinship Care) with security/legal categories (Secure Services/PSECA Confinement) with no grouping.

## Discovery-Doc Open-Issue Cross-Check
> "The Incident Report appears to be incomplete. Sections 3 onwards (what happened, who was notified, timestamps) do not exist. This needs to be completed before the portal is built."
**CONFIRMED**, exactly as described — the file has only Section 1 (Child/Youth Info) and Section 2 (Facility Info); there is no Section 3 or beyond in the source file.

## Cross-References
- CFS Status codes (CAG/TGO/CAY/PGO/ICO/SFP) and Facility Type list match the schema's `INCIDENT_REPORT_CFS_STATUS` and `INCIDENT_REPORT_FACILITY_TYPE` enums in `next_gen_services/prisma/schema.prisma` — confirming the prior dev pass copied exactly what exists in this file (Sections 1–2 only) and therefore inherited the same incompleteness; the schema's `IncidentReport` model has no "what happened" narrative field either.
- The discovery doc resolves this by proposing the portal capture Sections 1–2 internally and let staff **attach the official Government of Alberta Incident Report form** as a file upload for the narrative/what-happened content, plus a separate, fully-digital "Staff Incident Report" module using a template "to be provided separately" — that template was not among the 19 files in this set.

## Notes
This is the form most directly tied to mandatory external reporting (CFS, 24-hour/immediate notification) and it is also the most structurally incomplete file in the entire set.
