# Form: Grocery List

## Source
- File: `grocery-list.html`
- Format: html

## Field / Section Inventory (verbatim)
**Header**: Week (date), Program (select: `-- Select Program --` / Group Home / **Supportive Independent Living** [value="Supported Living"] / Family Reunification [value="family reunification"] / Youth Program / Mental Health Unit / Other → "Specify other program")

**Nine category sections**, each an identical 3-column table (Item / Quantity / Notes) starting with zero rows, each with its own "Add Entry" button:
🥦 Produce, 🍞 Bakery & Grains, 🥩 Meat, Poultry & Fish, 🧀 Dairy & Alternatives, 🧼 Household & Cleaning Supplies, 🍽️ Pantry, 🧃 Beverages, 🍭 Snacks & Treats, ❄️ Frozen Foods

**Additional Notes / Special Requests**: single textarea

Buttons: Save, Save & Lock, Export as PDF

## Computed / Derived Fields & Formulas
None — no totals, no budget calculation.
- `lockForm()` adds a `.locked` CSS class to the whole form (`pointer-events: none` on inputs) rather than individually disabling each input, unlike every other form in the set which disables inputs directly — a different, weaker locking implementation (CSS-only; underlying input `disabled` state is never set, so form data would still submit if a real backend existed).

## Structural Issues Found
- **Program dropdown's second option reads "Supportive Independent Living"** — yet another distinct spelling from "Supported Independent Living" (used by Behavior Tracker, Shift Checklist, Activity Calendar, mar-sheet.html) and "Supportive Living" (medication-administration-record.html, sharp-count.html's `supportiveLiving` maps to displayed "Supported Independent Living" — actually check: sharp-count.html displays "Supported Independent Living" text but internal value `supportiveLiving`). This file is the only one using the third variant "Supportive Independent Living" as **displayed text**.
- Locking implementation differs functionally from every other form (CSS `pointer-events: none` vs. setting `disabled = true` on each field) — inconsistent lock behavior across the form set.
- Nine fixed grocery categories with no way to add a tenth category, and no per-client or per-program tailoring of which categories appear.

## Discovery-Doc Open-Issue Cross-Check
No claim in the Open Issues section references this form by name.

## Cross-References
- Program dropdown option — see `00-index.md` for the full cross-form Program-naming inconsistency list; this file contributes yet another spelling variant.
- Category list (`GROCERY_ITEM_TYPE` in the existing schema: PRODUCE, BAKERY_GRAINS, MEAT_POULTRY_FISH, DAIRY_ALTERNATIVES, HOUSEHOLD_CLEANING_SUPPLIES, PANTRY, BEVERAGES, SNACKS_TREATS, FROZEN_FOODS) matches this file's nine sections exactly, one-to-one.

## Notes
None beyond the above.
