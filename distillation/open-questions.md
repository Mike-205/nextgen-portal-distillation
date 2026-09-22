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

**OQ-21 — Does the portal need to record *which* court order type applies to a client (Supervision / Temporary Guardianship / Permanent Guardianship / Custody Agreement), or is "Parent/Guardian" vs. "Case Worker" enough?**
Tag: UNANSWERED (new, from `legal-context-research.md` §1). A caseworker's actual authority genuinely differs by order type — under a Permanent Guardianship Order the Director is the child's sole guardian; under a Supervision Order the parent retains full authority and the caseworker's role is supportive/monitoring only. **Ask:** does NextGen need order-type granularity to correctly determine who can authorize what (e.g., consent to treatment, receive records), or is the simpler Parent/Guardian-vs-Case-Worker split sufficient for NextGen's own purposes? This is a scope call for the entity model and permission matrix, not something public research can answer.

**OQ-22 — Do referrals ever come through a Delegated First Nations Agency (DFNA) rather than the provincial ministry directly, and if so, do DFNA caseworkers use different title conventions?**
Tag: UNANSWERED (new, from `legal-context-research.md` §1). Alberta delivers child intervention services both directly and through 19 Delegated First Nations Agencies. **Ask:** does NextGen receive referrals via a DFNA, and if so, should "Case Worker" cover that relationship identically, or does it need a different label/handling?

---

