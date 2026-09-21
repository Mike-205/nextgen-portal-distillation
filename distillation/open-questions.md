# Open Questions & Decisions Register

This is the artifact that actually gets sent back to NextGen. Every entry is a direct question, with why it matters and where the ambiguity/contradiction/gap comes from. Nothing here gets resolved by us guessing — each stays open until the client (or an internal decision-maker, where noted) answers it. This is a **living document** — the entity model, permission matrix, lifecycle, and cross-cutting-concerns work still to come will surface more; append rather than rewrite.

Tags: **UNANSWERED** (asked, never really answered), **CONTRADICTED** (two client-provided sources disagree), **MISSING MATERIAL** (a referenced document/list doesn't exist yet), **NEEDS DECISION** (an internal call, not really the client's to make, but flagged here so it doesn't get decided silently).

---

## Roles & Org Structure

**OQ-01 — Are "Team Lead" and "Supervisor" the same position, or two distinct tiers?**
Tag: CONTRADICTED (low confidence). Discovery almost always writes "Team Lead/Supervisor" as one combined actor, and the org chart lists them on one line too ("Team Leaders / Supervisors"). But several answers describe "Supervisor/Coordinator" doing things (reviewing, approving, filing) without ever separately describing what a "Team Lead" alone does. **Ask:** Are these one role with two interchangeable titles, or two tiers with different scope (e.g., Team Lead handles daily shift-level oversight, Supervisor has broader program-level authority)? This gates the permission matrix — right now we can't tell if they get identical access or not.

**OQ-02 — Is "Director of Operations" the same role as "Program Director" and "Director of Programs & Operations"?**
Tag: CONTRADICTED (low confidence). The org chart names one position, "Director of Programs & Operations." Most answers shorten this to "Director of Operations." A few (e.g., the clinical-documents approval table) instead name "Program Director" as the approver. **Ask:** confirm these all refer to the same single position.

**OQ-17 — Is "Program Manager" a distinct title from Team Lead, Supervisor, or Director of Operations?**
Tag: UNANSWERED (new). Surfaced via client call while resolving OQ-03: client said "team leads or program managers will act as internal case managers," naming "Program Manager" as a title never seen elsewhere in the org chart or discovery doc. **Ask:** is this a distinct tier, a synonym for one of the existing titles (Team Lead? Supervisor? Program Director, per OQ-02?), or informal phrasing on the call that shouldn't be read too literally? Feeds directly into OQ-01/OQ-02 and the permission matrix's role axis.

---

**OQ-03 — What is the "Case Manager" role?** — **RESOLVED (2026-09-21, client call).**
Client clarified: "Case Manager," "Case Worker," and "legal guardian" are effectively the same external role in practice. When a family is not functioning (drug abuse, neglect, abuse) and the government removes children from parental care through the courts, the children are assigned to a Children and Family Services employee who acts and makes decisions in the parents' place. In other cases the parent retains guardian status and continues to function as parent/guardian. Client's explicit instruction: **use "Case Worker" as the standard term**, for clarity to others reading the material. Internally, if "Case Manager" is used at all, it maps to **Team Lead or Program Manager acting in that capacity** — not a distinct standalone role.
Entity-model implication: a Client needs two distinct external-party relationship concepts, not one — **Parent/Guardian** and **Case Worker** — since custody status determines which (or both, historically) applies. Carry into item 4.
New sub-question surfaced by this answer, registered separately below: **OQ-17** ("Program Manager" as a title not previously seen in the org chart).

---

## Programs & Services

**OQ-04 — Does "Mental Health Unit" refer to a Program, or a Site?** — **RESOLVED (2026-09-21, client call).**
Mental Health as a standalone program was scrapped entirely — it is neither a Program nor a Site, and not even a listed subservice. It's implicitly present inside other services (e.g., Respite Care may involve mental-health-related support) without ever being named as an explicit, separately-offered service. Action: any surviving "Mental Health Unit" preset (Sharp Count Checklist) is stale and should not be carried forward into the redesign.

**OQ-05 — Can a client be placed in more than one Program/Service at once?** — **RESOLVED (2026-09-21, client call).**
Confirmed single: a client has exactly one primary/main service. Other services that facilitate the main service (e.g. Respite Care as primary, with Transportation to medical appointments as a secondary service supporting it) are billed inclusively under the main service — the secondary services the client actually needs are what drive the extra billing, not a second concurrent placement. Entity-model implication: `Placement` stays single-active; add a "Secondary/facilitating service" concept tied to the active Placement for billing purposes, not a second Placement. The Client Intake Form's multi-select at §13 resolves down to one primary placement plus these billing-relevant secondary services.

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

**OQ-13 — Who assigns the new "Client ID" field, and how?** — **RESOLVED (2026-09-21, client call).**
Not a portal/dev-generated ID. It refers to an identifier already issued to the client by the referring government body or community agency (e.g., an Alberta Children's Services file/case number) before they ever reach NextGen — the Intake Form field *captures* that pre-existing external ID, it doesn't create one. Entity-model implication: `Client` needs a distinct **External/Referral Client ID** field (format TBD by research, likely optional since some clients may be self- or family-referred with no such ID) separate from whatever internal system key the portal generates for its own record-keeping — the two are not the same thing and shouldn't be conflated. Research into Alberta's actual ID conventions is in progress (see `distillation/legal-context-research.md`, once written).

---

## Compliance, Privacy & Retention

**OQ-14 — What is the actual required client-record retention period?**
Tag: UNANSWERED. Discovery's answer offered "a recommended organizational standard" of 7 years post-discharge but explicitly said the real number "should be confirmed" against NextGen's specific licensing, funding, and contractual obligations. That confirmation never happened. This is a compliance number we cannot invent.

**OQ-15 — Has Indigenous community/Nation consultation on data handling actually happened, or is it still to be scheduled?**
Tag: UNANSWERED. Discovery's answer described what such consultation *should* cover — it never actually confirmed whether NextGen has done it, is doing it, or with whom.

---

## Shift Handover

**OQ-16 — How does the outgoing staff member communicate critical information to the incoming one — verbal, written log, or both?** — **RESOLVED (2026-09-21, client call), with a caveat.**
Client's answer: the existing Daily Log's "(CU) Follow Through (notes)" field (confirmed present in the source form, `distillation/forms/07-client-daily-log-update.md`) can serve as the shift-handover mechanism — written, not a separate document. Important distinction the client's own phrasing blurs: this lives in the **Daily Log**, not the **Shift Checklist** (F14, a different existing document) — there is no separate "Shift Log."
**Our assessment, not yet client-confirmed:** reusing Follow Through Notes for handover content is reasonable and avoids a redundant field. What isn't settled is the *workflow* around it — a chronological narrative field is fine for record-keeping, but a genuine handover often needs the incoming staff member to actually see and act on it, not just have it exist in the log. Whether Follow Through Notes needs an explicit "read/acknowledged by incoming staff" step, or a plain written note is sufficient in practice, is a **new open item for the alert/escalation matrix (item 7)**, not decided here.

---

## Log of items resolved since this register was started (for traceability, not action)

- Programs/Services count: 5 → 6, plus the Program→Subservice model (confirmed by direct client conversation, see `glossary.md`).
- Case Note vs. Individual Contact Note distinction (resolved via Scope Memo).
- MAR naming (resolved via Scope Memo — title stays "Medication Administration Record (MAR)"; note the memo's claim that the two source files were identical was itself refuted by the forms audit, but the naming decision stands independent of that).
- "(CU)" prefix meaning (resolved: "Client Update," drop the abbreviation in the UI).
- **2026-09-21 batch, via client call:** OQ-03 (Case Manager = Case Worker = legal guardian, externally; internally maps to Team Lead/Program Manager), OQ-04 (Mental Health Unit scrapped, not a Program/Site/subservice), OQ-05 (single active Placement confirmed; other services bill inclusively as secondary/facilitating), OQ-13 (Client ID = externally-issued referral ID, not portal-generated), OQ-16 (handover = Daily Log's Follow Through Notes field, not a separate Shift Log — see caveat left in place at OQ-16 on the acknowledgment-workflow question). New item opened as a result: OQ-17 ("Program Manager" title needs reconciling with OQ-01/OQ-02).
