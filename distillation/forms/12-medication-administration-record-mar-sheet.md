# Form: Medication Administration Record (mar-sheet.html)

## Source
- File: `mar-sheet.html`
- Format: html

## Field / Section Inventory (verbatim)
**Client Information**: Client Name, Date of Birth, Program (select: Group Home / Supported Independent Living / Family Reunification [value="family reunification"] / Youth Program / Mental Health Unit / Other → "Specify other program"), Prescribing Physician

**Medication Details** (repeatable block, one per medication, added via "Add Medication" / "Scan Barcode" / "Scan QR Code"):
- Medication Name (free text)
- Dosage (select: 5mg / 10mg / 25mg / Other → "Specify dosage")
- Route (select: Oral / Topical / Injection / Inhaler / Sublingual / Other → "Specify route")
- Time(s) to Administer
- Start Date
- End Date
- Purpose / Notes

**Medication Administration Entry** (repeatable, "Add Another Entry"):
- Date (defaults to today)
- Time Administered (defaults to now)
- Medication Administered (select, dynamically populated from the Medication Name inputs above)
- Dose Given (select: Full Dose / Half Dose / Other)
- Administered By (Staff)
- Signature
- Comments
- (hidden, appears conditionally) Reason for administration outside scheduled window

**Missed or Refused Dose Record** (repeatable):
- Date, Time, Medication (select, dynamically populated), Reason (select: Refused / Missed / Vomited / Medication Not Available / Other → "Specify other reason"), Staff Action Taken

**Leave of Absence** (repeatable):
- Leave Start Date, Leave Start Time, Return Date, Return Time, Staff Name, Reason for Leave

**Emergency Response (If Applicable)** (repeatable):
- Date & Time of Event, What Happened, Immediate Actions Taken

**Follow-up Contacts** (checkbox list): ☐ Parent/Guardian ☐ Physician ☐ Emergency Services ☐ Supervisor ☐ Medication Error Report Completed ☐ Other: [text]

Buttons: Save, Save & Lock, Export as PDF; plus "Scan Barcode" / "Scan QR Code" / "Stop Scanning" for medication entry.

## Computed / Derived Fields & Formulas
- `updateMedicationDropdowns()`: populates the Medication Administration Entry and Missed Dose selects from whatever has been typed into the Medication Name fields — **the medication list is NOT pre-loaded from any client record or physician order; it only contains whatever the current user has typed into this same form, in this same session.**
- `checkMedicationTime()`: compares the administered date/time against the medication's own "Time(s) to Administer" field; if the difference is **less than -60 or greater than +60 minutes**, shows an inline warning "⚠️ Medication administered outside the 1-hour scheduled window" and reveals a "Reason for administration outside scheduled window" textarea. This is a real, working ±1-hour window check already implemented client-side — no data is sent anywhere, no supervisor/lead is notified, and nothing prevents saving regardless of the flag.
- Barcode/QR scanning: `scanBarcode()` uses a browser `prompt()` (not an actual scanner) to accept comma-separated or JSON text and calls `addMedication()` for each; `scanQRCode()` uses the device camera + `jsQR` library to decode a real QR code, same parsing logic applies. Both ultimately just call `addMedication(text)` — there is no barcode/QR-to-medication-database lookup of any kind.

## Structural Issues Found
- The medication dropdown used at administration time is **not literally empty in the DOM** (it says `--Select--` until populated) — it becomes populated only from data entered earlier in the same form session, never from a client's stored medication profile or a physician's order record.
- The ±1-hour lateness check and "reason for deviation" flow already exist in this file — more built-out than the discovery doc's description implies, though it produces no alert, notification, or Incident Report linkage (matches the discovery doc's request that a medication error "must automatically trigger a system alert... and notify" leadership — that automation does not exist here).
- Dosage options are hardcoded to "5mg / 10mg / 25mg / Other" regardless of which medication was typed in — nonsensical for many real medications (e.g. liquid doses, mg/kg dosing) and not tied to the specific medication selected.

## Discovery-Doc Open-Issue Cross-Check
> "The Medication dropdown on the MAR form is empty. Decide: is medication pre-populated from the client record, or entered fresh each time?"
**PARTIALLY CONFIRMED.** The dropdown is not permanently/statically empty (it self-populates from data typed earlier in the same session) but it is **confirmed to never pull from a client's medication profile or physician's order** — medications are entered fresh, by hand, every time the form is used, exactly the ambiguity the discovery doc is asking to resolve.

> "The MAR Sheet and Medication Administration Record appear to be exact duplicates. Which one is actually used — or are they used for different purposes?"
**REFUTED.** Diffed directly against `medication-administration-record.html` — the files are similar but **not identical**: this file (`mar-sheet.html`) uses an earth-brown (#8B4513) color scheme and includes a working "Export as PDF" button + `html2pdf` script that the other file lacks entirely; the other file uses a blue (#007BFF) color scheme and has "Supportive Living" instead of this file's "Supported Independent Living" as a Program option. See `13-medication-administration-record-alt.md` for the complementary write-up.

## Cross-References
- "Medication Taken" column on Behavior Tracker overlaps conceptually but has zero data linkage to this form.
- "Follow-up Contacts" checklist here overlaps with `MEDICATION_FOLLOW_UP_CONTACT_PERSON` enum in the existing schema.

## Notes
This is the most functionally sophisticated file in the entire 19-file set (barcode/QR scanning UI, dynamic dropdowns, time-window validation) despite still being a static, non-persistent client-side mockup with no backend.
