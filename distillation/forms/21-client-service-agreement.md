# Form: CLIENT SERVICE AGREEMENT

## Source
- File: `CLIENT SERVICE AGREEMENT.txt`
- Round: recently-sent (post-discovery)

## Field / Section Inventory (verbatim)
- Header: "Confidential Client Document"; Purpose statement (relationship, services, responsibilities, expectations, rights, conditions of service delivery)
- **Section 1: Client Information** — Client Name, Preferred Name, DOB, Client ID, Address, Phone, Email
- **Section 2: Legal Representative / Decision Maker** (if applicable) — Name, Relationship, Phone, Email, Authority (☐ Guardian/Substitute Decision Maker/Power of Attorney/Other)
- **Section 3: Service Provider Information** — Organization (NextGen Support Services, fixed); Primary Contact, Position, Phone, Email, Office Address
- **Section 4: Services to be Provided** — ☐ Respite Care / Supported Independent Living (SIL) / Community Access Support / Youth Support Services / Life Skills Development / Mental Health Support / Behaviour Support / Employment/Skill Development Support / Training & Consultation Services / Other
- **Section 5: Service Description** — purpose statement; Services may include (☐ Personal support/Community participation/Skill development/Daily living assistance/Social-recreational activities/Goal development/Health and wellness support/Family support and communication/Other)
- **Section 6: Service Schedule** — Service Start Date; Frequency (☐ Daily/Weekly/Monthly/As Required/Other); Scheduled Service Days; Scheduled Hours; note that services may be adjusted
- **Section 7: Client-Centred Support Commitment** — 8 agency commitments (dignity/privacy/culture, safe support, Individual Support Plan-based, confidentiality, respectful communication, independence/skill development, responsive to concerns, legislation/policy compliance)
- **Section 8: Client / Family Responsibilities** — 7 items (accurate info, inform of changes, respectful treatment of staff, safe environment, participate in planning/reviews, funding/payment info, communicate concerns)
- **Section 9: Client Rights** — 8 items (dignity/respect, participate in decisions, freedom from discrimination/abuse/neglect/exploitation, privacy, choice, raise concerns without retaliation, request service changes, access personal info per law)
- **Section 10: Privacy & Confidentiality** — info shared with (☐ Funding agencies/Healthcare providers/Emergency services/Guardian-SDM/Other authorized individuals); Client authorization (☐ Provided/Declined)
- **Section 11: Health & Safety Requirements** — client agrees to provide info on: Medical conditions, Allergies, Medications, Safety concerns, Behavioural support needs, Emergency contacts (no checkboxes/blanks — topic labels only); NextGen will maintain (☐ Individual Support Plan/Individual Safety Plan/Emergency Plan/Other required assessments)
- **Section 12: Medication Support** — ☐ Not required/Reminders only/Administration required/Medication monitoring; note re: NextGen policies
- **Section 13: Transportation Agreement** — ☐ Required/Not Required; if provided: Safety procedures, seatbelts, vehicle requirements, risk assessment (statements, no checkboxes); Additional transportation arrangements (free text)
- **Section 14: Fees & Payment Information** — Funding Source (☐ Government Funding/Insurance/Private Pay/Other); Service Rate ($___ per ☐Hour/Day/Week/Month); Payment Schedule (☐ Weekly/Biweekly/Monthly/Other)
- **Section 15: Cancellation Policy** — Cancellation Notice Required (☐ 24 hours/48 hours/Other); Cancellation fees (free text)
- **Section 16: Incidents & Concerns** — statement; Concerns may be reported to: Name, Position, Contact
- **Section 17: Service Termination** — ☐ Client request/Completion of goals/Funding changes/Change in needs/Safety concerns/Non-compliance/Other; reasonable notice statement
- **Section 18: Agreement Acknowledgement** — 4 acknowledgement checkboxes
- **Signatures** — Client (Name/Signature/Date); Guardian/SDM (Name/Signature/Date, if applicable); NextGen Representative (Name/Position/Signature/Date)
- **Service Review Information** — First Review Date; Review Frequency (☐ Quarterly/Semi-Annual/Annual/As Needed)

## Computed / Derived Fields & Formulas
None — no calculations. Service Rate is a manually entered dollar figure with a per-unit selector (Hour/Day/Week/Month), not a calculated field.

## Structural Issues Found
- **Section 11 and Section 13 list topics/statements with no actual input controls** (no blanks, no checkboxes) — inconsistent with every other section in this same form, which uses either checkboxes or underscore blanks. As written, there's nowhere to record the client's actual medical conditions/allergies/medications, or to confirm the transportation safety statements were reviewed.
- Section 4 "Services to be Provided" and Section 5 "Services may include" are two separate checklists of overlapping granularity (Section 4 = program-level service types, Section 5 = activity-level service types) within the same form — no stated relationship between the two lists.
- Section 10 "Client authorization: ☐ Provided / ☐ Declined" is a single global consent toggle for ALL info-sharing categories listed above it (funding agencies, healthcare providers, emergency services, guardian/SDM, other) — no per-category consent, unlike the Client Intake Form's Section 17 which lists consent as separate checkable items per purpose.

## Overlap With Original 19 Forms
- No equivalent document exists among the original 19 — this is a **wholly new document type** (a client-facing services contract/consent agreement). The original 19 are entirely internal staff documentation forms; nothing in that set covers agency-client contractual terms, fees, cancellation policy, or client rights.
- Section 11's reference list (Individual Support Plan, Individual Safety Plan, Emergency Plan) points to two of the other 4 recently-sent forms and, via "Emergency Plan," likely to the original **Emergency Preparedness Plan (F10)** — naming variant: "Emergency Plan" here vs. "Emergency Preparedness Plan" in F10.
- Section 13 Transportation Agreement overlaps in subject matter (not fields) with **Personal Mileage Form (F16)** and the transportation-safety content in Individual Safety Plan / Trip Risk Assessment (see files 22/24), but at a contractual/consent level rather than an operational-documentation level.

## Glossary Cross-Check
- Section 4's service checklist ("Respite Care, Supported Independent Living (SIL), Community Access Support, Youth Support Services, Life Skills Development, Mental Health Support, Behaviour Support, Employment/Skill Development Support, Training & Consultation Services, Other") is yet another Program/Service taxonomy variant, matching neither the glossary's canonical 5-program list nor either of the two lists found in the Client Intake Form (see file 20). "Training & Consultation Services" here is closer to the original schema's `PROGRAM_SERVICE` enum value `TRAINING_CONSULTING_SERVICES`, which doesn't appear in either Client Intake Form list.
- "Emergency Plan" (Section 11) is a new short-form name for what the glossary already canonicalized as "Emergency Preparedness Plan" — add as a variant.
- Introduces "NextGen Representative" as a signatory role — not previously named in the glossary's role list; unclear if this maps to a specific existing role (e.g., Program Manager, Intake Coordinator) or is meant generically.

## Cross-References
- Section 11 explicitly names Individual Support Plan and Individual Safety Plan (both audited separately in this batch, files 23 and 22).
- Section 16 "Incidents & Concerns" implies but does not name the Incident Report form.
- Section 12 Medication Support implies but does not name the MAR.

## Notes
This is the only document in the 24 forms audited so far that is explicitly a bilateral agreement (both parties sign, both parties have stated obligations) rather than a staff-completed operational record — a structurally different category of document than everything audited previously.
