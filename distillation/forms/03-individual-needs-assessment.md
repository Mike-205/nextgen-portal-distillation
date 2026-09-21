# Form: Individual Needs Assessment Form

## Source
- File: `Individual Needs Assessment Form.txt` (converted from `.docx`)
- Format: txt (static table, no JS/logic)

## Field / Section Inventory (verbatim)
**Assessment Information**
- Client Name
- Client ID/File Number
- Enrollment Begin Date **(pre-filled: "07/03/2025")**
- Staff Name (Completing Assessment)
- Date Completed

**A. Risk Factors** — 13 items, each rated: ☐ Never ☐ No – Not at Present ☐ Occasionally ☐ Sometimes ☐ Always ☐ Constant/Severe
1. Are behavioral issues a concern?
2. Is overall safety a concern?
3. Is substance abuse or misuse a concern?
4. Are diagnosed mental health issues a concern?
5. Do health issues (not including mental health) create concern?
6. Is risk of self-harm a concern?
7. Is risk of suicide a concern?
8. Is emotional wellness a concern?
9. Is a formal assessment (educational, psychiatric, etc.) required?
10. Is problem solving a concern?
11. Is involvement in criminal activity a concern?
12. Is abuse and/or exposure to abuse a factor?
13. Are meeting developmental milestones a concern?

**B. Personal Functioning** — 9 items (14–22), same 6-point rating scale:
14. Effective communication concern
15. Emotional regulation concern
16. Daily living skills concern
17. Appropriate peer relationships/skills concern
18. Self-identity (cultural, religious, gender) concern
19. Development of education or employment skills concern
20. Budgeting concern
21. Motivation/readiness/desire to change concern
22. Finding appropriate placement upon discharge concern

**C. Connection to Community** — 4 items (23–26), same scale:
23. Social awareness/social skills development concern
24. Cultural/spiritual/religious connection concern
25. Awareness of community supports/resources concern
26. Involvement in community-based activities required

**D. Relationship with Family and/or Significant Person** — 5 items (27–31), same scale:
27. Parent-child or family conflict concern
28. Grief, separation and/or loss concern
29. Parenting skills concern
30. Attachment to family or significant person concern
31. Reunification with family an area requiring attention

**Closing:** Additional Notes / Summary of Needs (free text), Staff Signature, Date

## Computed / Derived Fields & Formulas
None — no scoring, weighting, or aggregate risk score is calculated from the 31 ratings anywhere in the file.

## Structural Issues Found
- **"Enrollment Begin Date: 07/03/2025" is a hardcoded, filled-in value inside what is otherwise a blank template.** Either leftover sample/test data never cleared, or the template author's real enrollment date accidentally left in — either way it should not be treated as a real default.
- The 31 items use an identical 6-point scale ("Never / No – Not at Present / Occasionally / Sometimes / Always / Constant/Severe") worded as a *risk/concern frequency* scale, but several items (e.g. #9 "Is a formal assessment required?", #22 "Is finding appropriate placement upon discharge a concern?", #26 "Is involvement in community-based activities required?") are yes/no-shaped questions being forced into a frequency scale — same terminology mismatch noted independently in the discovery doc's Healing Plan section for "Goal Attainment Rating."
- No section header ties items to the "Risk Factor" naming used in the discovery doc/schema (`riskFactor...Concern` fields) — the grouping here (A/B/C/D) doesn't map one-to-one to the schema's flat field list without cross-referencing by item text.

## Discovery-Doc Open-Issue Cross-Check
No claim in the Open Issues section references this form by name.

## Cross-References
- Client ID/File Number field again appears only inside a specific form (here and Case Note/Contact Note/Noteworthy Update), never centrally, consistent with Client Information's face sheet having no dedicated top-level ID field.
- Discovery doc states this form should be completed "within 7 days after intake" — that deadline is not represented anywhere in the file itself.

## Notes
This is a pure rating-scale instrument with no branching logic, no auto-calculated risk score, and no explicit link to the Healing Plan it's supposed to feed into (per the discovery doc's stated sequence Intake → Needs Assessment → Healing Plan).
