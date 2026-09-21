# Form: CLIENT INTAKE FORM

## Source
- File: `CLIENT INTAKE FORM.txt`
- Round: recently-sent (post-discovery). Note: this form was redrafted by the coordinator's collaborator and already approved by the client. This audit is factual only — quality review of the redesign is a separate, later task.

## Field / Section Inventory (verbatim)
- **Section 1: Intake Information** — Date of Intake; Referral Source (☐ Self / Parent/Guardian / Family Member / AHS / PDD / FSCD / Children's Services / School / Physician / Community Agency / Other); Staff Completing Intake; Referral Date; Program Requested (☐ Residential Support / Supported Independent Living (SIL) / Respite Care / Community Access / Youth Services / Behaviour Support / Mental Health Support / Employment Support / Other)
- **Section 2: Client Information** — Full Legal Name (First/Middle/Last); Preferred Name; Date of Birth; Age; Gender (☐ Male/Female/Non-Binary/Prefer Not to Say/Other); Pronouns (☐ He-Him/She-Her/They-Them/Other); Primary Language; Interpreter Required (Y/N); Marital Status (☐ Single/Married/Common Law/Divorced/Widowed); Client ID (if applicable)
- **Section 3: Contact Information** — Home Address, City, Province, Postal Code, Phone, Email; Preferred Method of Contact (☐ Phone/Email/Text)
- **Section 4: Emergency Contact** — Name, Relationship, Phone, Alternate Phone
- **Section 5: Legal Guardian / Substitute Decision Maker** — Does client have guardian (Y/N); if Yes: Name, Relationship, Phone, Email
- **Section 6: Funding Information** — Funding Agency (☐ PDD/FSCD/AISH/Jordan's Principle/Private Pay/Insurance/Other); Case Worker Name, Phone, Email
- **Section 7: Medical Information** — Family Physician, Clinic, Phone; Medical Diagnoses; Mental Health Diagnoses; Current Medications (table: Medication/Dose/Frequency/Purpose); Allergies (☐ None/Medication/Food/Environmental + Describe); Special Diet (☐ None/Diabetic/Gluten Free/Vegetarian/Texture Modified/Other); Vision (☐ Glasses/Contacts/Blind/No Concerns); Hearing (☐ Hearing Aid/Deaf/No Concerns); Mobility (☐ Independent/Walker/Wheelchair/Cane/Requires Staff Assistance)
- **Section 8: Personal Care** — Requires assistance with (☐ Bathing/Dressing/Grooming/Toileting/Feeding/Medication/Transfers); Additional Information
- **Section 9: Communication** — Primary Communication (☐ Verbal/Sign Language/Communication Device/Picture Exchange/Limited Speech/Non-Verbal); Communication Preferences
- **Section 10: Behavioural Support** — History of behaviours of concern (Y/N); if yes (☐ Aggression/Self-Injury/Property Damage/Elopement/Verbal Aggression/Sexualized Behaviour/Substance Use/Other); Describe; Known Triggers; Successful Support Strategies
- **Section 11: Risk Assessment** — History of (☐ Falls/Seizures/Suicide Risk/Self Harm/Violence/Abuse/Fire Setting/Wandering/Choking Risk/Swallowing Difficulties); Additional Notes
- **Section 12: Daily Living Skills** — Can independently (☐ Cook/Clean/Laundry/Grocery Shop/Budget/Medication Management/Public Transportation/Personal Hygiene); Needs support with
- **Section 13: Employment / Education** — Current Status (☐ Student/Employed/Unemployed/Volunteer/Retired); School/Employer; Hours
- **Section 14: Social & Recreational Interests** — Favourite Activities (☐ Sports/Walking/Movies/Video Games/Reading/Music/Arts/Cooking/Swimming/Social Events/Other); Goals for Participation
- **Section 15: Client Goals** — Short-Term Goals; Long-Term Goals
- **Section 16: Service Needs** — Services Requested (☐ Community Access/SIL/Respite/Life Skills/Employment Support/Behaviour Support/Mental Health/Transportation/Recreation); Preferred Schedule (☐ Days/Evenings/Weekends); Preferred Start Date
- **Section 17: Consents** — ☐ Collect personal information / Share with funding agencies / Contact healthcare providers / Contact emergency contacts / Obtain previous records / Photography Consent / Email Communication / Text Message Communication
- **Section 18: Additional Information** — free text
- **Section 19: Signatures** — Client Name/Signature/Date; Guardian Signature/Date (if applicable); Staff Completing Intake/Signature/Date
- **Internal Use Only** (appended after signatures) — Eligibility Determination (☐ Accepted/Waitlisted/Declined); Assigned Program; Assigned Case Manager; Orientation Scheduled; Service Start Date; Next Review Date

## Computed / Derived Fields & Formulas
None found — no calculations or auto-fill logic in this file.

## Structural Issues Found
- **Two different, mutually inconsistent "program/service" checklists in the same form**: Section 1 "Program Requested" (Residential Support, SIL, Respite Care, Community Access, Youth Services, Behaviour Support, Mental Health Support, Employment Support, Other) vs. Section 16 "Service Needs" (Community Access, SIL, Respite, Life Skills, Employment Support, Behaviour Support, Mental Health, Transportation, Recreation). Neither list matches the other, and neither matches any prior taxonomy from the original 19 forms.
- **"Internal Use Only" admin/placement block is appended after the client/guardian/staff signature block** rather than being a separate section or document — client-facing intake data and internal eligibility/assignment decisions share one physical form with the signatures sitting between two unrelated concerns.
- Section 5 asks "Does the client have a guardian?" but Section 19 unconditionally includes a "Guardian Signature (if applicable)" line — the conditional logic implied by Section 5 isn't reflected structurally elsewhere in the form.
- Medical info is split: Section 7 has "Allergies" as its own checkbox group, but Section 2/Section 7 also each hold different medical-adjacent fields (Marital Status is in Section 2 with demographics, unrelated to the rest of that section's identity fields).

## Overlap With Original 19 Forms
- **CLIENT INFORMATION.txt (F01)** — near-total field overlap: name, DOB, gender, contact info, emergency contact, physician, medications, allergies are captured in both. This form appears to supersede/absorb F01's content rather than complement it.
- **intake-screening.html (F02)** — overlaps on referral source, program suitability/eligibility, and the "Internal Use Only" acceptance decision block, which mirrors intake-screening's role in the referral→acceptance workflow described in the discovery doc.
- **Individual Needs Assessment Form.txt (F03)** — Sections 8–14 (Personal Care, Communication, Behavioural Support, Risk Assessment, Daily Living Skills, Employment/Education, Social & Recreational) duplicate F03's needs-assessment content almost category-for-category.
- Net effect: this single form now covers ground previously split across three separate original documents (Client Information, Intake Screening Tool, and much of the Individual Needs Assessment). Whether those three are meant to be retired in favor of this one, or still coexist with duplicate data entry, is not stated anywhere in this file.

## Glossary Cross-Check
- Introduces a **third and fourth Program/Service taxonomy** not resolved in `glossary.md` (which already flags a Program-spelling collision from the original 19). Neither Section 1 nor Section 16's list matches the glossary's canonical 5-program list (Transportation, Respite Care, Group Care/Youth, Family Reunification, SIL). Both lists here include "Mental Health Support" and "Behaviour Support" as selectable items alongside residential/respite-type options, and add "Residential Support," "Community Access," "Employment Support," "Life Skills," "Recreation" — none of which appear in the glossary's Program entry.
- "Mental Health Support" appearing as a checkbox in a program-requested list reinforces the open question already flagged in the glossary (Mental Health Unit as a program) rather than resolving it — here it's offered as a selectable "program," contradicting the discovery doc's "not a standalone program" rule from the opposite direction (client-facing intake language, not just an old schema enum).

## Cross-References
- "Assigned Case Manager" (Internal Use Only) — introduces "Case Manager" as a role name not yet defined in the glossary's role list (Front-Line Staff / Team Lead-Supervisor / Program Manager / Director of Operations / Executive Director). Unclear if synonymous with an existing role or a new one.
- Section 6 Funding Information duplicates the funding-agency concept also present in the discovery doc's billing/funder discussion.

## Notes
This form's Sections 17 (Consents) and demographic granularity (pronouns, interpreter required, marital status) do not appear anywhere in the original 19 forms — genuinely new data captured, not previously present in any form.
