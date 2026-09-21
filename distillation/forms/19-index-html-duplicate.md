# Form: Monthly Activity (index.html)

## Source
- File: `index.html`
- Format: html

## Field / Section Inventory (verbatim)
**Identical to `activity-calendar.html` in every byte** — confirmed via `diff activity-calendar.html index.html`, which produced zero output (no differences at all, not even whitespace). See `18-activity-calendar.md` for the full field inventory; it applies unchanged to this file.

## Computed / Derived Fields & Formulas
Identical to `activity-calendar.html` — same `toggleOtherProgram()` and `lockForm()` functions, byte-for-byte.

## Structural Issues Found
- This file's existence as a second, fully identical copy of `activity-calendar.html` (under the generic filename `index.html`, likely because it was originally served as the directory's default page) is itself the structural issue — not a variant or an alternate design, but a literal duplicate copy.

## Discovery-Doc Open-Issue Cross-Check
> "The Activity Calendar and Monthly Activity form (index.html) are byte-for-byte identical. Same question — which one is current?"
**CONFIRMED**, and there is no meaningful "which one is current" question — they are the same file under two names. Any decision here is purely about which filename/route to keep, not about reconciling different content.

## Cross-References
Same as `18-activity-calendar.md`.

## Notes
Recommend treating `activity-calendar.html` and `index.html` as one entry in any downstream entity/form spec — they are not two forms, they are one form with two filenames.
