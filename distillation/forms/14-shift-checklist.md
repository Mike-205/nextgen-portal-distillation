# Form: Shift Checklist

## Source
- File: `shift-checklist.html`
- Format: html

## Field / Section Inventory (verbatim)
**Header**: Staff Name, Program (select: [disabled placeholder] Select program / Group Home / Supported Independent Living / Family Reunification / Youth Program / Mental Health Unit / Other → text input), Date, Time

**Tabs**: Morning Shift / Afternoon Shift / Night Shift (only one visible at a time)

**Morning Shift Tasks** (19 rows, each: checkbox + task label + free-text Comment cell):
Shift Exchange To Be Completed Upon Arrival; Medication/Narc Count Done; Meds Administered & Signed Off; Staff Communication Log Read; Client Wake Up Call to Complete Morning Routines; Schedule/Take Client for Appointments; Drop off at School/Pick Up as needed; Follow Client Food Schedule; Kitchen/Dining/Living Area Cleaned & Sanitized as Needed; Mop Floor If Needed; Sharp Count Completed; Client's Laundry Washed, Dried & Folded; Put Clean Laundry away in Room; Winter: Shovel Sidewalks, Stairway Clean & Salt Walkways; Summer: Trim Grass; Water Temperature Checked; Behavior Tracker Form completed; Complete Daily Logs, Case Notes & Incident Reports; Shift Exchange To Be Completed Before Departure.
Buttons: Checkmark All, Save, Save & Lock.

**Afternoon Shift Tasks** (20 rows): Shift Exchange Upon Arrival; Medication/Narc Count Done; Meds Administered & Signed Off; Staff Communication Log Read; Support Client to complete their chores; Schedule/Take Client for Appointments; School Pick Up; Follow Client Food Schedule; Dishwasher started; Kitchen/Dining/Living Area Cleaned & Sanitized as Needed; Lightly Clean all Bathrooms if needed; Mop Floor If Needed; Sharp Count Completed; Complete Case notes/Daily logs; Behavior Tracker Form completed; Winter: Shovel Sidewalks...; Summer: Trim Grass; Water Temperature Checked; Complete Daily Logs, Case Notes & Incident Reports; Shift Exchange Before Departure. Same 3 buttons.

**Night Shift Tasks** (15 rows): Shift Exchange Upon Arrival; Staff Communication Log Read; Medication/Narc Count Done; Meds Administered & Signed Off; Check Appointment & Set Reminders; Follow Client Food Schedule; Client Night Routines Supported (Hygiene, Bedtime); Sharp Count Completed; Kitchen/Dining/Living Area Cleaned & Sanitized; Clean all Bathrooms; Mop Floor; Clean Laundry & Furnace Room; Complete Daily Logs, Case Notes & Incident Reports; Behavior Tracker Form completed; Shift Exchange Before Departure. Same 3 buttons.

## Computed / Derived Fields & Formulas
- "Checkmark All" (`checkAll(sectionId)`): checks every non-disabled checkbox within the active shift section only.
- "Save & Lock" (`saveAndLockShift(shift)`): disables all inputs within that shift section and hides its own Save & Lock button — locking is per-shift-section, not per whole form.
- No calculation logic anywhere.

## Structural Issues Found
- Each task row's Comment cell is a free-text input, always blank by default (as expected for a blank template) — this is normal, not a defect.
- No client-specific or program-specific task variation is implemented — the same fixed task list appears regardless of which Program is selected in the header (the Program dropdown has no `onchange` handler wired to alter the task tables).
- No date/time validation tying "Time" field to which of the 3 tabs should be active.

## Discovery-Doc Open-Issue Cross-Check
> "The Shift Checklist has no actual tasks listed. The full task list for each program (Group Home, SIL, etc.) must be provided before this form can be built."
**REFUTED as stated.** The file already contains a fully populated, non-empty task list for all three shifts (19 Morning / 20 Afternoon / 15 Night tasks, each with real task text) — it is not the case that "every task row is empty." What IS true: the task list is a single fixed set, not varied by Program — so if the real requirement is *per-program* task lists (as the discovery doc's answers describe for Group Home vs. SIL vs. other programs), that variation is genuinely absent from this file. The claim "no actual tasks listed" does not match what's in the file; the more accurate open issue is "tasks exist but are not program-specific."

## Cross-References
- Task rows reference other forms by name directly: "Complete Daily Logs, Case Notes & Incident Reports," "Behavior Tracker Form completed," "Sharp Count Completed," "Meds Administered & Signed Off" — this form functions as a per-shift index/gate for four other forms in this set (Daily Log, Case Note, Incident Report, Behavior Tracker, Sharp Count, MAR), but contains no actual links/IDs to those records, only checkbox reminders.
- Program dropdown list matches the six-option set used by Behavior Tracker and Activity Calendar (Group Home / Supported Independent Living / Family Reunification / Youth Program / Mental Health Unit / Other), spelled identically here.

## Notes
This file directly contradicts the discovery doc's Open Issue claim about it — worth flagging clearly in the register as a claim that does not hold up against the actual source file, rather than silently accepting the discovery doc's framing.
