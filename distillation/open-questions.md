# Open Questions & Decisions Register

This is the artifact that actually gets sent back to NextGen. Every entry is a direct question, with why it matters and where the ambiguity/contradiction/gap comes from. Nothing here gets resolved by us guessing — each stays open until the client (or an internal decision-maker, where noted) answers it. This is a **living document** — the entity model, permission matrix, lifecycle, and cross-cutting-concerns work still to come will surface more; append rather than rewrite.

Tags: **UNANSWERED** (asked, never really answered), **CONTRADICTED** (two client-provided sources disagree), **MISSING MATERIAL** (a referenced document/list doesn't exist yet), **NEEDS DECISION** (an internal call, not really the client's to make, but flagged here so it doesn't get decided silently).

---

## Roles & Org Structure

**OQ-01 — Are "Team Lead" and "Supervisor" the same position, or two distinct tiers?**
Tag: CONTRADICTED (low confidence). Discovery almost always writes "Team Lead/Supervisor" as one combined actor, and the org chart lists them on one line too ("Team Leaders / Supervisors"). But several answers describe "Supervisor/Coordinator" doing things (reviewing, approving, filing) without ever separately describing what a "Team Lead" alone does. **Ask:** Are these one role with two interchangeable titles, or two tiers with different scope (e.g., Team Lead handles daily shift-level oversight, Supervisor has broader program-level authority)? This gates the permission matrix — right now we can't tell if they get identical access or not.

**OQ-02 — Is "Director of Operations" the same role as "Program Director" and "Director of Programs & Operations"?**
Tag: CONTRADICTED (low confidence). The org chart names one position, "Director of Programs & Operations." Most answers shorten this to "Director of Operations." A few (e.g., the clinical-documents approval table) instead name "Program Director" as the approver. **Ask:** confirm these all refer to the same single position.

**OQ-03 — What is the "Case Manager" role?**
Tag: MISSING MATERIAL. Referenced three times across the recently-sent forms (Individual Support Plan, Individual Safety Plan, Trip Risk Assessment) but does not appear anywhere in the organizational hierarchy given during discovery. **Ask:** is this a new role, a renamed existing one (Program Manager? Supervisor?), or an external party's role (like the funding-agency "case worker" the Intake Form separately references)?

---

## Programs & Services

**OQ-04 — Does "Mental Health Unit" refer to a Program, or a Site?**
Tag: CONTRADICTED. Discovery confirmed Mental Health is a cross-program service component, not one of the six Programs/Services — yet the Sharp Count Checklist form still lists "Mental Health Unit" as a selectable program, and it's a real value in `next_gen_services`'s existing `PROGRAMS` enum. **Ask:** should "Mental Health Unit" be removed as an option entirely, or does it actually name a specific Site (e.g., a Group Care site with a mental-health focus) rather than a Program?

**OQ-05 — Can a client be placed in more than one Program/Service at once?**
Tag: CONTRADICTED. Discovery (Q7) confirmed a client is assigned to exactly one primary program at a time, with transitions being sequential, never concurrent. But the redesigned, client-approved Client Intake Form (§13 "Service Requested") lets a client select multiple services and subservices. **Ask:** does requesting multiple services at intake result in one primary placement being chosen afterward, or has the single-placement rule actually changed? This directly decides whether "Placement" in the entity model is single-active or can be concurrent.

**OQ-06 — Does the Monthly Activity Report survive?**
Tag: CONTRADICTED. The Scope Confirmation Memo says "remove the Monthly Activity Form." The discovery doc's own shift-workflow walkthrough (Q2) still describes front-line staff completing a "Monthly Activity Report" as live documentation. Also note: the forms audit confirmed `activity-calendar.html` and `index.html` are byte-identical — there was only ever one file here, not two competing duplicates, so "which one do we keep" was the wrong framing from the start. **Ask:** is this document in or out, full stop?

---

## Documents & Forms — Missing or Incomplete

**OQ-07 — What should the portal's own Incident Report actually capture, beyond the attached government form?**
Tag: MISSING MATERIAL. The client-facing Incident Report file only contains Sections 1–2 (Child/Youth Info, Facility Info) — no narrative section, no timestamps, no notification log, no sign-off block exist anywhere in the file. The memo's fix is to let staff attach the official Government of Alberta incident form. **Ask:** should the portal also capture a structured internal narrative/timeline (what happened, actions taken, who was notified, when) independent of the attached PDF, or is all of that deferred entirely to the attached government form?

**OQ-08 — Is the Staff Incident Report template finalized yet?**
Tag: MISSING MATERIAL. Discovery said this template "will be provided separately." We don't have it. Blocks scoping that module.

**OQ-09 — Does a Discharge Form/Checklist already exist, or does it need to be designed from scratch?**
Tag: MISSING MATERIAL. Discovery describes both in detail (Q5: required fields, a full checklist), but no such file exists among the 24 forms audited. **Ask:** is there a paper version we haven't seen, or do we design it fresh from the discovery description?

**OQ-10 — What is the "Behaviour Support Plan" referenced in the Trip Risk Assessment?**
Tag: MISSING MATERIAL. Doesn't exist anywhere across all 24 form files audited. **Ask:** is this a real, separate NextGen document not included in either batch, or does it refer to something already covered under a different name (Behaviour Tracker, Healing Plan's behavioural goal area)?

