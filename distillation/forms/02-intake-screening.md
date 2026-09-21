# Form: Intake Screening Tool

## Source
- File: `intake-screening.html`
- Format: html

## Field / Section Inventory (verbatim)
**The file literally contains two complete, back-to-back `<!DOCTYPE html>` documents** (a second `<!DOCTYPE html><html><head>...` begins at line 282, inside the body of the first). Both are titled "Intake Screening Tool" with near-identical CSS. They are NOT identical to each other — Version 2 is a superset of Version 1 plus five additional sections.

### Version 1 (lines 1–281) — incomplete
- Section 1 - GENERAL: Date of Referral, Referral Source/Reason, Family/Youth Name, Date of Birth, Gender, Ethnic Background, Current Address, Phone, Additional Comments
- "Family Members/Significant Contacts" table: Name, Relationship, Phone (+ "Add Entry" button)
- **Cuts off here** — no Section 2 onward, no Save/Lock/Export buttons, no closing `</html>` before Version 2 begins.

### Version 2 (lines 282–846) — complete
- Section 1 - GENERAL: same 9 fields as Version 1, reordered (Family/Youth Name and DOB moved to the top, Date of Referral moved near the bottom)
- Family Members/Significant Contacts table (same 3 columns)
- Section 2 – Criteria Assessment: 14 risk/needs rows, each with Y / N / Unknown-N/A checkboxes + Comments text field:
  1. Medical or developmental diagnosis defined by a physician
  2. Medical concerns that require specialized monitoring (e.g., seizures)
  3. Mental disorder/diagnosis defined by a physician
  4. History of suicidal ideation or behaviors
  5. History of self-harming behaviors (e.g., cutting, head banging)
  6. Substantial alcohol use posing risk
  7. Substance misuse posing risk
  8. Criminal justice involvement (e.g., drug trafficking, violence)
  9. Inflicted serious harm to others in past 6 months
  10. Current violent behavior (e.g., punching, biting)
  11. History of weapons use (e.g., guns, knives)
  12. History of fire setting
  13. Safety concerns during transport
  14. Involvement with other services (e.g., AISH, SFI, Mental Health) — free text
  15. Length of Children Services involvement — free text (no Y/N)
  16. Other safety/risk concerns — free textarea (no Y/N)
- Section 3 – Support System, Relationships, Connections: "Close family or meaningful connections", "Natural support such as friends, community"
- Section 4 – Needs Assessment Comments: General Comments, 4A - What is working well/strengths, 4B - Areas of concern/development, 4C - Risk mitigation plan
- Section 5 – Admissibility Determination (Internal Use Only): Yes/No checkbox "referral has been deemed admissible", Explanation for non-admissibility
- Section 6 – Preparation, Review & Authorization (Internal Use Only): three-column table — Prepared by (Name)/Signature/Date, Reviewed by (Name)/Signature/Date, Approved by (Name)/Signature/Date
- Section 7 – Notifications: Referring Agency (Primary), Referring Agency Contact Name, Date Advised, Notes/Comments
- Buttons: Save, Save and Lock, Export as PDF

## Computed / Derived Fields & Formulas
None (no calculations). JS only handles: adding contact rows (`addContact()`), disabling all fields on save-and-lock (`saveAndLock()`), and `window.print()` for PDF export.

## Structural Issues Found
- **Confirmed duplication**, but not the ambiguity the discovery doc implies. Version 1 is not an alternate/competing version of the form — it is a strictly incomplete fragment (cuts off mid-form, no closing tags, no Sections 2–7). Version 2 is the complete form. This reads as a copy-paste/authoring accident (an old draft left in place before the final version was appended), not two competing designs that need a decision.
- Two `<!DOCTYPE html>`, two `<head>`, two `<body>` tags in one file — invalid HTML.
- Field order differs between the two versions' Section 1 (Family/Youth Name first vs. Date of Referral first) — trivial, doesn't affect field set.
- Item 14 and 15 in Section 2 lack the Y/N/Unknown checkbox pattern used by items 1–13, and item 16 is a plain textarea — inconsistent structure within the same section.
- No fields exist anywhere for "3 days after intake" completion deadline mentioned in the discovery doc — the deadline is not represented as data on the form itself.

## Discovery-Doc Open-Issue Cross-Check
> "The Intake Screening file contains two different versions of the form inside one document. Which version is the current one?"
**PARTIALLY CONFIRMED.** Two embedded documents are confirmed. But "two different versions" implies a genuine choice; in fact Version 2 is objectively the complete, later-authored superset (it has 7 sections vs. Version 1's fragment of 1.5 sections) — there's no real ambiguity about which is "current," only about why the incomplete draft was left in the file.

## Cross-References
- Section 6's "Approved by" ties to the referral/acceptance decision workflow described in the discovery doc.
- Section 7 "Referring Agency" overlaps with "Referral Source" on the Client Information face sheet.
- No field here links to a Client ID — matches Client Information's face sheet, which also has no dedicated ID field.

## Notes
Version 2's Section 5 ("Admissibility Determination") and Section 6 ("Preparation, Review & Authorization") are the only place across all 19 forms where a formal accept/decline decision and a three-signature (prepared/reviewed/approved) chain are captured on the document itself.
