# Form: FAMILY LIVING PROGRAM – HEALING PLAN

## Source
- File: `Healing Plan.txt` (converted from `.docx`)
- Format: txt (static table, no JS/logic)

## Field / Section Inventory (verbatim)
**Header**
- Client Full Name
- Date of Birth
- Date of Healing Plan
- Case Worker Name
- Authoring Staff Name
- Plan Type: ☐ Initial / Assessment ☐ Progress / Interim

**HEALING GOALS – BASED ON THE MEDICINE WHEEL** — four goal blocks, each with an identical structure (Area Addressed checkboxes, Program Tasks 1–3, Client Narrative/Engagement Summary, Indicators of Success, Observed Progress, Goal Attainment Rating 1–5):

1. **GOAL ONE: SPIRITUAL WELLBEING** — Area Addressed: ☐ Spiritual ☐ Identity ☐ Belonging ☐ Cultural Connection
2. **GOAL TWO: MENTAL WELLBEING** — Area Addressed: ☐ Mental Health ☐ Cognitive Functioning ☐ Substance Use
3. **GOAL THREE: EMOTIONAL WELLBEING** — Area Addressed: ☐ Emotional Regulation ☐ Relationships ☐ Trauma Response
4. **GOAL FOUR: PHYSICAL WELLBEING** — Area Addressed: ☐ Physical Health ☐ Medication ☐ Routines

**SUMMARY SECTIONS**
- Client Summary
- Cultural / Religious / Spiritual (2–4 paragraphs)
- External Services (list supports: therapist, doctors, addiction counselors, etc.)
- Relationships / Connections (2–4 paragraphs)
- Summary & Recommendations

## Computed / Derived Fields & Formulas
None. "Goal Attainment Rating (1–5)" is a plain numeric field with no formula, scale definition, or aggregation shown in the form.

## Structural Issues Found
- **The template defines FOUR Medicine Wheel goal areas — Spiritual, Mental, Emotional, and Physical Wellbeing** — each with its own full set of sub-fields (Area Addressed, 3 Program Tasks, Narrative, Indicators, Progress, Rating).
- No version number, review date, or "next review" field exists anywhere on the form, despite the discovery doc stating the Healing Plan must be reviewed every 3 months.
- No signature/approval block at all — unlike almost every other clinical/safety form in this set (Intake Screening, Needs Assessment, Emergency Preparedness Plan all have sign-off sections; this one, arguably the most clinically significant document, does not).
- "Goal Attainment Rating (1–5)" scale is undefined (no legend for what 1 vs. 5 means) on all four goals.

## Discovery-Doc Open-Issue Cross-Check
> "The Healing Plan has no version control or review date. The review cycle needs to be defined before building."
**CONFIRMED.** No version, review date, or next-review field exists anywhere in the source form.

No other Open-Issue item explicitly names the Healing Plan, but note: **the discovery doc's own text, when describing the Healing Plan, only ever mentions three wellbeing areas** ("Spiritual Wellbeing," "Mental Wellbeing," "Physical Wellbeing" — see `NextGen_Portal_Discovery.txt` Q1/Q5 area descriptions) and the previously-built schema (`next_gen_services/prisma/schema.prisma`) likewise only implements `HEALING_PLAN_SPIRITUAL_WELLBEING_AREA_ADDRESSED`, `HEALING_PLAN_MENTAL_WELLBEING_AREA_ADDRESSED`, and `HEALING_PLAN_PHYSICAL_WELLBEING_AREA_ADDRESSED` enums — **no Emotional Wellbeing enum or fields exist in that schema at all.** This is a genuine, previously-undetected gap: the fourth Medicine Wheel goal area (Emotional Wellbeing) present in the original form was silently dropped somewhere between the source form and the first digitization pass. This is not an Open Issue the discovery doc flagged — it's a new finding.

## Cross-References
- "Case Worker Name" and "Authoring Staff Name" are two distinct staff fields — the discovery doc's answer to Q2 also distinguishes "Program Manager/Supervisor" (primary responsibility) from a general worker role, which may map to these two fields, but the form itself gives no definition of the difference.
- "External Services" (therapist, doctors, addiction counselors) overlaps with Client Information's "Primary Care Physician" and "Primary Clinician" fields — no cross-link exists in either document.

## Notes
This is the highest-value finding in the audit so far: a whole clinical domain (Emotional Wellbeing) that exists in the org's actual paper form but is completely absent from the system that was already built. Flag for the entity model / per-form spec and for the open-questions register — this needs to go back to the client as a confirmed gap, not a "maybe."
