# Form: Monthly Sharp Count Checklist

## Source
- File: `sharp-count.html`
- Format: html

## Field / Section Inventory (verbatim)
**Header**: Month (select, auto-populated Jan–Dec, defaults to current month), Year (select, auto-populated 2000–2100, defaults to current year)

**Program** (select): `-- Select Program --` (value="default") / Group Home (value="groupHome") / Supported Independent Living (value="supportiveLiving") / Family Reunification (value="family reunification") / Youth Program (value="youthProgram") / Mental Health Unit (value="mentalHealthUnit") / Other (value="other") → reveals "Enter program name" text input

**Sharp count table**: rows = individual sharp items (Sharp Type text input, Quantity number input — both added via "Add Sharp Type" button, starts with zero rows); columns = every day of the selected month (dynamically generated: `Day 1`...`Day N`) × 3 shifts each (A/P/N), each cell a plain checkbox.

**Notes/Changes** (toggle-shown section, "Add Entry" button adds rows): Staff Name (text), Change Noted (textarea), Day-of-month (select 1–31), "Lock Entry" button (per-row lock).

Buttons: Add Sharp Type, Lock Sharp Type, Lock Quantity, Save, Save and Lock.

## Computed / Derived Fields & Formulas
```js
const sharpDataPresets = {
  groupHome: [],
  supportiveLiving: [],
  youthProgram: [],
  mentalHealthUnit: [],
  other: []
};
```
- Selecting a Program loads `sharpDataPresets[value]` as the starting sharp-item list for that program — **every preset array is empty**, so no program starts with any predefined sharp types; the user must click "Add Sharp Type" and type each one in manually, every time, for every program.
- "Lock Sharp Type" / "Lock Quantity" are independent per-month-per-year toggles (`getCurrentLockKey()` = `${year}-${month}`) that disable only the Name or only the Quantity input column, not the daily checkboxes.
- `numDays` for the header grid is computed from `new Date(year, month, 0).getDate()` — correctly handles variable month lengths.

## Structural Issues Found
- **Confirmed: all program presets are empty arrays** — no sharp types are pre-defined for any program.
- No two-person/dual-verification field exists anywhere (no second staff-name field for count verification), despite the discovery doc describing sharp counts as requiring two independent counters.
- No discrepancy/mismatch detection or alert logic exists — the checkboxes are simple per-shift-per-day marks with no expected-vs-actual comparison.
- "family reunification" is the only Program option using a lowercase, space-containing `value` attribute instead of camelCase like its siblings (`groupHome`, `supportiveLiving`) — inconsistent internally within this same file's own option values.

## Discovery-Doc Open-Issue Cross-Check
> "The Sharp Count presets are empty for all programs. The list of sharp types tracked per program must be provided."
**CONFIRMED**, verbatim — `sharpDataPresets` literally defines every program key as an empty array in the source.

## Cross-References
- Program list matches Behavior Tracker/Shift Checklist's set in content, though this file uses camelCase JS values internally (`groupHome`, `supportiveLiving`, `youthProgram`, `mentalHealthUnit`) rather than the display-string values used elsewhere — an internal naming convention difference, not a display difference (the *displayed* label "Supported Independent Living" matches Behavior Tracker/Shift Checklist's wording here).
- Shift Checklist's task list includes "Sharp Count Completed" as a checkbox reminder with no link to this form's data.

## Notes
None beyond the above.
