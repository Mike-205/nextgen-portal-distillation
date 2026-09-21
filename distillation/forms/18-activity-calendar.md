# Form: Monthly Activity (activity-calendar.html)

## Source
- File: `activity-calendar.html`
- Format: html
- Page `<title>`: "NextGen Support Services - Monthly Activity"; on-page `<h1>`/`<h2>`: "NextGen Support Services" / "Monthly Activity"

## Field / Section Inventory (verbatim)
**Header**: Month (select, Jan–Dec 2025 only, hardcoded list — no other years), Program (select: `-- Select Program --`→ i.e. "Select Program" / Group Home / Supported Independent Living [value="Supported Living"] / Family Reunification [value="family reunification"] / Youth Program / Mental Health Unit / Other → "Specify other program"), Coordinator/Lead Staff, Client Name

**1. Monthly Focus/Goals**: three blank textareas (first has placeholder "Describe goals for the month...", other two have none)

**2. Weekly Breakdown of Activities**: table, 5 fixed rows (Week 1–5), columns: Date Range (two date inputs), Planned Activities, Objective/Purpose, Responsible Staff, Materials Needed (all textareas)

**3. Participant Engagement/Notes**: 5 labeled textareas, one per week (Week 1–5)

**4. Outcomes & Reflection**: two textareas (first has placeholder "Reflect on whether goals were met, challenges, successes...")

**5. Planning for Next Month**: Identified Needs/Suggestions (textarea), Proposed Goals (textarea)

Buttons: Save, Save and Lock, Export as PDF (uses `window.print()`, not html2pdf)

## Computed / Derived Fields & Formulas
None. `lockForm()` disables all inputs/selects/textareas and hides the "Save" button (leaves "Save and Lock" and Export visible per its own logic, though "Save and Lock" itself isn't hidden after being clicked — minor UI inconsistency, not a data issue).

## Structural Issues Found
- Month dropdown is hardcoded to calendar year 2025 only (January 2025–December 2025) — will not represent any other year without manual code edits.
- "Weekly Breakdown" is fixed at exactly 5 weeks regardless of how many weeks the selected month actually spans.

## Discovery-Doc Open-Issue Cross-Check
> "The Activity Calendar and Monthly Activity form (index.html) are byte-for-byte identical. Same question — which one is current?"
**CONFIRMED — verified with `diff activity-calendar.html index.html`, output empty (zero differences).** The two files are 100% byte-identical. See `19-index-html-duplicate.md`.

> (Scope Confirmation Memo) "The Activity Calendar and Monthly Activity form are identical files. One must be removed. Please remove the Monthly Activity Form."
Note for the open-questions register (not resolvable from this file alone): the on-page title of *this very file* is "Monthly Activity," not "Activity Calendar" — the filename `activity-calendar.html` and the on-page title "Monthly Activity" don't match each other, in either duplicate copy. Whichever file survives, its `<title>`/`<h1>`/`<h2>` text still needs to be reconciled with whatever name is chosen — the client's instruction to "remove the Monthly Activity Form" is a filename-level decision that doesn't by itself resolve the fact that the surviving file displays "Monthly Activity" on-page.

## Cross-References
- Program dropdown matches Behavior Tracker's and Shift Checklist's list/spelling exactly ("Supported Independent Living").
- "Weekly Breakdown of Activities" (Week 1–5, with Date Range/Activities/Objective/Staff/Materials columns) maps directly to the existing schema's `MonthlyActivity` model fields (`weekOneDateFrom`...`weekFiveMaterialsNeeded`).

## Notes
See `19-index-html-duplicate.md` for the paired write-up; both files are documented separately per the audit brief even though they are exact duplicates, so the duplication itself is on record.
