# Form: TRIP RISK ASSESSMENT & EXCURSION PLAN

## Source
- File: `TRIP RISK ASSESSMENT.txt`
- Round: recently-sent (post-discovery)

## Field / Section Inventory (verbatim)
- Header: "Confidential"
- **Section 1: Trip Information** — Trip Name; Purpose of Trip; Destination; Address; Date; Departure Time; Return Time; Trip Leader; Staff Attending; Total Staff; Total Clients; Staff-to-Client Ratio
- **Section 2: Participants** — table (Client Name / Emergency Contact / Medical Alert / Mobility Needs / Behaviour Support Required)
- **Section 3: Transportation** — Method (☐ Walking/Agency Vehicle/Staff Vehicle/Accessible Van/Public Transit/Taxi-Rideshare/Charter Bus/Other); Vehicle Driver; Vehicle License Plate; Transportation Provider (if applicable)
- **Section 4: Destination Assessment** — Accessible (Y/N); Wheelchair Accessible (Y/N); Public Washrooms Available (Y/N); Shelter Available (Y/N); First Aid Available (Y/N); Emergency Exits Clearly Marked (Y/N); Nearest Hospital; Estimated Travel Time
- **Section 5: Risk Identification** — Environmental (☐ Extreme heat/Cold weather/Rain/Snow-Ice/Strong winds/Wildlife/Water hazards/Uneven terrain/Construction/Poor lighting/Slippery surfaces/Other); Transportation (☐ Traffic/Vehicle breakdown/Delays/Public transit issues/Parking hazards/Loading-unloading risks/Other); Client Safety (☐ Elopement/Falls/Aggression/Anxiety/Fatigue/Choking/Allergies/Medication requirements/Seizures/Diabetes/Self-injury/Mental health concerns/Other); Community Risks (☐ Crowds/Stranger interactions/Crime/Lost participant/Food safety/Public washroom risks/Infection exposure/Other)
- **Section 6: Risk Level** — matrix (Transportation/Medical/Behaviour/Environmental/Community × Low/Medium/High); Overall Risk Rating (☐ Low/Moderate/High)
- **Section 7: Risk Mitigation Plan** — Supervision (☐ 1:1/2:1/Group/Frequent Head Counts/Buddy System); Medical Supports (☐ First Aid Kit/Emergency Medication/EpiPen/Glucose Supplies/Water/Snacks/Medical Information Sheet/Other); Behaviour Supports (☐ Visual Schedule/Sensory Supports/Calm Break Area/Positive Reinforcement/Preferred Staff Assigned/Behaviour Support Plan Available/Other); Environmental Controls (☐ Weather Check Completed/Appropriate Clothing/Sunscreen/Bug Spray/Indoor Backup Plan/Hydration Breaks/Accessible Route Planned)
- **Section 8: Emergency Response Plan** — ☐ Provide First Aid/Call 911 if required/Notify Supervisor/Notify Guardian-Family/Complete Incident Report/Preserve scene if required/Follow Individual Safety Plan; Emergency Meeting Point; Nearest Hospital; Emergency Phone Numbers Available (Y/N)
- **Section 9: Medication Plan** — Will medications be required (Y/N); table (Client/Medication/Time Due/Staff Responsible); Medication stored by
- **Section 10: Items to Take** — Safety Equipment (☐ First Aid Kit/Cell Phone/Charger-Power Bank/Emergency Contacts/Medication/PPE/Gloves/Flashlight/Reflective Vest); Client Needs (☐ Water/Snacks/Lunch/Wheelchair/Walker/Communication Device/Behaviour Supports/Change of Clothing/Hygiene Supplies/Blanket/Activity Supplies/Other)
- **Section 11: Staff Assignments** — table (Responsibility: Trip Leader/Driver/First Aid/Medication/Attendance/Emergency Contact × Staff Name)
- **Section 12: Pre-Departure Checklist** — 13 items (weather reviewed, transportation confirmed, staff assigned, medications packed, emergency contacts available, cell phones charged, first aid kit available, client consent obtained, Individual Safety Plans reviewed, Behaviour Support Plans reviewed, head count completed, destination confirmed, funding approval if applicable)
- **Section 13: Post-Trip Review** — Any incidents (☐ No/Yes — Complete Incident Report); Describe concerns/successes/recommendations; Trip completed safely (Y/N); Recommendations for future outings
- **Approvals** — Trip Leader; Supervisor Approval; Program Manager (if required) — each Name/Signature/Date
- **"Best Practice" note** (verbatim, client-authored): "This form should be used for non-routine outings or activities with increased risk (e.g., swimming, hiking, overnight trips, large public events, or out-of-town travel). For routine community activities—such as grocery shopping, medical appointments, or local recreation—the client's Individual Safety Plan is typically sufficient unless new or unusual risks are identified."

## Computed / Derived Fields & Formulas
None found as formulas, but Section 1's "Staff-to-Client Ratio" is a derived value (from Total Staff / Total Clients) with no calculation shown — it's a blank field, not an auto-computed one, in this template.

## Structural Issues Found
- None significant — this is the most internally consistent form audited in this batch: every checkbox section has a purpose, sections build logically from planning (1-4) through risk (5-7) to response (8) to logistics (9-11) to checklist/review (12-13).
- Minor: "Behaviour Support Plan Available" (Section 7) and "Behaviour Support Plans reviewed" (Section 12) reference a document that is not named or defined anywhere else in either this form or the other 23 forms audited (see Cross-References).

## Overlap With Original 19 Forms
- No original-19 form covers trip/excursion-specific risk assessment — this is a **wholly new document type**. The closest original document by subject matter is the **Emergency Preparedness Plan (F10)**, but that is site-level and static (reviewed periodically), whereas this form is per-event and dynamic (completed before each non-routine outing).
- Section 8's Emergency Response checklist overlaps in content (not structure) with F10's emergency contact/evacuation categories, generalized to an off-site context.

## Glossary Cross-Check
- No Program/Service checkbox list appears anywhere in this form — it is the only one of the 5 recently-sent forms that avoids the Program-taxonomy collision entirely.
- Introduces "Trip Leader" as a role/responsibility label — not previously seen; likely an assigned duty rather than a distinct job title, but not defined as either anywhere in the discovery doc's org hierarchy.
- The form's own "Best Practice" note is the clearest, most authoritative (client-authored, unambiguous) statement of scope found across all 24 forms audited to date — it should be treated as CONFIRMED policy language, not a proposal, when building the entity/lifecycle model for when this document is required vs. optional.

## Cross-References
- Section 8 explicitly names "Individual Safety Plan" and implies (via "Complete Incident Report") the Incident Report.
- Section 7 and Section 12 both reference a "Behaviour Support Plan" — this document does not exist among any of the 24 files audited so far (original 19 + these 5). It is distinct from "Behaviour Tracker" (F11, a weekly incentive/tracking log) by name, and its content/existence should be treated as an open question, not assumed to be a synonym.
- Section 12 also references "funding approval (if applicable)" — ties to the billing/funder concept from the discovery doc and Client Service Agreement (file 21).

## Notes
This form's closing "Best Practice" note is a rare example in this whole audit of the source material directly answering "when do I use this form vs. another one" in the client's own words — flag this to the coordinator as a model for how other form-boundary ambiguities (e.g., Case Note vs. Contact Note, Noteworthy Update vs. Incident Report) ideally should have been resolved.
