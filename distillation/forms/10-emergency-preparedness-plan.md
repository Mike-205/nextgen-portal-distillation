# Form: Emergency Preparedness Plan

## Source
- File: `Emergency Preparedness Plan.txt` (converted from `.docx`)
- Format: txt (static table, no JS/logic)

## Field / Section Inventory (verbatim)
**1. Site Information**: Program Name, Site Address, Phone Number, Emergency Coordinator Name, Alternate Contact Person, Number of Residents/Clients, Number of Staff (Per Shift), Nearest Hospital/Clinic, Date of Last Emergency Drill, Date of Plan Review

**2. Types of Emergencies Covered** (checkbox): ☐ Fire ☐ Flood ☐ Power Outage ☐ Severe Weather ☐ Medical Emergency ☐ Missing Person (AWOL) ☐ Violence/Threat/Intruder ☐ Earthquake ☐ Pandemic/Infectious Disease ☐ Evacuation Required ☐ Shelter-in-Place ☐ Other

**3. Emergency Contacts** (table: Contact Type / Name-Agency / Phone / Email), rows: Emergency Services (pre-filled "911" / "N/A" / "N/A"), Police (Non-Emergency), Fire Department, Medical Facility, On-Call Supervisor, Property Manager, Transportation

**4. Evacuation Plan**: Evacuation Route(s), Meeting Point (Primary), Alternate Meeting Point, Assigned Staff Responsibilities (Task/Comment rows: Client headcount, Grab emergency kits, Notify authorities, Support clients with mobility needs), Transportation Plan (if relocation required)

**5. Shelter-in-Place Plan**: Designated Safe Room, Supplies Located At, Duration of Shelter Capacity, Staff Responsibilities During Shelter-in-Place

**6. Emergency Supplies Checklist** (Item / Present ☐Yes ☐No / Location): First Aid Kit, Emergency Contact List, Flashlights/Batteries, Emergency Food & Water (3 Days), Medications/Health Supplies, Blankets/Warm Clothing, Fire Extinguisher, Emergency Binder (Plans, Forms)

**7. Training and Drills** (Drill Type / Date Last Conducted / Next Scheduled): Fire Drill, Evacuation Drill, Shelter-in-Place, Lockdown/Intruder; plus "Staff Trained on Emergency Plan: ☐ Yes ☐ No"

**8. Special Considerations**: Clients with Accessibility or Medical Needs, Behavioral Considerations in Emergencies, Communication with Non-Verbal Clients/Language Needs

**9. Post-Emergency Procedures** (☐ Yes ☐ No each): Incident Report Completed, Debrief with Staff & Clients Held, Follow-up Support Required, Plan Reviewed and Updated

**Sign-Off**: Prepared/Reviewed By, Title, Date; Supervisor Approval, Date

## Computed / Derived Fields & Formulas
None.

## Structural Issues Found
- This is the most structurally complete form in the set — all 9 numbered sections are present and consistent, with a sign-off block (unlike Healing Plan and Client Information, which lack one).
- "Emergency Services" row is pre-filled with "911" / "N/A" / "N/A" while every other contact row is blank — this is a legitimate default (911 is always the emergency number), not leftover sample data, unlike the Needs Assessment form's pre-filled date.

## Discovery-Doc Open-Issue Cross-Check
No claim in the Open Issues section references this form by name.

## Cross-References
- "Types of Emergencies Covered" checklist matches `EMERGENCIES_COVERED_TYPE` enum in the existing schema field-for-field.
- Section 9 "Incident Report Completed: ☐ Yes ☐ No" is a boolean flag with no link to an actual Incident Report record — same "flag without linked record" pattern seen on Client Noteworthy Update's Cross Reference checklist.

## Notes
No issues requiring resolution were found in this file — it can likely proceed to per-field spec with minimal open questions, aside from the general cross-cutting "flag vs. linked record" pattern noted above.
