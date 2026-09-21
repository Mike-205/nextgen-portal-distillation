# Original Forms Audit — Index

Factual audit of the 19 original form files NextGen provided (paper/HTML forms, pre-digitization). Each row links to its full spec sheet. This index does not resolve anything — it is a map of what was found, for use when building the glossary, entity model, and open-questions register.

| # | Source file | Canonical form name (on-page/in-file) | Names used elsewhere (discovery doc / scope memo) | Status |
|---|---|---|---|---|
| 01 | `CLIENT INFORMATION.txt` | CLIENT INFORMATION / FACE SHEET | "Client Information," "Face Sheet" | Clean — no structural issues, but no sign-off block and no dedicated ID field |
| 02 | `intake-screening.html` | Intake Screening Tool | "Intake Screening Tool" | **Contains two embedded HTML documents** — a fragment (Section 1 + contacts only) followed by a complete 7-section version |
| 03 | `Individual Needs Assessment Form.txt` | Individual Needs Assessment Form | "Individual Needs Assessment," "Needs Assessment" | Has a stray pre-filled date (07/03/2025) left in a blank template |
| 04 | `Healing Plan.txt` | FAMILY LIVING PROGRAM – HEALING PLAN | "Healing Plan" | **Has 4 Medicine Wheel goal areas (incl. Emotional Wellbeing); existing schema only implements 3** — new finding, no version/review-date field |
| 05 | `Client Case Note.txt` | Client Case Note | "Case Note" | Clean internally; overlaps heavily with #06 |
| 06 | `Individual Contact Note.txt` | Individual Contact Note | "Contact Note," "Individual Contact Note" | Clean internally; overlaps heavily with #05 |
| 07 | `Client Daily Log Update.txt` | Client Daily Log Update | "Daily Log" | Unexplained "(CU)" prefix on 6+ fields; internal field duplication (hygiene, follow-through) |
| 08 | `Client Noteworthy Update.txt` | Client Noteworthy Update | "Noteworthy Report," "Noteworthy Update" | No escalation rule to Incident Report anywhere in the fields |
| 09 | `incident-report.txt` | Incident Report Requirements | "Incident Report," "Client Incident Report" | **Confirmed incomplete — ends after Section 2 (Facility Info); no narrative, no timestamps, no sign-off** |
| 10 | `Emergency Preparedness Plan.txt` | Emergency Preparedness Plan | "Emergency Preparedness," "Emergency Preparedness Documentation" | Clean — most structurally complete file in the set |
| 11 | `behavior-tracker.html` | Behavior Tracker Form | "Behaviour Tracker" | **Confirmed hardcoded $20 cap / 25% bonus**; "Medication Taken" column has no link to MAR; no real persistence (client-side only) |
| 12 | `mar-sheet.html` | Medication Administration Record | "MAR Sheet" | Medication list is session-only (not pulled from client record); has working ±1hr lateness check; has PDF export |
| 13 | `medication-administration-record.html` | Medication Administration Record | "Medication Administration Record (MAR)" | **Near-duplicate of #12, NOT identical** — different color scheme, "Supportive Living" spelling, no PDF export |
| 14 | `shift-checklist.html` | Shift Checklist | "Shift Checklist" | **Discovery doc's "no tasks listed" claim is REFUTED — file has full 19/20/15-task lists per shift.** Tasks are fixed, not program-specific |
| 15 | `sharp-count.html` | Monthly Sharp Count Checklist | "Sharp Count Checklist," "Monthly Sharp Count Checklist" | **Confirmed — all program sharp-type presets are empty arrays**; no two-person verification field; no discrepancy alert logic |
| 16 | `mileage-form.html` | Personal Mileage Form | "Personal Mileage," "Mileage Form" | Hardcoded $0.50/km rate (new finding, not in Open Issues); **Program list diverges sharply from every other form** (adds Community Inclusion/Respite/Day Program/Community Support/Youth Support, omits Mental Health Unit) |
| 17 | `grocery-list.html` | NextGen Support Services – Grocery List | "Grocery List" | Uses a third Program-name spelling ("Supportive Independent Living"); locking implemented differently (CSS-only) than every other form |
| 18 | `activity-calendar.html` | Monthly Activity | "Activity Calendar" | **Byte-for-byte identical to #19 (index.html)** — confirmed via `diff`. On-page title "Monthly Activity" conflicts with filename "activity-calendar" |
| 19 | `index.html` | Monthly Activity | "Monthly Activity form" | **Byte-for-byte identical to #18** — one form, two filenames, not two competing versions |

## Cross-cutting finding: "Program" dropdown has at least 4 incompatible variants across the 19 files

