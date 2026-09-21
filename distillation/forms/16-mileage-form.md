# Form: Personal Mileage Form

## Source
- File: `mileage-form.html`
- Format: html

## Field / Section Inventory (verbatim)
**Header**: Employee Name, Employee #, Pay Period From/To, Supervisor Name, Program (select: `-- Select Program --` / Group Home / Supported Independent Living / Family Reunification [value="family reunification"] / Community Inclusion / Respite / Day Program / Community Support / Youth Support / Other → "Specify Other Program")

**Mileage entries table** (repeatable via "+ Add Entry"): Day (date), From (text), To (text), KM Travelled (number, `oninput` triggers total recalculation), Clients in Transit (text), Reason for Trip (text)

**Totals**: Total KM (readonly, auto-summed), Reimbursement Rate (readonly, hardcoded "$0.50"), Total Claim (readonly, auto-calculated)

**Signatures**: Employee's Sign / Date, Manager/Supervisor Sign / Date

Buttons: Save, Save & Lock, Export as PDF

## Computed / Derived Fields & Formulas
```js
function calculateTotalKM() {
  // sums every .km input across all entry rows
  document.getElementById('totalKm').value = total.toFixed(1);
  document.getElementById('totalClaim').value = "$" + (total * 0.50).toFixed(2);
}
```
- **Reimbursement rate is hardcoded to $0.50/km** both as a displayed readonly field value and as the literal multiplier in the total-claim calculation — no configuration option, no per-employee or per-year rate, no reference to any external rate table anywhere in the file.
- "Clients in Transit" and "Reason for Trip" are plain text fields with no numeric/required validation, so they don't feed any calculation.

## Structural Issues Found
- **Program dropdown list is a different, larger set than every other form in this set**: Group Home, Supported Independent Living, Family Reunification, **Community Inclusion, Respite, Day Program, Community Support, Youth Support**, Other. The four bolded options (Community Inclusion, Respite, Day Program, Community Support, Youth Support) appear on no other form in the 19-file set — either this form predates a later consolidation of program names, or mileage claims are genuinely tracked against a different/finer-grained taxonomy than client documentation is. Also notably **missing "Mental Health Unit"**, which every other form's Program list includes.
- Hardcoded $0.50/km rate is a real, unexplained constant of the same kind flagged for Behavior Tracker's incentive math — the discovery doc's Open Issues section does not mention this one, but it is the same class of problem.
- No approval-status field (e.g. pending/approved/rejected) exists despite two signature lines — the form only captures that a signature occurred, not a workflow state.

## Discovery-Doc Open-Issue Cross-Check
No claim in the Open Issues section references this form by name. **New finding, not previously flagged**: the hardcoded $0.50/km reimbursement rate and the divergent Program option list (see above) are both structural issues of the same character as the Open Issues the discovery doc did flag for other forms, but neither was raised for this one.

## Cross-References
- "Program" list divergence is the most significant cross-form naming inconsistency found in the whole audit — see `00-index.md` for the consolidated list of every distinct Program-option variant found across all forms.
- Existing schema's `PersonalMileage` model has a `reimbursementRate Int?` field (nullable, i.e. theoretically configurable) — but this source form hardcodes it, meaning the prior digitization pass had the opportunity to make it a real per-record field and the form itself still shows it as fixed/readonly.

## Notes
None beyond the above.
