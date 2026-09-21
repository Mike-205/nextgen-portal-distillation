# Form: INDIVIDUAL SAFETY PLAN

## Source
- File: `INDIVIDUAL SAFETY PLAN.txt`
- Round: recently-sent (post-discovery)

## Field / Section Inventory (verbatim)
- Header: "Confidential"
- **1. Client Information** — Client Name, Preferred Name, DOB, Client ID, Program, Primary Support Worker, Case Manager, Date Completed, Review Date
- **2. Client Strengths** — Communication strengths; Independent living skills; Protective factors; Personal coping strategies (all free text)
- **3. Health & Medical Safety** — Medical diagnoses; Allergies; Current medications; Seizure protocol; Diabetes care; Choking risk; Swallowing precautions; Mobility considerations; Medical equipment required; Hospital preference (all free text)
- **4. Behavioural & Emotional Safety** — Risks (☐ Aggression/Self-injury/Elopement/Property damage/Emotional dysregulation/Suicidal ideation/Substance use); Early Warning Signs; Known Triggers; Prevention Strategies; De-escalation Techniques; Crisis Response
- **5. Environmental Safety** — "Identify risks at home or within the program. Examples include:" ☐ Fire safety/Kitchen safety/Bathroom safety/Medication storage/Cleaning chemicals/Sharp objects/Fall prevention/Infection prevention/Weather-related risks
- **6. Personal Care Safety** — Support required for (☐ Bathing/Dressing/Toileting/Eating/Transfers/Skin care/Oral hygiene); Special precautions
- **7. Emergency Response Plan** — Medical emergency procedures; Behavioural crisis response; Fire evacuation procedures; Severe weather procedures; Power outage procedures; Missing person response; Emergency meeting location; Emergency contacts (all free text, no checkboxes)
- **8. Community Outings & Transportation Safety** — Typical Community Activities (☐ Shopping/Recreation/Medical appointments/Employment/School/Social visits/Community events/Banking/Other); Transportation Method (☐ Walking/Staff vehicle/Family vehicle/Public transit/Accessible transit/Taxi-Rideshare/Other); Community Risks (☐ Wandering-elopement/Traffic safety/Crowded places/Stranger awareness/Water hazards/Extreme weather/Food allergies/Behaviour escalation/Falls/Fatigue/Public transportation risks/Medical emergency/Other); Community Safety Strategies (☐ One-to-one supervision/Visual supervision/Carry ID/Medical alert bracelet/GPS device/Cell phone carried/First aid kit/Emergency medication/Regular head counts/Planned meeting location/Weather monitoring/Hydration reminders/Scheduled breaks/Other); Transportation Safety (☐ Seatbelt independently/Requires reminders/Requires assistance/Wheelchair securement/Child safety seat/Specialized restraints); Vehicle loading precautions; Medication During Community Activities (Y/N + table: Medication/Time/Staff responsible/Storage method); If Client Becomes Lost (☐ Search immediate area/Notify supervisor/Contact guardian/Call Police (911 if appropriate)/Follow Missing Person Procedure + Known locations client may go); Emergency Supplies Taken on Community Trips (☐ Cell phone/First aid kit/Medication/Emergency contact list/Water/Snacks/Medical supplies/Activity schedule/Behaviour support tools/Other)
- **9. Staff Responsibilities** — ☐ Review Safety Plan before providing support/Follow identified safety strategies/Document incidents/Report hazards/Communicate changes/Complete required safety checks/Maintain confidentiality
- **10. Plan Review** — Review completed (☐ Upon Admission/Quarterly/Annually/Following Incident/Change in Health/Change in Behaviour/Change in Living Situation); Reason for Review
- **11. Signatures** — Client; Guardian/Decision Maker; Support Worker; Supervisor; Date (one shared Date field for all four signatories)

## Computed / Derived Fields & Formulas
None.

## Structural Issues Found
- **Section 7 "Emergency Response Plan" duplicates site-level emergency procedures (fire evacuation, severe weather, power outage) at the individual-client level**, with no checkboxes — free text only — while Section 8 separately re-covers missing-person response and emergency supplies specifically for community outings, creating two different emergency-supplies/missing-person lists in the same document (Section 7's "Missing person response" line vs. Section 8's "If Client Becomes Lost" checklist).
- **Medication information is split across three places in the same form**: Section 3 "Current medications" (free text), Section 8 "Medication During Community Activities" (table), and no consolidation between them — a client's medication list could disagree between sections since nothing forces them to match.
- **Section 11 has a single shared "Date" field for four different signatories** (Client, Guardian, Support Worker, Supervisor) rather than one date per signature, unlike every other form in this set which pairs each signature with its own date.
- Section 4's risk checkboxes and Section 11 (Safety Plan) risk list closely mirror the risk categories in the Client Intake Form's Section 10/11 (Behavioural Support / Risk Assessment) — see overlap section below.

## Overlap With Original 19 Forms
- **Emergency Preparedness Plan (F10)** — substantial conceptual overlap: F10 covers site-level emergency contacts, evacuation plan, shelter-in-place, supplies checklist, and drills; this form's Section 7 covers the same categories (fire, severe weather, power outage, missing person) but scoped to one client instead of one site. Neither file states whether the client-level plan is meant to reference/inherit from the site-level plan or duplicate it independently.
- No original-19 form previously captured **per-client** behavioural triggers, de-escalation techniques, or community-outing safety strategies — that content is new relative to the original set, though closely related to the Behaviour Tracker (F11, behavior patterns) and Client Intake Form Section 10/11 (this batch, file 20).

## Glossary Cross-Check
- No new Program-name variants introduced (Section 1 has a plain "Program" field, no checkbox list).
- Introduces **"Primary Support Worker"** and **"Case Manager"** as two distinct named roles in Section 1 — "Case Manager" is not in the glossary's current role list (Front-Line Staff / Team Lead-Supervisor / Program Manager / Director of Operations / Executive Director) and also appears in the Client Intake Form's "Assigned Case Manager" field (file 20) and Individual Support Plan (file 23) — a role that shows up three times across these new forms but is undefined anywhere in the discovery doc's org hierarchy (D Q1), which lists "Intake & Admissions Coordinator" and "Program Managers" but no "Case Manager" title.

## Cross-References
- Section 8's "Community Outings & Transportation Safety" content overlaps almost entirely with the **Trip Risk Assessment** form (file 24) — transportation method options, community-risk categories, and emergency-supplies checklists are near-identical in substance between the two, differing mainly in per-client vs. per-trip framing.
- Section 8 implies but does not name the Incident Report for post-event documentation.

## Notes
This form is one of the two (with Individual Support Plan) that Section 8 of the **Individual Support Plan** (file 23) explicitly cross-references by name ("Refer to Individual Safety Plan for detailed safety information") — a genuine, client-confirmed link between two of these five forms, not an inferred one.