No two forms in this set use the exact same Program option list/spelling. Confirmed variants of the second option alone:
- **"Supported Independent Living"** — `activity-calendar.html`/`index.html`, `behavior-tracker.html`, `mar-sheet.html`, `sharp-count.html` (displayed text; internal JS value `supportiveLiving`), `shift-checklist.html`, `mileage-form.html`
- **"Supportive Independent Living"** — `grocery-list.html` (a third spelling, distinct from both of the above)
- **"Supportive Living"** — `medication-administration-record.html`
- **A structurally different list entirely** — `mileage-form.html`'s full list is Group Home / Supported Independent Living / Family Reunification / **Community Inclusion / Respite / Day Program / Community Support / Youth Support** / Other — five options that appear on no other form, and it's missing "Mental Health Unit," which every other form includes.

This is a real, file-verifiable inconsistency independent of anything the discovery doc flagged, and should go into the glossary/entity-model work as a "Program" canonicalization item.

## Forms named in other documents but not present in this 19-file set
- **Discharge Form / Discharge Checklist** — described in detail in `NextGen_Portal_Discovery.txt` (Q5) and referenced as a cross-reference option on Client Noteworthy Update (#08), but no such file was provided.
- **Staff Incident Report** — the discovery doc's Open Issues section says its "complete format and required fields... will be provided separately." Not present here; `incident-report.txt` (#09) is the client-facing Incident Report only.

---

## Recently-Sent Forms (Round 2, post-discovery)

A second batch of 5 forms NextGen sent after the discovery/scope-confirmation conversation. Distinct from the original 19 above — none of these have a direct original-19 predecessor, though several overlap heavily in content. `CLIENT INTAKE FORM.txt` was redrafted by the coordinator's collaborator and already approved by the client; audited factually here the same as the rest — quality review is a separate, later task.

| # | Source file | Canonical form name | Names used elsewhere | Status |
|---|---|---|---|---|
| 20 | `CLIENT INTAKE FORM.txt` | Client Intake Form | — | Consolidates/overlaps Client Information (#01), Intake Screening Tool (#02), and much of Individual Needs Assessment (#03) into one form; contains two internally inconsistent Program/Service checklists (Section 1 vs. Section 16); "Internal Use Only" admin block appended after signatures |
| 21 | `CLIENT SERVICE AGREEMENT.txt` | Client Service Agreement | — | Wholly new document type (client-facing contract/consent, not internal documentation) — no original-19 equivalent; Sections 11 & 13 list topics with no actual input controls; yet another Program/Service taxonomy variant |
| 22 | `INDIVIDUAL SAFETY PLAN.txt` | Individual Safety Plan | — | Overlaps with Emergency Preparedness Plan (#10) at client- vs. site-level; medication info split across 2 sections; single shared Date field for 4 signatories; Section 8 overlaps heavily with Trip Risk Assessment (#24) |
| 23 | `INDIVIDUAL SUPPORT PLAN.txt` | Individual Support Plan (ISP) | — | Goal-planning structure incompatible with Healing Plan's (#04) Medicine Wheel framework; overlaps with Individual Needs Assessment (#03) and Client Intake Form (#20); explicitly cross-references Individual Safety Plan (#22) — one clean, confirmed link |
| 24 | `TRIP RISK ASSESSMENT.txt` | Trip Risk Assessment & Excursion Plan | — | Wholly new document type, most internally consistent form audited across both rounds; contains a client-authored "Best Practice" note that directly resolves its own scope-vs.-Individual Safety Plan boundary; references an undefined "Behaviour Support Plan" document |

### Cross-cutting finding: Program/Service taxonomy collision now has 5+ incompatible variants
The original-19 audit found 4 incompatible spellings of "Supported Independent Living" plus a divergent Mileage Form list. These 5 new forms add at least 4 MORE distinct Program/Service checklists (Client Intake Form has two different ones internally), none matching each other or the glossary's canonical 5-program list, and several treat "Mental Health Support" and "Behaviour Support" as selectable program-like items — repeating, from the client's own newest material, the exact ambiguity the discovery process was meant to resolve. This is now the single highest-priority item for the open-questions register.

### New undefined document reference
- **"Behaviour Support Plan"** — named in Trip Risk Assessment (#24) Sections 7 & 12. Not the same as "Behaviour Tracker" (#11) by name or apparent purpose. Does not exist among any of the 24 files audited to date. Status unknown — treat as a possible missing form, not a synonym.

### New undefined role
- **"Case Manager" / "Case Manager/Coordinator" / "Assigned Case Manager"** — appears in Client Intake Form (#20), Individual Safety Plan (#22), and Individual Support Plan (#23), alongside "Primary Support Worker." Not present in the discovery doc's org hierarchy (D Q1) under that name. Needs reconciling against existing roles (Program Manager? Intake & Admissions Coordinator? a new role entirely?) before the permission matrix can assign it a scope.
