# Form: Behavior Tracker Form

## Source
- File: `behavior-tracker.html`
- Format: html

## Field / Section Inventory (verbatim)
**Header fields**: Client Name, Program (select: `-- Select Program --` / Group Home / Supported Independent Living [value="Supported Living"] / Family Reunification [value="family reunification"] / Youth Program / Mental Health Unit / Other → reveals "Other Program Name" text input), Week of (date)

**Daily Behavior and Task Completion Log** — one row per day (Sunday–Saturday), each row has 4 category groups × 3 shift columns (AM/PM/N) + Comments:
- Chores Completed (AM/PM/N)
- Medication Taken (AM/PM/N)
- Respectful Behavior (AM/PM/N)
- Earned Daily Incentive (AM/PM/N)
- Comments

**Weekly Summary** table: Total Days Met, Total Daily Earnings, Bonus Earned (readonly), Total Weekly Incentive (readonly), Balance (readonly)

Buttons: Calculate Summary, Save, Save and Lock, Export as PDF

## Computed / Derived Fields & Formulas
Exact JS from `calculateSummary()`:
```js
const bonus = earnings * 0.25;
const total = earnings + bonus;
const balance = 20 - total;
```
- `earnings` = sum of all 21 "Earned Daily Incentive" AM/PM/N cell values across the week (parsed as float, blank/non-numeric = 0).
- `daysMet` = count of days where that day's 3 incentive cells sum > 0.
- Bonus is hardcoded at 25% of earnings.
- Balance is hardcoded as `20 - total` — i.e. a fixed $20 weekly cap.
- If `balance < 0`, the balance field gets a `.negative-balance` CSS class and a tooltip "Alert: Balance is negative!" — this is a purely visual/client-side flag; no supervisor notification, no alert record, no persistence of any kind exists in the file (there is no backend — `saveData()` only writes to an in-memory JS object `savedData`, never sent anywhere).

## Structural Issues Found
- **Confirmed hardcoded $20 cap and 25% bonus**, exactly as the discovery doc describes, with zero explanation, comment, or configuration option anywhere in the file.
- "Medication Taken" is a free-text cell per shift per day with no connection to any medication record — entirely independent of the MAR forms.
- `saveAndLock()` only disables `input[type="text"]`, `input[type="date"]`, and `select` — it does **not** disable checkboxes (there are none in this form) but note the negative-balance visual flag is not preserved/locked with any special state; a user can still, in theory, load fresh unsaved data after lock since there is no real persistence layer in this static file.
- Program dropdown option text differs subtly from other forms using the same list — see cross-references.

## Discovery-Doc Open-Issue Cross-Check
> "The Behavior Tracker incentive system ($20 cap, 25% bonus) is hardcoded. Confirm: is this universal or per client? Who sets these amounts?"
**CONFIRMED**, verbatim match to the JS shown above — `20 - total` and `earnings * 0.25` are literal hardcoded constants with no client-specific override anywhere in the file.

> "The Behavior Tracker also has a 'Medication Taken' column — is this the same information being recorded twice, or do they serve different purposes?"
Not resolvable from this file alone — the "Medication Taken" cell is a bare free-text field with no label explaining its relationship to the MAR. The file provides no evidence either way; the discovery doc's answer (they serve different purposes) is a **PROPOSED** clarification, not something this source file confirms.

## Cross-References
- Program dropdown list (Group Home / Supported Independent Living / Family Reunification / Youth Program / Mental Health Unit / Other) is near-identical to Activity Calendar's list, but this file's second option text is "Supported Independent Living" while Activity Calendar's is also "Supported Independent Living" (both match here) — see `16-mileage-form.md`, `15-sharp-count.md`, and `17-grocery-list.md` for forms where this same option is spelled differently ("Supportive Living," "Supportive Independent Living," or omitted from the list entirely).
- "Medication Taken" column overlaps conceptually with MAR forms (`12-medication-administration-record-mar-sheet.md`, `13-medication-administration-record-alt.md`).

## Notes
No backend/persistence exists in this file at all — `saveData()` stores to an in-memory object only, and `saveAndLock()` just disables inputs. This confirms the entire 19-file set consists of **static client-side mockups/prototypes**, not functioning data-capture tools — a point relevant to how literally the "Save and Lock" behavior described across forms should be read as a real workflow requirement vs. a UI placeholder the original form-builder added for demonstration purposes.