**OQ-11 — Are the Sharp Count and Shift Checklist task/preset lists ready for the other four Programs/Services?**
Tag: MISSING MATERIAL. Discovery only ever provided task lists / sharp-type presets for Group Home and SIL, and its own Open Issues section says lists for Family Reunification and Youth Program "must still be developed." Now that we've confirmed six Programs/Services (not five, and not the same five), this also needs a Training & Consultation Services list. **Ask:** can NextGen provide these, or do we need to draft them and get sign-off?

**OQ-12 — Confirm all four Medicine Wheel goal areas belong in the Healing Plan.**
Tag: NEEDS DECISION (but easy — just confirm). The source form has Spiritual, Mental, Emotional, and Physical Wellbeing. The previously built schema silently dropped Emotional Wellbeing. Low-risk to just confirm and fix, flagging here so it's not silently re-dropped in the new design either.

---

## Client Records & Identity

**OQ-13 — Who assigns the new "Client ID" field, and how?**
Tag: UNANSWERED. Discovery said clients are currently identified by name only, with a vague note that a unique ID "would improve record management" (the answer trails off without confirming a scheme). The redesigned Intake Form now has a "Client ID" field under "Office use only." **Ask:** auto-generated by the portal, manually assigned by intake staff under an existing numbering convention, or something we need to design?

---

## Compliance, Privacy & Retention

**OQ-14 — What is the actual required client-record retention period?**
Tag: UNANSWERED. Discovery's answer offered "a recommended organizational standard" of 7 years post-discharge but explicitly said the real number "should be confirmed" against NextGen's specific licensing, funding, and contractual obligations. That confirmation never happened. This is a compliance number we cannot invent.

**OQ-15 — Has Indigenous community/Nation consultation on data handling actually happened, or is it still to be scheduled?**
Tag: UNANSWERED. Discovery's answer described what such consultation *should* cover — it never actually confirmed whether NextGen has done it, is doing it, or with whom.

---

## Shift Handover

**OQ-16 — How does the outgoing staff member communicate critical information to the incoming one — verbal, written log, or both?**
Tag: UNANSWERED. Asked directly in discovery (Q15); the answer field was left blank.

---

## Log of items resolved since this register was started (for traceability, not action)

- Programs/Services count: 5 → 6, plus the Program→Subservice model (confirmed by direct client conversation, see `glossary.md`).
- Case Note vs. Individual Contact Note distinction (resolved via Scope Memo).
- MAR naming (resolved via Scope Memo — title stays "Medication Administration Record (MAR)"; note the memo's claim that the two source files were identical was itself refuted by the forms audit, but the naming decision stands independent of that).
- "(CU)" prefix meaning (resolved: "Client Update," drop the abbreviation in the UI).