**OQ-03 — What is the "Case Manager" role?** — **RESOLVED (2026-09-21, client call).**
Client clarified: "Case Manager," "Case Worker," and "legal guardian" are effectively the same external role in practice. When a family is not functioning (drug abuse, neglect, abuse) and the government removes children from parental care through the courts, the children are assigned to a Children and Family Services employee who acts and makes decisions in the parents' place. In other cases the parent retains guardian status and continues to function as parent/guardian. Client's explicit instruction: **use "Case Worker" as the standard term**, for clarity to others reading the material. Internally, if "Case Manager" is used at all, it maps to **Team Lead or Program Manager acting in that capacity** — not a distinct standalone role.
Entity-model implication: a Client needs two distinct external-party relationship concepts, not one — **Parent/Guardian** and **Case Worker** — since custody status determines which (or both, historically) applies. Carry into item 4.
New sub-question surfaced by this answer, registered separately below: **OQ-17** ("Program Manager" as a title not previously seen in the org chart).
**Research completed** (`distillation/legal-context-research.md`, §1): "Case Worker" is well-supported as the plain-language term NextGen should use (matches Alberta.ca's own public-facing "caseworker" and the formal job title "Child Intervention Caseworker"). But the research surfaced a real nuance: a Case Worker's actual decision-making authority differs by which court order is in place (Supervision Order / Temporary Guardianship Order / Permanent Guardianship Order / Custody Agreement) — under a PGO the Director is the child's sole guardian; under lighter orders the parent retains real authority and the caseworker's role is supportive. See **OQ-21** below for whether the portal needs to capture this granularity.

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
Not a portal/dev-generated ID. It refers to an identifier already issued to the client by the referring government body or community agency (e.g., an Alberta Children and Family Services file/case number — note: this ministry was renamed from "Children's Services" in 2023; use the current name going forward) before they ever reach NextGen — the Intake Form field *captures* that pre-existing external ID, it doesn't create one. Entity-model implication: `Client` needs a distinct **External/Referral Client ID** field (format TBD by research, likely optional since some clients may be self- or family-referred with no such ID) separate from whatever internal system key the portal generates for its own record-keeping — the two are not the same thing and shouldn't be conflated.
**Research completed** (`distillation/legal-context-research.md`, §2): no referring body (Children and Family Services, FSCD, PDD, AISH, Jordan's Principle) publishes a standard ID format, and formats/presence vary heterogeneously by source — there's no evidence of one shared, portable identifier scheme. See **OQ-23** below for the resulting field-structure call.

**OQ-23 — Should the entity model use one generic "External Referral ID" field (paired with a "Referral Source" field for context), or separate fields per referring body?**
Tag: NEEDS DECISION (internal call, flagged so it isn't decided silently). Research found referral IDs are heterogeneous in format and inconsistently present depending on the source (Children and Family Services, FSCD, PDD, AISH, Jordan's Principle, DFNA, or none at all for self-/family-referrals) — no evidence of a shared format across sources. Leaning: one generic field + a paired "Referral Source" field is more realistic than per-agency fields, since sources vary too much to standardize sub-fields per agency. This is a modelling judgment for whoever builds the entity model (item 4), not a client question — flagged here for visibility, not to be silently decided without noting it.
**Also worth asking the client directly (not resolvable from public sources):** which referral sources actually hand over a written ID at intake in practice, versus which almost never do — this affects whether the field should be treated as commonly populated or a rare edge case.

---

## Compliance, Privacy & Retention

**OQ-14 — What is the actual required client-record retention period?**
Tag: UNANSWERED. Discovery's answer offered "a recommended organizational standard" of 7 years post-discharge but explicitly said the real number "should be confirmed" against NextGen's specific licensing, funding, and contractual obligations. That confirmation never happened. This is a compliance number we cannot invent. **Research checked** (`legal-context-research.md` §3): no public source gives a NextGen-specific mandated figure — remains genuinely open, unresolved by research, needs the client directly.

**OQ-15 — Has Indigenous community/Nation consultation on data handling actually happened, or is it still to be scheduled?**
Tag: UNANSWERED. Discovery's answer described what such consultation *should* cover — it never actually confirmed whether NextGen has done it, is doing it, or with whom. **Research adds a nuance** (`legal-context-research.md` §3): OCAP (Ownership, Control, Access, Possession) is specifically a **First Nations** framework (stewarded by the First Nations Information Governance Centre) — it is not a universal Indigenous-data standard. Métis and Inuit data governance are separate and, for Métis, still emerging (distinct *Métis Health Research and Data Governance Principles*, not identical to OCAP). Since NextGen's clients are described as "Indigenous and marginalized" broadly, not First Nations-only, **"has consultation happened" isn't the whole question — "which framework, negotiated with which specific community, for which clients" is a second, equally open dimension.** Do not let a single "we follow OCAP" statement stand in for the Métis/Inuit side of this.

**OQ-18 — Does NextGen's incorporation structure put it fully under Alberta's PIPA, or only for its commercial activities?**
Tag: NEEDS DECISION / needs counsel. Research (`legal-context-research.md` §3): some non-profit structures (trade unions, condo boards, school councils, churches) are subject to PIPA in full by virtue of incorporation type; others only for commercial activities (accepting donations doesn't count as commercial). Confirmed as the applicable statute either way (PIPEDA is a backstop; the old FOIP was repealed June 2025 and replaced by ATIA/POPA, which govern public bodies — NextGen is not a public body). **Ask:** this is a fact about NextGen's own corporate structure only NextGen's counsel can confirm.

**OQ-19 — Are NextGen's Medication Administration Records governed by Alberta's Health Information Act (as an HIA "affiliate"), or by PIPA?**
Tag: NEEDS DECISION / needs counsel. Research (`legal-context-research.md` §3, flagged as inference only — direct sourcing on this point repeatedly failed) leans toward PIPA, since HIA's "custodian" list is built around licensed health-sector entities (health authorities, pharmacies, licensed care facilities) rather than social-service non-profits — but this needs a direct legal read of the Health Information Regulation's custodian list against NextGen's actual service model, not an inference from public search.

**OQ-20 — Do any of NextGen's funding agreements contain explicit Canadian-data-residency clauses?**
Tag: UNANSWERED. Research (`legal-context-research.md` §3): there's no single blanket Canadian law requiring all personal data to stay in Canada — residency requirements come from specific contract clauses. Given NextGen is government/program-funded, its actual contracts may impose this; that's a contract-review question only the client can answer, not something general law settles.

---

## Shift Handover

**OQ-16 — How does the outgoing staff member communicate critical information to the incoming one — verbal, written log, or both?** — **CORRECTED, 2026-09-22. Original 2026-09-21 resolution below was wrong; kept for traceability, not to be treated as current.**

~~Original 2026-09-21 resolution (superseded):~~ ~~Client's answer: the existing Daily Log's "(CU) Follow Through (notes)" field can serve as the shift-handover mechanism — written, not a separate document.~~ This missed something: the discovery doc independently and repeatedly (all three shift walkthroughs, plus the dedicated shift-start Q&A — 4 separate mentions) describes a **"staff communication log"** as a distinct step, always in this order: (1) verbal shift exchange, (2) **review the staff communication log** for important updates, (3) *then* review client documentation including Daily Logs. That's three separate things, not one. When this was put back to the client as a live tension (Daily Log vs. a possible separate Shift Log), the client confirmed a Shift Log is real and distinct — see below.

**Client's actual answer (2026-09-22), to three follow-up questions:**
1. **Scope:** the Shift Log is **per-Client** (one per individual client, not one shared log for the whole house/site).
2. **Existing material:** there is **no existing version of it** (paper or otherwise) — it needs to be **designed from scratch**. Client's own words: it "will serve similar to daily log in some way."
3. **Relationship to the Shift Checklist:** the Shift Log is a **different thing** — it does **not** replace the Shift Checklist's (F14) "Shift Exchange To Be Completed Upon/Before Departure" checkboxes. Both exist; the checklist's checkboxes remain a pure confirmation gate with no content field of their own.

Tag: MISSING MATERIAL (like the Staff Incident Report template, Discharge Form, and Behaviour Support Plan — a real document NextGen uses in some form but never provided/formalized).

**New question this raises, registered as OQ-24 below:** the client's own phrase — "it will serve similar to daily log in some way" — combined with Shift Log being per-Client (same scope as Daily Log) means we do not yet know what actually distinguishes Shift Log content from Daily Log content. Without that distinction, this risks becoming exactly the kind of duplicate-with-no-stated-difference pattern already found elsewhere in the source forms (e.g. Daily Log's own "Hygiene During Shift" vs. "Completed Hygiene Routines," or "Incidents and/or Follow Through" vs. "Follow Through (notes)" — see `distillation/forms/07-client-daily-log-update.md`). Needs a direct answer before the entity model can treat these as two genuinely separate document types.

**OQ-24 — What should the Shift Log actually capture that the Daily Log doesn't (or vice versa)?**
Tag: UNANSWERED (new, 2026-09-22). **Ask:** is the Shift Log meant to be the short, operational, forward-looking handover note (what the next staff member needs to know or do) while the Daily Log stays the fuller narrative record of the day/shift's activities (hygiene, meals, programming, health, behaviour)? Or is the Shift Log meant to eventually replace the Daily Log's role for per-shift documentation, with "Daily Log" becoming something else (e.g. a rolled-up daily summary)? Since NextGen said this is being designed from scratch, this is also a chance to ask directly what fields/sections they'd actually want on it, rather than us guessing between these framings.

---

## Log of items resolved since this register was started (for traceability, not action)

- Programs/Services count: 5 → 6, plus the Program→Subservice model (confirmed by direct client conversation, see `glossary.md`).
- Case Note vs. Individual Contact Note distinction (resolved via Scope Memo).
- MAR naming (resolved via Scope Memo — title stays "Medication Administration Record (MAR)"; note the memo's claim that the two source files were identical was itself refuted by the forms audit, but the naming decision stands independent of that).
- "(CU)" prefix meaning (resolved: "Client Update," drop the abbreviation in the UI).
- **2026-09-21 batch, via client call:** OQ-03 (Case Manager = Case Worker = legal guardian, externally; internally maps to Team Lead/Program Manager), OQ-04 (Mental Health Unit scrapped, not a Program/Site/subservice), OQ-05 (single active Placement confirmed; other services bill inclusively as secondary/facilitating), OQ-13 (Client ID = externally-issued referral ID, not portal-generated), OQ-16 (**initially** resolved as "handover = Daily Log's Follow Through Notes field" — **corrected 2026-09-22, see below**). New item opened as a result: OQ-17 ("Program Manager" title needs reconciling with OQ-01/OQ-02).
- **2026-09-22, via client call:** OQ-16 corrected — the discovery doc's own "staff communication log" (mentioned 4× independently) was missed on the first pass. Client confirmed a genuinely separate **Shift Log** exists in concept: per-Client, designed from scratch (no prior version), does not replace the Shift Checklist's exchange checkboxes. Opened **OQ-24** (what distinguishes Shift Log content from Daily Log content) since both are now per-Client and the client described them as "similar in some way."
- **2026-09-21, `distillation/legal-context-research.md` (background research, not a client answer):** corrected ministry name to "Children and Family Services" throughout (renamed from "Children's Services" in 2023). Added nuance to OQ-03 (caseworker authority varies by court order type) and OQ-15 (OCAP is First-Nations-specific, not universal — Métis/Inuit governance is separate). Opened six new items: OQ-18–OQ-20 (PIPA coverage bucket, HIA custodian status, funding-agreement residency clauses — all need counsel/client), OQ-21–OQ-22 (order-type granularity, DFNA referral title conventions), OQ-23 (Client ID field structure — internal modelling call, NEEDS DECISION).
