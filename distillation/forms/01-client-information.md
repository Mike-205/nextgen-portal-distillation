# Form: CLIENT INFORMATION / FACE SHEET

## Source
- File: `CLIENT INFORMATION.txt` (converted from `CLIENT INFORMATION.docx`)
- Format: txt (originally docx, plain table — no form logic/JS, static reference document)

## Field / Section Inventory (verbatim)
Rendered as a two-column "Section / Details" table, all Details cells blank.

**Client Information**
- Full Name
- Preferred Name / Pronouns
- Date of Birth
- Gender
- Cultural / Ethnic Background
- Spiritual / Religious Affiliation
- Language(s) Spoken
- Immigration Status
- Indigenous Identity (if applicable)

**Contact Information**
- Phone Number
- Email
- Physical Address
- Mailing Address (if different)
- Preferred Method of Contact
- Emergency Contact Name
- Emergency Contact Relationship
- Emergency Contact Phone

**Program Details**
- Program / Service Enrolled
- Admission Date
- Referral Source
- Case Manager / Worker
- Primary Clinician (if applicable)
- Funding Source / Insurance
- File Number / ID
- Discharge Date (if applicable)

**Medical / Health Information**
- Primary Care Physician
- Mental Health Diagnoses
- Physical Health Diagnoses
- Medications
- Allergies / Dietary Needs
- Special Needs / Accommodations
- History of Hospitalization
- Substance Use History
- Other Relevant Health Info

**Legal / Safety Information**
- Guardianship Status
- Court Orders / Legal Issues
- Risk Factors / Safety Alerts
- Involvement with Child Welfare
- Probation / Parole Status

**Additional Notes**
- Strengths / Protective Factors
- Goals / Interests
- Cultural or Spiritual Practices to be Honored
- Notes / Observations

## Computed / Derived Fields & Formulas
None. Static document, no logic of any kind.

## Structural Issues Found
- "File Number / ID" is listed under **Program Details**, not as a top-level client identifier — there is no dedicated unique-ID field at the top of the form (consistent with the discovery doc's statement that clients are currently tracked by name, not ID).
- No signature/sign-off block, no date-completed field, no "completed by" field — unlike almost every other form in this set (Case Note, Contact Note, Noteworthy Update, Emergency Preparedness Plan, Intake Screening, Needs Assessment all have a signature/sign-off section; this one does not).
- No lock/save mechanism described (it's a static docx table, not an HTML form) — so "Save & Lock" behavior seen on the HTML forms doesn't apply here; this file gives no indication of how this document is meant to be finalized.

## Discovery-Doc Open-Issue Cross-Check
No claim in the Open Issues section references this form by name.

## Cross-References
- "Case Manager / Worker" and "Primary Clinician" fields imply a link to staff/user records.
- "Program / Service Enrolled" implies a link to a program entity.
- "Medications" field here overlaps with the Medication Administration Record and Behaviour Tracker's "Medication Taken" column — this file gives no indication of which is authoritative.

## Notes
This is the only one of the 19 files with no interactivity, no buttons, and no sign-off block — it reads as a pure field checklist rather than a workflow-integrated form.
