# Form: Client Case Note

## Source
- File: `Client Case Note.txt` (converted from `.docx`)
- Format: txt (static table, no JS/logic)

## Field / Section Inventory (verbatim)
- Client Name
- Client ID / File Number
- Date of Entry
- Time (From: ___ To: ___)
- Worker Name
- Program / Service Area
- Type of Contact: ☐ In-Person ☐ Phone ☐ Video Call ☐ Email ☐ Home Visit ☐ Group Session ☐ Other: ___
- Presenting Issue / Reason for Contact
- Summary of Contact / Interaction
- Client's Mood / Behaviour / Engagement
- Assessment / Worker's Impressions
- Actions Taken
- Client's Response / Decision / Feedback
- Plan / Next Steps / Recommendations
- Additional Notes / Confidential Concerns (if applicable)
- Worker Signature / Date

## Computed / Derived Fields & Formulas
None.

## Structural Issues Found
None found within this file itself — it is internally complete and consistent (every section present in the schema's `ClientCaseNote` model maps to a field here). The only issue is external: see Cross-References.

## Discovery-Doc Open-Issue Cross-Check
> "The Client Case Note and Individual Contact Note overlap significantly. Decide: merge into one form or clearly differentiate their use cases."
**CONFIRMED as overlap, at the field level.** See `06-individual-contact-note.md` for the side-by-side comparison — 12 of this form's 16 fields have a same-purpose counterpart on the Contact Note (Client Name, Client ID, Date, Time, Worker Name, Type/Purpose of Contact, Presenting Issue, Summary of interaction, Mood/Behaviour observed, Actions Taken, Response/Feedback, Next Steps, Confidential Notes, Signature/Date). The discovery doc's answer resolves this by *function* (Case Note = staff↔external-party communication; Contact Note = client↔external-party contact) rather than by *form structure* — the two forms as they exist today do not encode that distinction anywhere (neither has a field indicating "who was the other party" beyond "Type of Contact").

## Cross-References
- "Type of Contact" checkbox options (In-Person/Phone/Video Call/Email/Home Visit/Group Session/Other) differ from Individual Contact Note's options (In-Person/Phone/Email/Virtual (Video)/Text/Other) — five of seven options differ in wording ("Video Call" vs "Virtual (Video)"), and each form has one option the other lacks (Case Note has "Home Visit"/"Group Session"; Contact Note has "Text").
- "Program / Service Area" here vs. no equivalent field on Contact Note.
- No field on either form indicates who the "other party" is (staff-to-external vs. client-to-external) — the distinction the discovery doc says should exist is not present as data on either form.

## Notes
None beyond the above.
