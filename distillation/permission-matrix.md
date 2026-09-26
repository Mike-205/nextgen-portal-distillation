# Permission Matrix (Item 5)

Role × Document × Action × Scope, collapsed from the discovery doc's several inconsistent versions of this (Q2's front-line/supervisor tables, Q3's client-file/MAR/incident/financial tables, Q5's intake–acceptance–discharge tables, Q10's medication tables, Q13's lock/approve/unlock tables, Q14's sharp-count table, and Additional System Requirements §5/§6) into one canonical structure.

**Evidence base:** `distillation/research/permission-matrix-input-discovery.md` (full transcription of every discovery-doc permission statement, with exact line numbers, plus a contradictions list, an orphan-role-label list, and a document-coverage-gap list — read that file for sourcing on any claim below). Also: `entity-model.md`'s Staff section (Hierarchy Tier / Functional Group / Engagement Type axes, per-title table), `glossary.md`'s Lock/Approve/Unlock entries, and forms 20–24's signature blocks.

**Provenance caveat (applies to nearly everything below):** almost every table transcribed from the discovery doc sits under a header literally reading "Recommended System Permission Structure" or "Recommended Permission Structure" — this is vendor-voice **PROPOSED** design language, not the client's confirmed current practice, and (per the register's standing methodological caveat) NextGen has zero active clients, so there is no tested practice to confirm against yet regardless. Only the **Category axis system itself** (Hierarchy Tier / Functional Group / Engagement Type, and the specific per-title placements in `entity-model.md`) carries the CLIENT/COLLABORATOR provenance already established there — this matrix inherits that provenance rather than re-arguing it. Where this artifact makes its own collapse decision (resolving one of the doc's internal contradictions by picking a reading), that's called out explicitly as a **collapse decision**, distinct from a client-confirmed fact.

**Scope boundary (per `entity-model.md`'s own boundary note, restated here):** this artifact defines who may act on a document and under what document-type/scope conditions. It does **not** define alert trigger conditions or escalation timing (item 7), retention periods (item 7), consent/disclosure policy (item 7), or lifecycle-transition decisions like accept/decline/discharge (item 6) — only the *document-approval* facts embedded in those workflows are captured here, per the advisor's guidance on this boundary.

---

## 1. Axis recap (defined in full elsewhere — not redefined here)

- **Hierarchy Tier** and **Functional Group** and **Engagement Type** — see `entity-model.md`'s Staff section and `glossary.md`'s "Staff Title vs. Category" entry for the full definitions, values, and per-title mapping. This matrix uses Hierarchy Tier as its primary approval-chain axis and Functional Group as its document-authorship gate, consistent with the collaborator's confirmation that Functional Group is what gates document authorship/view access while Tier gates approval/escalation authority (`entity-model.md` §4).
- **Direct Care Hierarchy Tier chain** (the chain most of this matrix runs on, since most of the 22 document types are client-care documents): **Front-Line/Support Staff → Team Lead → Supervisor → Program Manager → Director of Operations → Executive Director.** Program Manager and the five senior/functional managers (Clinical Services, HR & Admin, Finance & Corporate, QI & Compliance, Community Partnerships & Outreach) sit at the same rank, one level below Director of Operations, but in different Functional Groups.
- **Individual Contributor / Specialist** tier (the seven Clinical Professional titles, most individual-contributor Administrative & Compliance titles, Indigenous Cultural Coordinator) sits outside this chain entirely — no supervisory reports, and (per `entity-model.md`'s own flagged residual) **still an open question whether this tier approves or receives escalations for anything** — see §8 below.

---

## 2. Action vocabulary (canonical — collapses the doc's inconsistent verbs)

| Canonical action | What it means | Source verbs collapsed into it |
|---|---|---|
| **View** | Read-only access to a document's current version | "view-only," "access... for oversight," "review" (when not paired with a required sign-off) |
| **Create/Edit** | Author or amend a document's current, not-yet-locked version | "Create, Edit, Update," "complete," "document" |
| **Lock** | The authoring staff member finalizes their own entry; no longer editable by them (RESOLVED, `glossary.md`) | "Save & Lock," "finalize," "submit" |
| **Review (optional, audit-based)** | A supervisory role reads a locked document and may leave notes, but this is **not** a gate on the document's visibility or a required step (Q3 L620–622; Q13 L1725–1769) | "review," "monitor trends," "verify quality," most of Q2's "approve" language for routine documents — see collapse decision in §5 |
| **Approve (required co-sign)** | A required, blocking sign-off before a document is considered finalized — applies **only** to the five buckets in §5 | "approve/sign-off" (Q2, loosely) narrowed to Q13's five buckets specifically |
| **Escalate** | Forwarding a document/event to a higher tier, typically Program Manager/Director of Operations/Executive Director, per the recurring 4-tier alert ladder (item 7's concern, noted here only where it's a document-approval fact) | "escalate," "notify leadership" |
| **Unlock** | A restricted action creating a new Version while preserving the original (RESOLVED, `glossary.md`) — see §9 | "unlock," "correction," "amendment" |

**Collapse decision — routine vs. required-approval framing (resolves contradiction #6 in the evidence file):** Q2's tables use loose "approve" language for Daily Logs, Case Notes, Shift Checklists, and Behaviour Trackers, but Q13 explicitly places these four in a **routine** bucket ("may be completed and locked by authorized staff, with Supervisor review occurring through regular documentation audits"), and Q3 (L620–622) states directly that **no document requires approval before becoming visible to other authorized users**. This matrix treats **Q13 + Q3 as authoritative** (later, more specific, and internally consistent with each other, whereas Q2's "approve" language isn't load-bearing anywhere else in the document) — Daily Logs, Case Notes, Individual Contact Notes, Noteworthy Updates, Shift Checklists, and Behaviour Trackers get **Review (optional, audit-based)**, not **Approve (required co-sign)**, from Supervisor/Team Lead. This matches how `entity-model.md`'s Lock section already reads the same evidence.

---

## 3. Table — Client File Access Scope by Hierarchy Tier

Collapsed from Q3's "Recommended System Permission Structure" table (L448–463), reconciled against **OQ-33's resolution** that the scope unit is **Site**, not Program (the source table's own text still says "program(s)" in places — read as Site per OQ-33, not re-transcribed literally).

| Hierarchy Tier | Client File Access Scope |
|---|---|
| Front-Line/Support Staff | Clients assigned to their current shift, or within their designated Site/Program assignment — not unassigned clients, not other Programs/Sites unless authorized, not archived records unrelated to current responsibilities |
| Team Lead | Clients within their one assigned Site |
| Supervisor | Clients within their several assigned Sites |
| Program Manager | All clients across their assigned Program (Program-wide, spanning every Site under it) |
| Director of Operations | Organization-wide oversight access |
| Executive Director | Organization-wide oversight access (implied by Q5/Q13's oversight language; not separately tabled from Director of Operations in Q3, but confirmed as the top tier elsewhere) |
| Individual Contributor / Specialist (Clinical, Administrative & Compliance) | Not stated in the source tables at all — **inferred** as scoped to whichever clients/records the role's specific duties require (e.g., a clinician's assigned caseload, a Finance & Payroll Officer's mileage-claim review queue), not a Tier-wide default. Flagged, not resolved — this is the same authorship gap §6 and §8 already document (**OQ-42** for Clinical specifically); there is no separate client-file-scope answer to give until that's resolved. |

**Exceptions and Temporary Access** (Q3, L440–446): staff covering another Program/shift, emergencies, case consultation/QA reviews, and "leadership-approved operational requirements" can all justify additional access beyond the table above — "documented and removed once no longer required." **No named grantor role, approval workflow, or duration exists anywhere in the source material.** This is a real gap, but it's a workflow/lifecycle mechanism, not a static permission fact — carried forward as a note for item 7 (cross-cutting concerns), not modeled as a matrix cell here.

**External users (foster/kinship caregivers, partner agencies) — not modeled in this table at all.** Whether these count as a distinct scoped-access category or are excluded entirely as "family members, guardians, and external contacts" is the live discovery-doc self-contradiction tracked at **OQ-29** (Q1 says they "may be granted portal access... role-based," Q18/Q25 say external parties get no direct access, initial scope "strictly internal staff-facing"). This matrix takes no position on it — every Tier row above assumes an internal NextGen staff member; if OQ-29 resolves toward external access, a new row (or a new Engagement Type value) is needed here, not assumed in advance.

### 3a. First-line supervisory reviewer — resolved by Program type, not a fixed Tier

The discovery doc almost always writes "Team Lead/Supervisor" as one combined actor for first-line review/co-sign duties — the same conflation OQ-01/OQ-33 already resolved as two distinct tiers in general org-chart terms, but never disambiguated for *this specific* approval-chain question (which one actually signs, or do both). **This is now tracked as OQ-47**, and every matrix cell below that would otherwise silently pick one of "Team Lead" or "Supervisor" instead reads **"first-line supervisory reviewer (OQ-47)."**

Layered on top of that unresolved question, the *identity* of the first-line reviewer also depends on which kind of Program the Client/Document belongs to — this part **is** resolved, from existing OQ-33/OQ-36/entity-model.md facts, not newly open:

| Program type | First-line supervisory reviewer | Basis |
|---|---|---|
| Site-based (Group Care Services, SIL, and — not yet explicitly re-confirmed — assumed Site-based) | Team Lead (one Site) and/or Supervisor (several Sites) — **which one, or both, is OQ-47** | OQ-33 |
| Non-Site-based (Family Reunification Support, Respite Care) | **Program Manager directly** — Team Lead/Supervisor layer doesn't exist for these Programs at all | CLIENT (relayed, 2026-09-26): "They report to the program manager, same with respite cos it's not residential as well" — `entity-model.md` Staff Assignment section |
| Program with no Program Manager assigned (currently Transportation, Training & Consultation) | **Director of Operations directly, interim** — and since Transportation has no confirmed Site-based structure either (Driver's own row has no Team Lead/Supervisor), this collapses straight to Director of Operations with no first-line tier in between at all | OQ-36 (CLIENT) |

---

## 4. Table — Document Type × Access (the core matrix)

Every canonical Document type from `entity-model.md` §5, plus the three known-needed-but-not-yet-designed types. **Author** = who has Create/Edit before lock. **Lock** = who triggers it (always the author, per the universal rule — not repeated per row unless different). **Required Approval?** references the bucket number in §5 if applicable, "No (routine)" if not, "N/A" if the document doesn't fit either framework (financial, standing/administrative types) or "Unaddressed" if the source material has no statement at all. **Reviewer/Approver Tier(s)** is populated only where an approval or a named review step exists. **Additional View** lists tiers/groups with view-only access beyond the author.

| Document Type | Author (Create/Edit) | Required Approval? | Reviewer/Approver Tier(s) | Additional View | Notes |
|---|---|---|---|---|---|
| Daily Log | Front-Line/Support Staff | No (routine) — §2 collapse decision | First-line supervisory reviewer (§3a, OQ-47) (audit-based, optional) | Program Manager+ | Per-Placement, per-Shift grain |
| Case Note | Front-Line/Support Staff | No (routine) | First-line supervisory reviewer (§3a, OQ-47) (audit-based) | Program Manager+ | Staff-to-external-party communication (glossary) |
| Individual Contact Note | Front-Line/Support Staff | No (routine) | First-line supervisory reviewer (§3a, OQ-47) (audit-based) | Program Manager+ | Client-to-external-party contact (glossary) |
| Noteworthy Update | Front-Line/Support Staff | No (routine) | First-line supervisory reviewer (§3a, OQ-47) (review, determine follow-up) | Program Manager+ | |
| Shift Checklist | Front-Line/Support Staff | No (routine) | First-line supervisory reviewer (§3a, OQ-47) (verify completion) | Program Manager+ | Locks **per shift-section** (Morning/Afternoon/Night), not once for the whole instance — `entity-model.md` §5 |
| Behaviour Tracker | Front-Line/Support Staff | No (routine), **unless the entry documents a serious behavioural incident, in which case an Incident Report is also required and that Incident Report — a separate Document — falls under Bucket 5 (High-Risk)** — collapse decision, resolves the apparent Behaviour-Tracker/High-Risk-bucket overlap without inventing a second lock state on the same document | Supervisor (monitor patterns) | Program Manager+ | The overlap is resolved by treating the routine tracker and the triggered Incident Report as two separate Document instances, not by escalating the tracker itself |
| Monthly Activity Report | Front-Line/Support Staff | No (routine) | Supervisor (review participation/outcomes) | Program Manager+ | |
| Grocery List | Front-Line/Support Staff | No (routine) | Supervisor ("as needed") | Program Manager+ | No deeper access statement exists in the source (`permission-matrix-input-discovery.md` gap list) |
| Emergency Preparedness Documentation | Front-Line/Support Staff | No (routine) for the completion record itself | Supervisor (review compliance/completion) | Program Manager+ | An actual emergency-response *event* likely triggers Bucket 5 (High-Risk) separately — same overlap-resolution logic as Behaviour Tracker |
| Monthly Sharp Count Checklist | Front-Line/Support Staff + **Second Verifying Staff Member** (dual-control, per-transaction — not a Tier value, see §10) | No (routine) unless a discrepancy is found, which triggers an automatic alert (item 7) plus a **Staff-Related Incident Report** (Bucket 1 content, elevated to Bucket 5's escalation criteria — see §5 note and OQ-08) | First-line supervisory reviewer (§3a, OQ-47) (review discrepancies) | Program Manager+ | |
| Medication Administration Record (MAR) — routine entries | Front-Line/Support Staff **who hold a medication-administration-training credential** (§10 — not Tier-gated) | No (routine) | First-line supervisory reviewer (§3a, OQ-47) (review accuracy/compliance) | Program Manager+ | Untrained Front-Line staff get view-only or no access, "depending on their role" (unspecified which) |
| MAR — error/missed-dose/refusal/discrepancy entries | Same as above | **Yes — Bucket 2 (Medication-Related Documentation)** | First-line supervisory reviewer (§3a, OQ-47) required co-sign; escalates to Program Manager/Director of Operations/Executive Director | — | Controlled-substance counts additionally require **Two Authorized Staff** verification (§10) |
| Incident Report (Client Incident Report) | Front-Line/Support Staff (the staff member involved/witnessing) | **Yes — Bucket 1 (Incident Reports)** | First-line supervisory reviewer (§3a, OQ-47) required co-sign; escalates to Program Manager/Director of Operations when required | Program Manager+ | Front-line view restricted to their own currently-assigned clients' incidents — explicitly **not** historical incidents, other staff's incidents, or unrelated clients (Q3 L493) |
| Individual Needs Assessment | Program Manager or Supervisor (contradiction #2 in evidence file — one instance says "Team Lead under supervisory direction," treated as drafting looseness, not a real Team-Lead authorship right, since every other mention names Supervisor) | **Yes — Bucket 3 (Client Assessments and Planning Documents)** | **Ambiguous approver — see OQ-40.** Two different phrasings appear ("Program Director or Clinical Supervisor" in Q2 vs. "Director of Operations or Designated Supervisor" in Q5); Director of Operations is the one point of agreement | Front-Line/Support Staff (view-only) | Completed within 7 days of intake |
| Healing Plan | Program Manager or Supervisor (same contradiction as above — "Program Coordinator" also appears once, collapsed as loose vendor-voice for Program Manager/Supervisor, not a distinct role — no such title exists in the confirmed org chart) | **Yes — Bucket 3** | Same ambiguity as Individual Needs Assessment — see OQ-40 | Front-Line/Support Staff (view-only) | Completed within 7 days of intake, reviewed every 3 months; also needs its own review-cadence metadata beyond the generic Version chain (`entity-model.md` §5) |
| Individual Support Plan | **Unaddressed in the discovery doc** (postdates it — form 23). Form 23's own signature block: Support Worker + **Supervisor Approval** | Likely Bucket 3 by analogy ("significant updates to client support plans" is named in Bucket 3's own wording) — **not confirmed**, see OQ-45 | Supervisor (per form's own signature block) | Front-Line/Support Staff (inferred, by analogy with Individual Needs Assessment/Healing Plan) | Program field is multi-select in the source form, conflicting with the single-active-Placement rule — treated as stale (`entity-model.md` §3) |
| Individual Safety Plan | **Unaddressed in the discovery doc** (postdates it — form 22). Form 22's own signature block: **Support Worker + Supervisor** (shared date field, structural oddity per the form audit) | Likely Bucket 3 by analogy (same "planning documents" language) — **not confirmed**, see OQ-45 | Supervisor (per form's own signature block) | Front-Line/Support Staff (inferred) | Q3's "client risk information and safety plans" view-only phrase (L416) may reference this document type, but never names it directly |
| Intake Screening Tool | Intake & Admissions Coordinator, Program Manager, or Supervisor (all three named as completers) | **Yes — treated as Bucket 3-adjacent** (not literally named in Bucket 3's list, but the Review and Approval tables give it its own required approver) | **Rank-inversion, unresolved — see OQ-40.** Approved by "Program Director or Designated Supervisor" (Q2) / not separately restated in Q5's table — a Supervisor (a tier below Program Manager) approving a document a Program Manager may have completed | Front-Line/Support Staff (view-only) | Completed at intake or within 3 days |
| Client Information (Face Sheet) | **No author/approver stated anywhere in the discovery doc or forms 20–24** | Unaddressed | Unaddressed | — | Two documents with no authorship field at all in their source form (Client Information, Grocery List) — `entity-model.md` §5 already notes this gap; carried here as a coverage gap, not invented |
| Client Intake Form | Staff Completing Intake (per Form 20's signature block, any staff — no restriction stated); its "Internal Use Only" block (Eligibility Determination, Assigned Program, Assigned Case Manager, Service Start Date) has no named approver in the source | Unaddressed beyond the signature requirement | Unaddressed | — | "Assigned Case Manager" on this form maps to Team Lead/Program Manager acting in that capacity per the OQ-03 resolution — not a distinct role |
| Client Service Agreement | **NextGen Representative** (Form 21's signature block — "Name/Position/Signature/Date," any Title can sign, no restriction stated) | Unaddressed | Unaddressed | — | Grain itself still open (standing vs. episodic) — **OQ-32** |
| Discharge Form | Program Manager/Supervisor (per Q5's Discharge Approval Summary) | **Yes — Bucket 4 (Discharge Documentation)** | Director of Operations (Executive Director for high-risk/special-circumstance discharges) | — | Document doesn't exist as a source file yet — **OQ-09**; approval facts exist ahead of the form itself |
| Discharge Checklist | Program Manager/Supervisor, with Team Lead input | **Yes — Bucket 4** | Director of Operations | — | Same MISSING MATERIAL status as Discharge Form |
| Final Progress Summary / Final service summary | Program Manager/Supervisor | **Yes — Bucket 4** | Director of Operations | — | Named in both Q5's table and Q13's Bucket 4 wording ("Final service summaries") — treated as the same document |
| Personal Mileage Form (+ Log) | Any Staff (own submissions only) | N/A — financial track, see §7 | First-line supervisory reviewer (§3a, OQ-47) (approve own-team submissions) | Finance/Administration (processing) | Per-Staff, per-Pay-Period grain |
| Trip Risk Assessment & Excursion Plan | Trip Leader (a Staff Assignment role, not a Title — `entity-model.md` §3) | Its own approval chain, not one of the five buckets: **Supervisor Approval + Program Manager (if required)**, per Form 24's signature block | Supervisor; Program Manager conditionally | — | Per-Excursion grain, many-Clients |
| Staff Incident Report | **Unaddressed — template not yet provided (OQ-08)** | Presumably Bucket 1-equivalent for staff-involved incidents, but not confirmed since the document doesn't exist | Unaddressed | — | Possibly the same document as the "Staff-Related Incident Report" the sharp-count/medication-discrepancy alerts generate — not resolved (OQ-08) |
| Behaviour Support Plan | **Unaddressed — document doesn't exist anywhere across all 24 audited forms (OQ-10)** | Unaddressed | Unaddressed | — | |

---

## 5. The five required-approval buckets (definitive, per Q13 L1740–1769)

These are Q13's own definitive list (L1740–1769) of document categories with a genuinely required, blocking co-signature before finalization — everything else in Table §4 that isn't in one of these five is Lock + optional audit-based Review (§2's collapse decision). **This list is not exhaustive of every "Yes" cell in Table §4, though** — two rows there require approval for reasons outside Q13's five buckets entirely, not covered by this list: the **Intake Screening Tool** (its own named Review-and-Approval table, Q2/Q5) and the **Trip Risk Assessment & Excursion Plan** (its own signature-block approval chain, Form 24, postdating Q13 altogether). Table §4 flags both as such rather than folding them silently into one of the five.

1. **Incident Reports** — completed by the involved/witnessing staff member, reviewed and signed by the **first-line supervisory reviewer (§3a, OQ-47)** before finalization, escalated to Program Manager/Director of Operations when required.
2. **Medication-Related Documentation** — medication error reports, medication incident documentation, controlled substance discrepancy reports (not routine MAR entries — see Table in §4).
3. **Client Assessments and Planning Documents** — Individual Needs Assessment, Healing Plan, and (source's own wording) "significant updates to client support plans" — read as extending to Individual Support Plan and Individual Safety Plan **by inference, not by name** (**OQ-45**).
4. **Discharge Documentation** — Discharge Form, Discharge Checklist, Final service summaries.
5. **High-Risk Documentation** — serious behavioural incidents, safety-related reports, missing person/AWOL documentation, emergency response documentation. **This bucket has no backing Document type of its own** — on the evidence available, it reads as a *severity overlay* on top of Bucket 1 (an Incident Report documenting a serious behavioural incident or an AWOL event) and possibly Emergency Preparedness Documentation during an actual activation, raising that instance's escalation criteria, rather than naming a sixth document type. Table §4 treats it this way (e.g. the Sharp Count Checklist's discrepancy-triggered "Staff-Related Incident Report" is Bucket-1 content elevated to Bucket 5's escalation tier, not a separate bucket assignment) — flagged as a collapse decision, not confirmed by any source text.

---

## 6. Functional Group gating — which department authors which document types

Confirmed (collaborator, `entity-model.md` §4): Functional Group is the axis that gates document authorship/view access.

| Functional Group | Document types this group authors (per the matrix above) |
|---|---|
| **Direct Care** (Front-Line/Support Staff → Team Lead → Supervisor → Program Manager chain) | Daily Log, Case Note, Individual Contact Note, Noteworthy Update, Shift Checklist, Behaviour Tracker, Monthly Activity Report, Grocery List, Emergency Preparedness Documentation, Monthly Sharp Count Checklist, MAR (routine + incident), Incident Report, Individual Needs Assessment, Healing Plan, Individual Support Plan, Individual Safety Plan, Discharge Form/Checklist/Final Progress Summary, Trip Risk Assessment |
| **Clinical** (7 Clinical Professional titles) | **No document type in the discovery doc is directly authored by a Clinical Professional title** — every clinical/planning document's "Completed By" column names Program Manager or Supervisor, never a Clinical Professional by title. Clinicians are described only as contributing assessment/therapeutic expertise, not as the named author-of-record. This is a genuine, surprising gap — flagged as **OQ-42**, not resolved by inference. |
| **Administrative & Compliance** | Personal Mileage Form (own submissions), Client Intake Form (Staff Completing Intake — any staff, not restricted to this group specifically). **Intake Screening Tool deliberately not listed here as a flat group-wide grant** — the Intake & Admissions Coordinator specifically is one of its named completers, but so is Driver's own Functional Group-mate status a reason to worry: applying Functional Group as a flat gate would hand every Administrative & Compliance title (including Driver) the same Intake Screening Tool access as the Intake Coordinator, which conflicts with Q3's own example that a Driver shouldn't see a client's mental health diagnosis. **Flagged as OQ-48**, not resolved by a silent per-Title carve-out. |
| **Cultural** (Indigenous Cultural Coordinator) | **No document type anywhere in the discovery doc or the 24 audited forms names this role as an author, reviewer, or approver of anything.** This role has never appeared in any operational (non-org-chart) text — a standing observation already made in `entity-model.md`'s OQ-38 discussion, restated here because it means the Cultural Functional Group currently unlocks access to nothing in this matrix. Flagged as **OQ-41**. |
| **Executive/Corporate** (Executive Director, Director of Operations) | No routine authorship — this tier's role in the matrix is exclusively approval/escalation (Buckets 1–5, plus organization-wide View) |
| **IT/System** (System Administrator) | Not a document-authoring role at all — see §9 (Unlock) and its own contradiction note there |
| **Community Partnerships & Outreach** | No document type named in the discovery doc — the Community Partnerships & Development Manager's department deals with external training/partnership relationships (per OQ-36's resolution, purely staffing-side for Training & Consultation), not client-care documentation |

**The five senior/functional managers (Clinical Services, HR & Administration, Finance & Corporate Services, Quality Improvement & Compliance, Community Partnerships & Outreach), stated explicitly rather than left implicit:** moving each into the department they head (client-confirmed, `entity-model.md` §4) was justified specifically because Functional Group "determines which documents a manager can see and sign off on for their own team" — but applying that logic to what's actually in this matrix, **four of the five get nothing named here**, because their own department has no document type in the table above to begin with:
- **Clinical Services Manager** — Clinical Functional Group has no authored document type (OQ-42) and, per §8, Clinical's Individual Contributor/Specialist tier isn't a named approver anywhere either — so this manager's document-permission content is currently empty, not merely unstated.
- **HR & Administration Manager, Quality Improvement & Compliance Manager, Community Partnerships & Outreach Manager** — same outcome: Administrative & Compliance (beyond Intake/Mileage/Client-Intake-signature, none tied to HR or QA specifically) and Community Partnerships & Outreach have no named document type either.
- **Finance & Corporate Services Manager** — the one exception: gets Financial/Billing access via §7's Finance/Administration Team line (their direct report, Finance & Payroll Officer, sits in that track).

This is a direct, material consequence of OQ-42/OQ-41's gaps, not a new open question of its own — but the client-confirmed reassignment's own stated rationale ("this grouping is what determines which documents a manager can see and sign off on") is currently unfulfilled for four of the five managers, and that's worth knowing before this matrix is treated as final.

---

## 7. Financial/Billing access (separate track — collapsed from Q3, L532–616)

| Hierarchy Tier | Financial/Billing Access |
|---|---|
| Front-Line/Support Staff | Submit own mileage/expense claims; view own submissions only. Explicitly **not**: other employees' claims, client billing info, agency revenue, payroll info, funding agreements, budget reports, other financial records |
| Team Lead | Review/verify staff mileage & expense submissions; confirm expenses tie to approved client services; approve/recommend approval; monitor Site-level spending |
| Supervisor | Expense oversight across their several assigned Sites (broader than Team Lead's one-Site scope, per OQ-33 — the source table's own text says "program-level," read as Site-based here for consistency with §3) |
| Program Manager | Program budgets and operational spending; approve program-related expenditures |
| Director of Operations | **Undifferentiated from Program Manager in the source** — same bullet list verbatim (Q3 L583–589), and the Recommended Permission Structure table's own "Director" row is blank (L612–613). **Genuine drafting gap, not resolved here — OQ-39.** |
| Executive Director / Executive Leadership | Organization-wide financial reports, program budgets, revenue/expense summaries, funding/contract info, financial performance info |
| Finance & Payroll Officer (Administrative & Compliance) | Processing reimbursements, payroll-related financial info, billing records, invoices/payments, financial reports, audit documentation. "Limited access to clinical information unless required for billing verification" |

---

## 8. Approval/escalation authority for the Individual Contributor / Specialist tier — unresolved

`entity-model.md` §4 already flags this: the seven Clinical Professional titles sit at Individual Contributor / Specialist tier, flat, with no internal lead and no supervisory reports (client-confirmed, 2026-09-26). **Consequence for this matrix, stated but not resolved:** if Hierarchy Tier is what gates approval/escalation authority (§1), this flat placement means a clinician **approves nothing and is never a named escalation target** in any bucket above — consistent with §6's finding that no document names a clinician as author either. Whether this is actually intended (i.e., clinicians are pure individual contributors with zero document-approval role, full stop) or a gap in how the discovery doc was drafted (clinicians simply weren't asked about directly) is exactly **OQ-42**.

The same applies to every other Individual Contributor / Specialist title (Finance & Payroll Officer, HR Coordinator, QA & Compliance Officer, Training & Staff Development Coordinator, Maintenance & Facilities Coordinator, Driver, Indigenous Cultural Coordinator, System Administrator) — none of them appear as an approver in any bucket above. For most of these this is expected (their work isn't client-care documentation), but it's stated explicitly here rather than left implicit.

---

## 9. Unlock authority (restating the glossary's existing resolution as an action, not re-litigating it)

Per `glossary.md`'s existing resolution (Additional Requirements §5 treated as authoritative over Q13's differing default, being the more specific, later section — reconfirmed here after transcribing both sides in full in the evidence file):

- **Default:** System Administrator(s) only.
- **Delegable to:** Director of Operations, Program Manager(s), or other Executive-Director-approved leadership personnel — role-based, clearly assigned, fully auditable, removable when no longer required.
- Every unlock records who unlocked, why, and when; the original locked version is preserved; the correction creates a new Version (`entity-model.md` §5).

This matrix does not add a new default — it's restated here only because "who may unlock" is the one action in the whole model that's Tier/Functional-Group-independent by design (a delegation list, not a fixed axis value), and the permission matrix is where a reader would otherwise expect to find it.

**Unresolved tension this default rests on, surfaced by the evidence file, not previously stated this plainly:** Discovery Q27 (L2982–2993) says **no dedicated System Administrator role exists today** — "system administration responsibilities will be assigned to designated members of leadership based on organizational needs" — framing it as a responsibility bundle, not a standalone Title. But `entity-model.md`'s OQ-37 resolution treats System Administrator as **a real title someone holds** (collaborator's authorized inference, "its a title that someone actually holds and not a permission that can be granted to any staff member"). If Q27's framing is the operative one, the canonical unlock default above ("System Administrator(s) only") may currently have no one actually holding it — the delegation list (Director of Operations/Program Managers/ED-approved leadership) would be doing all the real work from day one, not a fallback. This bears directly on how the unlock default should be implemented and is worth surfacing to the collaborator specifically (per the same authorization pattern as the rest of OQ-37), not necessarily a new client-facing question — System Administrator's own reporting line is already item 7 of the still-pending OQ-37 client-facing ask.

---

## 10. Cross-cutting rules the three confirmed axes cannot express

Per the axis set being closed at exactly three (Hierarchy Tier / Functional Group / Engagement Type — collaborator, "no thats it," OQ-30/37) — these are real access-gating facts that don't fit any of the three, flagged rather than forced into one:

- **Medication-administration training credential** — MAR create/edit access requires "completed required medication administration training and... approved by NextGen Support Services" (Q10, L1372–1379), independent of Title/Tier/Functional Group. An untrained Front-Line Staff member gets view-only or no access; a trained one gets full create/edit. **Not modeled by any axis — OQ-44** (does the portal need to track this as a Staff attribute, or trust an off-system HR/training record?).
- **Dual-control, per-transaction verification** — "Two Authorized Staff" (controlled-substance/narcotic counts, Q10 L1455) and "Second Verifying Staff Member" (sharp counts, Q14 L1897) are not role values — they're a requirement that *some second trained staff member*, whoever is on shift, co-verifies a specific transaction. **OQ-46**: does the second verifier need to be Team-Lead-tier or above, or can any two medication/sharp-count-trained peers satisfy this?
- **Volunteer's "restricted portal access"** — client-confirmed as a real requirement (OQ-37, `entity-model.md` §4) but never defined *which* document types or actions are excluded. **OQ-43.**
- **Exceptions and Temporary Access** (§3 above) — a real, named mechanism with no defined grantor, workflow, or duration; carried to item 7, not modeled as a matrix cell.

---

## 11. Open items surfaced by this artifact

New items, registered in full in `distillation/open-questions.md`:

- **OQ-39** — Director of Operations' financial access is undifferentiated from Program Manager's in the source (identical bullet list), and the Recommended Permission Structure table's own "Director" row is blank. What should Director of Operations' financial access actually be?
- **OQ-40** — "Clinical Supervisor" / "Designated Clinical Supervisor" / "Designated Supervisor" appear only in isolated approval-chain cells (Individual Needs Assessment, Healing Plan, Intake Screening Tool) and match no confirmed Title. Does this mean the Clinical Services Manager, an ordinary Site-based Supervisor acting in a clinical-review capacity, or an as-yet-unnamed role? Also covers the Intake Screening Tool's rank-inversion (a Supervisor approving a Program Manager's own completed work) and the Q2-vs-Q5 approver mismatch for Individual Needs Assessment/Healing Plan.
- **OQ-41** — Indigenous Cultural Coordinator/Cultural Liaison authors, reviews, or approves nothing named anywhere in the discovery doc or the 24 audited forms. What documents (if any) does this role actually touch, and what does the Cultural Functional Group gate access to in practice?
- **OQ-42** — None of the seven Clinical Professional titles appear as the named author of any clinical/planning document — Program Manager/Supervisor are named instead. Do clinicians ever author Individual Needs Assessment/Healing Plan directly, or only contribute clinical input the way Front-Line staff contribute observations? Related to, but distinct from, OQ-37's still-open question about a clinician's program-side reporting line for timesheet/note review.
- **OQ-43** — Volunteer's client-confirmed "restricted portal access" (OQ-37) has never been defined — which document types/actions does a Volunteer engagement type actually exclude?
- **OQ-44** — NEEDS DECISION (likely ours, not the client's): should the medication-administration-training credential gating MAR access be modeled as a tracked Staff attribute, or treated as an off-system HR/training fact the portal simply trusts?
- **OQ-45** — Client Information, Client Intake Form, Client Service Agreement, Individual Support Plan, Trip Risk Assessment, Individual Safety Plan have no discovery-doc access statement beyond forms 20–24's bare signature blocks (who signs, not who may view/edit/lock at each stage). Does the client need to confirm full access semantics for these, or is the signature-block evidence sufficient to design from?
- **OQ-46** — Does the "second verifier" in medication/sharp-count dual-control checks need to be Team-Lead-tier or above, or can any two trained peers on shift satisfy the requirement?
- **OQ-47** — Is the first-line supervisory co-signer for a document Team Lead, Supervisor, either, or both in sequence (§3a)? Every "Team Lead/Supervisor"-required cell in Table §4 cites this rather than silently picking one.
- **OQ-48** — NEEDS DECISION (collaborator, since the three-axis set is closed): is Functional Group alone too coarse a gate for client-sensitive documents within Administrative & Compliance — specifically, does the Driver need to be excluded from Intake Screening Tool access despite sharing a Functional Group with the Intake & Admissions Coordinator?

**Not new open items — resolved by this artifact's own collapse decisions, not pushed to the client:**
- Daily Log/Case Note/Individual Contact Note/Noteworthy Update/Shift Checklist/Behaviour Tracker's routine-vs-required-approval status (§2 collapse decision, favoring Q13+Q3 over Q2's looser language).
- "Program Coordinator" treated as loose vendor-voice for Program Manager/Supervisor, not a distinct role (no such title exists in the confirmed org chart).
- Behaviour Tracker/Emergency Preparedness/Sharp Count's apparent overlap with Bucket 5 (High-Risk Documentation) — resolved as two separate Document instances (the routine record stays routine; a genuinely high-risk event produces its own Incident Report, itself Bucket 1 content elevated to Bucket 5's escalation criteria, not a sixth bucket or an escalated state on the routine document itself — see §5's revised note).

**Redirectable calls made in this artifact, worth flagging back rather than treating as final:** the Q13-over-Q2 routine/required-approval reading (§2), "Program Coordinator" as loose vendor-voice (§4/§6), and the Bucket 5 severity-overlay reading (§5) are all collapse decisions this artifact made rather than sent to the client — reasonable readings of the evidence, not confirmed facts. OQ-44 and OQ-48 are explicitly flagged as calls for the collaborator, not the client, consistent with `CLAUDE.md`'s working preference to distill and present options rather than silently pick where the choice is genuinely someone else's to make.
