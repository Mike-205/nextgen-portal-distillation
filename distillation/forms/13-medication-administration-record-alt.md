# Form: Medication Administration Record (medication-administration-record.html)

## Source
- File: `medication-administration-record.html`
- Format: html

## Field / Section Inventory (verbatim)
Structurally identical section-for-section to `mar-sheet.html` (see `12-medication-administration-record-mar-sheet.md` for the full field list): Client Information, Medication Details (repeatable), Medication Administration Entry (repeatable), Missed or Refused Dose Record (repeatable), Leave of Absence (repeatable), Emergency Response (repeatable), Follow-up Contacts (checklist). All field labels, ids, and JS function names are the same.

## Computed / Derived Fields & Formulas
Identical `checkMedicationTime()` ±60-minute window check and `updateMedicationDropdowns()` session-only population logic — confirmed via `diff` against `mar-sheet.html`, no differences in any JS logic.

## Structural Issues Found (differences from mar-sheet.html, confirmed via `diff`)
- Color scheme uses blue (`#007BFF` / `#0056b3`) instead of mar-sheet.html's earth-brown (`#8B4513` / `#5A2E0A`) — purely cosmetic, but a real, visible inconsistency if both were ever shown to the same user.
- Program dropdown's second option reads **"Supportive Living"** here vs. **"Supported Independent Living"** in `mar-sheet.html` — a third spelling variant of this program name (see cross-file naming issue noted in `00-index.md`).
- **Missing entirely**: the "Export as PDF" button and its `html2pdf` script/CDN include — this file has no PDF export capability at all, while `mar-sheet.html` does.
- No `transition: background-color 0.3s ease;` CSS rule (trivial, cosmetic only).
- Minor formatting-only differences in three inline `<textarea>` closing-backtick placements (Staff Action Taken, Reason for Leave, Immediate Actions Taken blocks) — no functional difference.

## Discovery-Doc Open-Issue Cross-Check
> "The MAR Sheet and Medication Administration Record appear to be exact duplicates. Which one is actually used — or are they used for different purposes?"
**REFUTED.** Confirmed via `diff` that the two files are not identical — see the four concrete differences above. Both implement the exact same fields, workflow, and validation logic; the only substantive functional difference is that this file lacks PDF export. There is no evidence in either file of an intentional "different purpose" — this reads as an earlier or a forked copy of the same file, not two forms serving different needs.

## Cross-References
Same as `12-medication-administration-record-mar-sheet.md`.

## Notes
Given the two files are near-identical with `mar-sheet.html` being the strictly more complete version (has PDF export, no missing features), the discovery doc's own resolution — "retain the title as Medication Administration Record (MAR)" — most likely refers to keeping one canonical form under that name; this file's title is already "Medication Administration Record" while `mar-sheet.html`'s title is also "Medication Administration Record" (both files use the same `<title>` — only their filenames differ, "mar-sheet" vs "medication-administration-record"). The filename, not the on-page title, is the only thing distinguishing them.
