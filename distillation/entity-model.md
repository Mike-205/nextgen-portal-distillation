# Entity Model (Conceptual)

This is a conceptual model — what the real-world things are, what they're made of, and how they relate — not a database schema. No table names, no column types, no foreign keys. Ground truth is the discovery doc, scope memo, the 24 form audits, the glossary, and direct client answers recorded in `open-questions.md`; `../next_gen_services`'s Prisma schema was not consulted anywhere in building this.

**Scope boundary (deliberate, per `CLAUDE.md`'s artifact dependency order):** this item defines *what a record is and what it points to* — entity shape, attributes, cardinality. It does **not** define *who may act on it and when* — that's item 7 (Cross-Cutting Concerns): unlock authority, alert trigger conditions and escalation chains, retention periods, disclosure consent/OCAP framework, Canadian data residency. Where a boundary line had to be drawn, it's called out explicitly below rather than silently absorbed into either item.

**Evidence base:** synthesized from two provenance-tagged working files built specifically for this artifact — `distillation/research/entity-model-input-documents.md` (document inventory grounded in all 24 form audits) and `distillation/research/entity-model-input-discovery.md` (entity-bearing statements from the discovery doc and scope memo, tagged CONFIRMED/PROPOSED/CONTRADICTED/UNANSWERED). Both are kept as supporting evidence, not superseded by this file.

**Reading the tags below:** most discovery-doc-derived statements are **PROPOSED** (vendor-voice "the system should..." language), not CONFIRMED — see the methodological caveat in `open-questions.md`: NextGen currently has zero active clients, so "current process" language in the discovery doc describes intended design, not tested practice. This model still uses PROPOSED statements to shape entity structure (that's what an unbuilt system's design intent is *for*), but does not treat them as settled fact the way a CONFIRMED client-call answer is treated.

---

## 1. Organizational structure

### Program / Service
The six confirmed offerings (RESOLVED, `glossary.md`): Respite Care, Transportation, Group Care Services, Family Reunification Support, Supported Independent Living (SIL), Training & Consultation Services. A Program is the top-level service category a Client is placed into.

- **Program ↔ Site: many-to-many.** Discovery Q17 (PROPOSED): "each physical site may operate a single dedicated program, or multiple programs depending on the service model." Not one-Site-per-Program.
- **Program → Program Manager: 0..1; Program Manager → Program: one, target one-to-one, RESOLVED (2026-09-24, OQ-17/OQ-34/OQ-35).** Three separate sources, not one: (1) collaborator's framing, client agreed ("cool") — **"1 program will map to 1 program manager"** is the target, made possible precisely because nothing is hardcoded to four/six named variants; (2) client fact (OQ-34) — a Program can currently have **none** assigned at all ("there's none currently"), which is where the 0..1 comes from; (3) our own PROPOSED design inference, not stated by either party — a Program Manager *may* hold more than one Program in the interim (implied by OQ-17's "report to the existing program managers" intent), though as of today this doesn't actually happen (the four named PMs each hold exactly one; Transportation/Training & Consultation currently have none). Org chart (CONFIRMED, D Q1) names a dedicated Program Manager variant for 4 of the 6 Programs (Group Living, Family Living & Reunification, SIL, Respite Services). **Transportation and Training & Consultation currently have no Program Manager assigned at all** — client's words, "there's none currently" (**OQ-34**, RESOLVED). Client only "kind of" agreed when a spare-capacity-based pick was floated, and independently confirmed anticipating dedicated per-program PMs eventually ("another program manager can be appointed to"). **RESOLVED (2026-09-26, OQ-36):** interim Program-Manager-level authority for these two Programs is the **Director of Operations directly** (client-confirmed); the eventual-assignment deciding factor is **spare capacity**, but only as a collaborator decision given the client's repeated non-answer on that specific point, not a clean client confirmation. **Modeled as an assignable, optional reference** (confirmed design, **OQ-35**): the Program's Program Manager slot must support a genuine "none assigned" state, not just a placeholder among four/six fixed values.

### Subservice
Each Program has its own fixed set of Subservices (RESOLVED, `glossary.md`, confirmed via the client-approved Client Intake Form §13), e.g. Respite Care → In-home / Out-of-home-Overnight / Emergency. A Placement's "service requested" resolves to one Program plus one or more Subservices under it (see Placement below) — Subservice attaches to the **Placement**, not directly to the Client, since it's a property of *this specific placement episode*, not a permanent Client attribute.

### Site
A physical location (house/service location) — RESOLVED as a new structural entity the portal introduces; not present as a concept in any of the original 19 forms. Confirmed examples under Group Care: Ravens Nest, Eagles Nest, Golden Bear, Whispering Harmony. Admin-created.

- **Site ↔ Program: many-to-many** (see above).
- Several document types (Shift Checklist, Sharp Count, Grocery List, Behaviour Tracker, MAR, Activity Calendar) currently only carry a Program field, predating Site as a concept — expected to move to a real Site reference in the redesign, not a new client-facing question.
- **Open:** whether the Client Incident Report's "Facility Information" section describes a NextGen Site or an external caregiver's location — **OQ-31**.

---

## 2. Client and external parties

### Client
RESOLVED canonical term (`glossary.md`) for the person receiving services, regardless of program. Key attributes surfaced across the form set:
- **External Referral ID** + **Referral Source** (RESOLVED, **OQ-13/OQ-23**) — an identifier already issued by the referring body (e.g. Children and Family Services), captured, not generated; one generic field pair, not per-agency fields. Likely optional (self-/family-referrals may have none).
- **Funding Source** (RESOLVED, `glossary.md`) — PDD, FSCD, AISH, Jordan's Principle, Private Pay, Insurance, Other.
- Internal system key — a separate, portal-generated identifier, unrelated to the External Referral ID.

### Parent/Guardian and Case Worker
Two distinct external-party relationship types a Client can have (RESOLVED, **OQ-03**), not one collapsed field — which one (or both, over the Client's history) applies depends on custody status:
- **Case Worker** — canonical term for the Children and Family Services employee who acts in the parents' place when a court has removed the child from parental care.
- **Parent/Guardian** — the parent/guardian, where guardianship has not been removed.
- **Deliberately out of scope:** court-order-type granularity (Supervision / Temporary Guardianship / Permanent Guardianship / Custody Agreement) — RESOLVED **OQ-21**, client confirmed the simpler Parent/Guardian-vs-Case-Worker split is sufficient for now. The underlying research (`distillation/research/legal-context-research.md` §1) is preserved, not discarded, in case this needs revisiting — no `courtOrderType` placeholder is being modeled now.
- **Open:** whether a foster/kinship caregiver counts as a Parent/Guardian (excluded from portal access) or a distinct external-user category (potentially granted staff-like scoped access) — genuine discovery-doc self-contradiction, **OQ-29**. Not resolved here; the model leaves "external party type" as a category that may need a third value pending that answer.

---

## 3. Placement and Excursion

### Placement
New term (`glossary.md`) naming the entity tying a Client to a Program + Site for a date range — the client's own material has no equivalent word, but every mention of "which program/site a client is in" describes this.

- **Cardinality: single-active** (RESOLVED, **OQ-05**) — a Client has exactly one primary/main Placement at a time. Program transitions are handled as ending one Placement and starting another (discovery Q7, PROPOSED but consistent with the confirmed rule), not a concurrent second Placement.
- **Attributes:** Program, one or more Subservices, Site, start date, end date (open-ended while active), a "reason for change" pointer to the transition/discharge event that ended it.
- **Placement → episodic Document: one-to-many.** Only the episodic bucket of Document types (§5 below) is scoped to a Placement; standing Document types attach to the Client directly and survive Placement transitions — see the grain split in §5.
- **Secondary/facilitating services** (RESOLVED, **OQ-05**) — other services that support the main Placement (e.g. Transportation to medical appointments under a Respite Care placement) are billed inclusively under the active Placement, not a second Placement. Modeled as an attribute list on the active Placement, not a new entity.
- **Client Intake Form's "Internal Use Only" block** (Eligibility Determination / Assigned Program / Assigned Case Manager / Service Start Date) is, in substance, Placement-creation data bolted onto the intake document rather than intake data itself — modeled here as the data that creates a Client's first Placement, even though the client-facing form stays one physical document. Not a new open question, a synthesis call.
- **Billing relevance** (PROPOSED, discovery Q25/memo): Placement + Shift + Document(Mileage Log) feed a billing/funder-reporting concept — service hours, program utilization, service delivery records, reimbursable expenses. Confirms the same shape as the secondary-services billing rule above; no new entity needed for item 4, a reporting view over existing entities.
- **Individual Support Plan's Program field is multi-select** in its source form (form 23) — conflicts with the single-active-Placement rule. Treat the source form's multi-select as stale/unreconciled against the now-confirmed single-Placement model, not as evidence Placement should be multi-valued.

### Excursion
**New entity, not in `CLAUDE.md`'s original illustrative list — required by the evidence.** The Trip Risk Assessment & Excursion Plan (form 24) is the only document across all 24 audited whose natural subject is an event with **many Clients attached**, not a single Client or a single Site — it doesn't fit the per-Client or per-Site pattern every other document follows.

- **Excursion ↔ Client: many-to-many** (a participants table lists multiple Clients).
- **Excursion ↔ Staff: many, with named roles** — Trip Leader, plus per-role assignments (Driver, First Aid, Medication, Attendance, Emergency Contact). Each is a Staff Assignment scoped to this Excursion specifically, not to a Program/Site.
- No Program field on the source form — an Excursion's Program/Site context, if any, is inherited from its participating Clients' active Placements, not stored on the Excursion itself.

---

## 4. Staff, Staff Assignment, and Shift

### Staff
A person employed by NextGen. **Role is modeled as a reference to a role list, now confirmed in shape and scope unit, not yet fully populated** — OQ-01, OQ-02, OQ-17, OQ-33, OQ-34, and OQ-35 (Team Lead/Supervisor/Program Manager/Director of Operations naming, hierarchy, and scope unit) are all RESOLVED as of 2026-09-24: the confirmed tier order is **Director of Operations > Program Manager > Supervisor > Team Lead > Front-Line/Support Staff**; Team Lead and Supervisor are scoped by **Site count** (Team Lead → one Site, Supervisor → several Sites), not by Program; Program Manager is assigned per-Program as data, and a Program can genuinely have none assigned — Transportation and Training & Consultation currently don't. **OQ-36 (RESOLVED, 2026-09-26):** interim Program-Manager-level authority for both is the Director of Operations directly; the eventual-assignment deciding factor (spare capacity) is a collaborator decision, not a client confirmation — see `open-questions.md`. This is deliberate: item 4 needs Staff to exist and be assignable; item 5 (Permission Matrix) is where the role axis's access scopes get built.

**OQ-30 RESOLVED (2026-09-24, collaborator answered on the client's behalf; original tag UNANSWERED; not yet relayed to the client):** the full ~25-title org chart is in scope now. Staff.title references the full org-chart title list as data, not a fixed enum (same pattern as Program Manager). But the permission matrix doesn't key off Title directly — it keys off a separate **Category** layer each Title maps onto: **Hierarchy Tier**, **Functional Group**, **Engagement Type** — axis set CONFIRMED (2026-09-24, "no thats it"). **Functional Group is what actually gates which Document types a role can author/view — CONFIRMED (collaborator, 2026-09-26), covering both the client-confirmed and the previously-INFERRED Functional Group cells alike (explicit collaborator sign-off on extending the confirmation to the inferred cells, this batch).** See glossary's **Staff Title vs. Category** entry for the value vocabulary.

- Confirmed operationally-relevant tiers appearing in actual workflow answers (not just the org chart): Front-Line/Support Worker, Team Lead, Supervisor, Program Manager, Director of Operations, Executive Director, Finance/Admin staff, System Administrator. (Team Lead and Supervisor now confirmed distinct, not a combined "Team Lead/Supervisor" actor — see glossary.) **New bottom-rank Tier value, added 2026-09-26 (collaborator):** **Individual Contributor / Specialist** — no supervisory reports, not part of the Direct Care Team Lead/Supervisor/Front-Line chain, and deliberately distinct from **Front-Line/Support Worker** (glossary's definition of that term is specifically "working one-on-one with clients" in the direct-care support-worker sense, which doesn't fit a psychologist, a compliance officer, or a payroll officer). Covers the seven Clinical Professional titles and the individual-contributor Administrative & Compliance titles below.
- **OQ-37 RESOLVED (2026-09-25, mixed provenance — see table below).** Every title from the org chart, plus System Administrator (a real title, not on the org-chart list), now has a Hierarchy Tier/reporting-line and Functional Group assignment. Most of these are our own inference, explicitly authorized by the collaborator rather than individually relayed to the client ("for the questions that are left hanging i think we can infer and/or try to map them correctly") — flagged per-row below, not silently treated as client fact. **Revised again 2026-09-26 (tenth batch, collaborator relayed further client answers plus made several calls directly)** — see per-row changes below and **OQ-38** (new) for the one item this batch could not close.

**Title → Hierarchy Tier / Functional Group mapping (OQ-37).** **Revised 2026-09-26 (advisor review):** reporting line is now its own column, split out from Hierarchy Tier, because for Direct Care roles below Program Manager the two are not the same kind of fact — the Tier is a Title-level property, but *who specifically* a person reports to depends on their Staff Assignment (which Site/Program), not their Title alone. Rows marked **assignment-derived** below are not a fixed Title→Title line the way e.g. "Finance & Payroll Officer → Finance & Corporate Services Manager" is; they resolve only once a specific Staff Assignment exists (see Staff Assignment, below).

| Title | Hierarchy Tier | Reporting line | Functional Group | Provenance |
|---|---|---|---|---|
| Executive Director / CEO | Top of hierarchy | — (top of hierarchy) | Executive/Corporate | CLIENT (D Q1; ED glossary entry) |
| Director of Operations | Above Program Manager and the five managers below | Executive Director | Executive/Corporate | CLIENT (OQ-02/17) |
| Clinical Services Manager | Same rank as Program Manager — both report directly to the Director of Operations (COLLABORATOR, 2026-09-26) | Director of Operations | **Clinical** — moved from Executive/Corporate into the department this manager actually heads (COLLABORATOR decision, 2026-09-26; **CLIENT-CONFIRMED, 2026-09-26**, relayed correction accepted) | Tier: COLLABORATOR. Reporting line: CLIENT (2026-09-25 batch). Functional Group: CLIENT (relayed, 2026-09-26) — originally a COLLABORATOR correction that contradicted the client's 2026-09-25 "everything is correctly listed" answer; relayed and **client confirmed the correction** |
| HR & Administration Manager | Same rank as Program Manager (COLLABORATOR, 2026-09-26) | Director of Operations | **Administrative & Compliance** — moved from Executive/Corporate (CLIENT-CONFIRMED, 2026-09-26, relayed correction accepted) | same as above |
| Finance & Corporate Services Manager | Same rank as Program Manager (COLLABORATOR, 2026-09-26) | Director of Operations | **Administrative & Compliance** — moved from Executive/Corporate (CLIENT-CONFIRMED, 2026-09-26, relayed correction accepted) | same as above |
| Quality Improvement & Compliance Manager | Same rank as Program Manager (COLLABORATOR, 2026-09-26) | Director of Operations | **Administrative & Compliance** — moved from Executive/Corporate (CLIENT-CONFIRMED, 2026-09-26, relayed correction accepted) | same as above |
| Community Partnerships & Development Manager | Same rank as Program Manager (COLLABORATOR, 2026-09-26) | Director of Operations | **Community Partnerships & Outreach** — the department's actual name per the client (2026-09-26): "the manager is the person but the [Outreach name] is the department's name." Manager currently works alone, no confirmed reports, per the client's own description ("they'll coordinate all activities of the department alone") | Functional Group and department-naming: both CLIENT (relayed, 2026-09-26) — the reassignment out of Executive/Corporate was relayed as a correction and confirmed |
| Program Manager (Group Living / Family Living & Reunification / SIL / Respite Services) | supervises Supervisors | Director of Operations | Direct Care | Tier: CLIENT (OQ-17/33/34/35). Functional Group: COLLABORATOR (2026-09-26) — previously INFERRED, now explicitly confirmed to extend to this cell |
| Supervisor | scope = several Sites | **Assignment-derived** — the Program Manager of the Program(s) their assigned Sites belong to, not a fixed Title-level line | Direct Care | Tier: CLIENT (OQ-01/33). Functional Group: COLLABORATOR (2026-09-26) — previously INFERRED, now explicitly confirmed |
| Team Lead | scope = one Site | **Assignment-derived** — the Supervisor covering their assigned Site | Direct Care | Tier: CLIENT (OQ-01/33). Functional Group: COLLABORATOR (2026-09-26) — previously INFERRED, now explicitly confirmed |
| Registered Psychologist, Registered Social Worker, Mental Health Therapist, Behaviour Consultant, Occupational Therapist, Speech-Language Pathologist, Nurse (7 titles) | **Individual Contributor / Specialist** — flat, no internal lead role. **CLIENT (relayed, 2026-09-26):** "they [are] all at the same level, reporting individually to the Clinical Services Manager." **Still open, not yet asked:** if Tier is what gates approval/unlock authority and who receives escalation alerts, this flat placement means a clinician approves nothing and is never an escalation target — worth confirming that's actually intended before item 5 locks it in | Clinical Services Manager (adjacent functional manager) — **still open, not yet asked**: when a clinician works within a specific program, does timesheet approval/note review instead run to that program's Program Manager (a possible second, program-side line)? This is a different question from the internal-hierarchy one just answered, and hasn't been put to the client yet | Clinical | Functional Group: CLIENT ("everything is correctly listed"). Tier: CLIENT (relayed, this batch) |
| Family Support Workers, Child & Youth Care Workers (CYCWs), Support Workers — **when assigned to a Site-based/residential program** (e.g. Group Care Services, SIL) | Front-Line/Support Worker | **Assignment-derived** — the Team Lead at their assigned Site | Direct Care | Functional Group: CLIENT. Tier: INFERRED, well-grounded (matches glossary's Front-Line definition). Reporting line: CLIENT (relayed, 2026-09-26) |
| Family Support Workers, CYCWs, Support Workers — **when assigned to a non-Site-based program** (Family Reunification Support, Respite Care) | Front-Line/Support Worker | **Directly to that Program's Program Manager — no Team Lead/Supervisor layer**, since these programs aren't Site-based | Direct Care | **CLIENT (relayed, 2026-09-26):** "They report to the program manager, same with respite cos it's not residential as well." Resolves the Family Support Worker gap the previous draft's client-facing ask had flagged (item 6) — the Site-based Team Lead chain genuinely doesn't apply here, confirming the earlier structural read that Team Lead/Supervisor scope (Site-based, OQ-33) only makes sense where the Program actually has Sites |
| Indigenous Cultural Coordinator / Cultural Liaison | **Individual Contributor / Specialist** (PROPOSED, by analogy with the other individual-contributor titles — not itself confirmed) | **Community Partnerships & Outreach Manager** (RESOLVED, **OQ-38**, collaborator decision, 2026-09-26) | **Cultural** (RESOLVED, **OQ-38**, collaborator decision, 2026-09-26) | Three client answers across three occasions didn't converge: (1) 2026-09-25, "everything is correctly listed" — Cultural is its own department; (2) 2026-09-26 — "under Community Partnerships & Outreach"; (3) 2026-09-26, same day, after being offered the reconciliation directly — "under compliance... report to Quality improvement and Compliance manager," a third department not among the options actually asked about, and with no functional connection to that department's one other member (QA & Compliance Officer). **Collaborator's assessment: the third answer wasn't applied** — it doesn't engage with the question asked, and this title has never appeared in any operational text in the discovery doc, consistent with the client not having a fixed answer for this specific role. **Resolution applied:** Functional Group kept as Cultural (from the one methodical, in-context answer); reporting line taken as Community Partnerships & Outreach Manager (from the second answer, the only one of the three that specifically addressed "what department is this role under"). Not relayed to the client as a formal correction — unlike the five senior managers' Functional Group reassignment (below), which *was* relayed and client-confirmed; this one stays a collaborator-only call for now |
| Finance & Payroll Officer | Individual Contributor / Specialist (PROPOSED, by analogy) | Finance & Corporate Services Manager | Administrative & Compliance | Functional Group: CLIENT. Reporting line: INFERRED. Tier: PROPOSED |
| Human Resources Coordinator | Individual Contributor / Specialist (PROPOSED, by analogy) | HR & Administration Manager | Administrative & Compliance | Functional Group: CLIENT. Reporting line: INFERRED. Tier: PROPOSED |
| Intake & Admissions Coordinator | **Individual Contributor / Specialist — CLIENT (relayed, 2026-09-26), ruling out Program Manager/Supervisor rank specifically** (see note below) | **Unclear — no strong basis to infer.** An earlier proposed default (reports directly to Director of Operations, inferred from being named alongside Program Manager/Supervisor in intake-workflow steps) is **retracted**: the client's own explanation is that multiple roles (Program Manager, Supervisor, Intake Coordinator) were deliberately given the *ability* to perform intake steps so the function isn't tied to one role — a permissions/capability design choice, not a statement of equal organizational rank. Collaborator's read, which the client's explanation supports: Intake & Admissions Coordinator does **not** sit at the same rank as Program Manager or Supervisor | Administrative & Compliance | Functional Group: CLIENT. Reporting line: INFERRED/unresolved, genuinely open (no suggested default — same category as Indigenous Cultural Coordinator now). Tier: CLIENT (relayed, 2026-09-26) |
| Quality Assurance & Compliance Officer | Individual Contributor / Specialist (PROPOSED, by analogy) | Quality Improvement & Compliance Manager | Administrative & Compliance | Functional Group: CLIENT. Reporting line: INFERRED (strong — near-identical title match to "Quality Improvement & Compliance Manager"). Tier: PROPOSED |
| Training & Staff Development Coordinator | Individual Contributor / Specialist (PROPOSED, by analogy) | HR & Administration Manager (weak guess) | Administrative & Compliance | Functional Group: CLIENT. Reporting line: INFERRED, low-confidence. Tier: PROPOSED |
| Maintenance & Facilities Coordinator | Individual Contributor / Specialist (PROPOSED, by analogy) | Finance & Corporate Services Manager (weak guess) | Administrative & Compliance | Functional Group: CLIENT. Reporting line: INFERRED, low-confidence. Tier: PROPOSED |
| Driver | Individual Contributor / Specialist (PROPOSED, by analogy) | **Director of Operations, interim** — Transportation currently has no Program Manager; resolved **OQ-36** (client), not inferred | Administrative & Compliance | Functional Group: CLIENT. Reporting line: CLIENT (OQ-36). Tier: PROPOSED |
| System Administrator | Individual Contributor / Specialist if the role is internal (PROPOSED) — but see reporting-line caveat | unclear — no strong basis to infer; may not have an internal reporting line at all if the role is external/contracted (still an open, unasked question) | IT/System | Title existence + realness: COLLABORATOR (not on the org chart at all — a genuine gap in D Q1, filled by the collaborator's direct statement, not a client answer). Functional Group: INFERRED, new value never put to the client. Tier/reporting line: unresolved |

**Note on the five senior managers' Functional Group reassignment (2026-09-26, RESOLVED — client-confirmed):** moving each manager into the department they head (option chosen: collaborator, this batch) makes them consistent with how Program Manager already works (Program Manager sits in Direct Care, the group it heads) and resolves what Functional Group actually means for a manager if it gates document access — under the old Executive/Corporate placement, the Clinical Services Manager would have had no Clinical document access under their own name. This directly overrode the client's earlier "everything is correctly listed" answer, which had all five in Executive/Corporate, so it was relayed back to the client as an explicit correction — **client confirmed the correction, 2026-09-26.** All five managers' Functional Group cells above are now CLIENT-confirmed, not just COLLABORATOR-decided. See `open-questions.md`, OQ-37 residual.

Practicum Students, Volunteers, and Relief/Casual Staff are **not** separate Titles/rows here — see Engagement Type below; they cut across whichever Title/Functional Group a person actually holds.

**Engagement Type, revised (2026-09-25), two-attribute model CONFIRMED (collaborator, 2026-09-26, re-explained and reconfirmed same day):** **CONFIRMED (client, relayed):** Volunteer is its own category, not a value flattened into a schedule list, and needs restricted portal access — client's stated reason: a volunteer "can be full time, part time, relief... but on a voluntary basis." **CONFIRMED (collaborator, 2026-09-26):** modeling this as two attributes rather than one flat list is the right call —
- **Schedule basis** (CLIENT, D Q1's employment-status sentence): Full-time / Part-time / Casual / Relief / Contract / Practicum Student. These describe the *pattern* of when/how often someone works — they are not job titles and not Engagement Types on their own.
- **Paid/Voluntary flag** (our own read of the client's reasoning above, collaborator-confirmed as the right modeling choice, not itself put to the client): Paid (default) / Voluntary — orthogonal to schedule basis, so any schedule-basis value can pair with either flag (e.g. Relief+Paid is a fill-in staff member paid per shift; Relief+Voluntary is a volunteer who only fills in occasionally). This is why "volunteer" isn't a sixth schedule-basis value — per the client's own example, a volunteer isn't limited to one schedule pattern, they cut across all of them. Practical effect if adopted: scheduling/GPS clock-in still needs a Volunteer's schedule basis; the payroll timesheet export (discovery Q25 / Scope Memo) would need to exclude Volunteer records — this exclusion is our own inference from "restricted... access," not something the client was asked about directly. **Residual, non-blocking:** Practicum Students' pay status isn't settled — practicum placements are usually unpaid, but that's a different reason than "volunteering," and nothing in the source material says which; not urgent.

### Staff Assignment
Ties a Staff member to a Program and/or Site. **Not necessarily one-to-one** (PROPOSED, discovery Q17): staff "may be assigned to a specific site and program... scheduled across multiple sites or programs when required... assigned temporarily to provide coverage." Model as a Staff member having zero or more concurrent-or-temporary Program/Site assignments, not a single fixed pair. **Confirmed for Team Lead/Supervisor specifically (OQ-33):** Team Lead → exactly one Site; Supervisor → several Sites. Residual, not blocking: since Site↔Program is many-to-many, a Supervisor's Sites could span two Programs (and thus two Program Managers) — carried to item 7, not resolved here.

**The Team Lead/Supervisor layer only exists where the Program is Site-based — CONFIRMED (client, relayed, 2026-09-26).** Front-line Direct Care staff (Family Support Workers, CYCWs, Support Workers) assigned to a non-Site-based Program report **directly to that Program's Program Manager**, skipping Team Lead/Supervisor entirely: "They report to the program manager, same with respite cos it's not residential as well." This is consistent with Team Lead/Supervisor being scoped by Site count (OQ-33) — a Program with no Sites has nothing for that scope to attach to. Confirmed non-Site-based so far: **Family Reunification Support, Respite Care**. Not yet checked against **Transportation** or **Training & Consultation** (both already have no Program Manager assigned per OQ-34/36, so the question is somewhat moot for them at present) or **Group Care Services**/**SIL**, which are assumed Site-based (residential/independent-living) but not explicitly re-confirmed under this same question — carried forward as a residual, not blocking.

### Shift
**A first-class, scheduled entity** — not merely a checkbox on the Daily Log. Discovery Q25 (PROPOSED, but specific enough to read as real design intent) describes a scheduling module tracking "which staff member was scheduled and assigned to each shift... the program/site where the shift occurred... the clients supported during the shift... required documentation associated with the shift... whether required shift documentation has been completed" — plus a GPS time-clock layer (clock-in/out, geofencing) and a payroll timesheet export (staff name, employee ID, position/role, program/site worked, client assignment where applicable, scheduled vs. actual times, regular/overtime hours, supervisor approvals).

- **Shift → Staff: one** (who worked it).
- **Shift → Program/Site: one** (where it occurred).
- **Shift → Client: zero-to-many** ("where applicable" — per-Program/Site shifts exist alongside shifts tied to a specific Client roster; not every Shift has a Client list).
- **Shift → expected Documents:** the scheduling module is described as tracking whether a shift's required documentation was completed — implying Shift knows which Document types it expects (e.g., a Daily Log per Client on roster, a Shift Checklist for the Site).
- **Open, not decided here (`OQ-28`):** whether a Daily Log entry must reference an actual Shift record (making it dependent on a real clock-in), or whether the Daily Log's AM/PM/Overnight marker stays a free-standing, self-reported field independent of the scheduling system. The evidence leans toward Shift being real and documents referencing it, but the exact linkage mechanism isn't settled by any source document — flagged rather than assumed, given this is the same shape of question that cost three correction rounds on OQ-16.

---

## 5. Document, Version, and Lock

### Document (abstract type)
Every one of the 22 distinct document types found across the 24 source forms (full inventory: `distillation/research/entity-model-input-documents.md`) is an instance of this abstract type. A Document instance carries, at minimum:
- a **Document Type** (one of the 22 canonical types, or a future new type)
- a **scope/grain** — which other entity it's created against: per-Client, per-Site, per-Shift, per-Staff, per-Excursion, or org-level. This is the attribute the OQ-16 saga was ultimately about, and it's now explicit rather than assumed per type.
- an authoring **Staff** reference (with two confirmed exceptions with no authorship field at all in their source form: Client Information and Grocery List — carry the gap forward, don't invent an author)
- a **Lock** state (below)
- a **Version** chain (below)

**Document scope grain, by canonical type** (condensed from the full inventory). The per-Client bucket actually hides two different grains, distinguished by one test: **when a Client transitions to a new Placement, does this document start fresh, or carry across unchanged?** Carries across → **standing**, attached to the Client directly. Starts fresh → **episodic**, attached to the Placement during which it was written (and thus indirectly to the Client through it).

| Grain | Document types |
|---|---|
| per-Client (standing — survives Placement transitions) | Client Information (Face Sheet), Intake Screening Tool |
| per-Placement (episodic — scoped to the Placement during which written) | Individual Needs Assessment, Healing Plan, Case Note, Individual Contact Note, Noteworthy Update, Client Incident Report, Behaviour Tracker, MAR, Monthly Activity Report, Individual Safety Plan, Individual Support Plan |
| per-Placement, per-Shift | Daily Log |
| per-Client, but the intake→Placement relationship is inverted (see note) | Client Intake Form |
| per-Client, standing vs. per-Placement — **open, OQ-32** | Client Service Agreement |
| per-Site | Emergency Preparedness Plan |
| per-Site, per-Shift | Shift Checklist |
| per-Site, per-Month | Monthly Sharp Count Checklist |
| per-Site, per-Week | Grocery List |
| per-Staff, per-Pay-Period | Personal Mileage Form (containing many Personal Mileage Log entries) |
| per-Excursion (many Clients) | Trip Risk Assessment & Excursion Plan |

**Client Intake Form is not Placement-scoped like the rest of the episodic bucket — it's the reverse.** Its client-facing sections are a standing, one-time-per-intake-event Client record, but its "Internal Use Only" block *creates* the Client's first Placement (§3 above) — it can't simultaneously be a child of the Placement it creates. Modeled as a Client-level document whose data seeds a Placement, not as a document scoped to a Placement.

**Client Service Agreement — open, not decided here (OQ-32):** does a Program/Placement change require a newly signed agreement (episodic), or does one agreement stand for the whole Client relationship regardless of Placement changes (standing)? Not derivable from the form audit — a client question, not a synthesis call.

Two documents whose grain touches an entity boundary rather than sitting cleanly on it: the **Client Incident Report**'s Facility Information section (Site vs. external location, OQ-31) and the **Daily Log**'s Shift marker (free-text vs. real Shift reference, OQ-28).

**Known-needed Document types with no source form yet** (tracked as missing material, not modeled with a grain until they exist):
- **Discharge Form/Checklist** (OQ-09) — grain unknown; discovery Q5's discharge-trigger/approval-chain passage is effectively its design brief, not yet a form.
- **Staff Incident Report** (OQ-08) — grain unknown; template "to be provided separately," not received. Possibly the same document as the "Staff-Related Incident Report" generated by sharp/medication discrepancy alerts (see Alert, below) — not resolved here.
- **Behaviour Support Plan** (OQ-10) — grain unknown; referenced by the Trip Risk Assessment form but doesn't exist anywhere across all 24 audited files.

**Two source-file dedups collapse into one Document type each**, not two: forms 18/19 (Monthly Activity Report — byte-identical files) and forms 12/13 (Medication Administration Record — two non-identical files, same name and field set, cosmetic/minor differences only; one authoritative layout still to be chosen is a later, non-structural decision).

### Version
An immutable predecessor of a Document, created when an already-locked Document is unlocked for correction or addendum (RESOLVED, `glossary.md`: unlock "never edits the original locked record — it creates a new version and preserves the original"). Item 4 owns this shape (a Document has a chain of Versions); **retention period for how long Versions must be kept is item 7, blocked on OQ-14.** Healing Plan additionally needs its own review-cadence metadata (version number, review date, next scheduled review, reason for revision) beyond the generic Version chain — PROPOSED, discovery's Open Issues list.

### Lock
A state on a Document (specifically, on its current version): a staff member marking their own documentation complete and no longer editable by them (RESOLVED, `glossary.md`; distinct from Approval). One structural nuance found: the **Shift Checklist locks per shift-section** (Morning/Afternoon/Night are three separate lockable sub-records), not once for the whole document instance — the only document type found with sub-document-level locking.

- **Approval/co-sign** is a separate, later action on top of an already-locked Document, required only for five named categories (RESOLVED, this file's glossary update: Incident Reports; medication-related documentation; client assessments/planning documents; discharge documentation; and a fifth, separately-named "High-Risk Documentation" bucket — serious behavioural incidents, safety reports, missing-person/AWOL documentation, emergency response documentation).
- **Who may unlock, and when** — item 5 (`permission-matrix.md` §9), not item 4. (Canonical default: System Administrator, delegable — see glossary.)

---

## 6. Alert

A system-generated notice, distinct from Approval and distinct from Disclosure. Item 4 owns *what an Alert references and who it can target*; item 7 owns *trigger conditions and the escalation chain*.

- **Alert → source Document: one** (the entry/record that triggered it) — except the 16-hour automated critical-event detection, whose Alert references **an expected-but-missing Document type**, not an existing one (it scans Daily Logs/Case Notes/Behaviour Trackers/Contact Notes for keyword indicators and alerts when no matching Incident Report or Noteworthy Update exists).
- **Alert → Client:** most alert types are Client-scoped (medication, sharp/count discrepancy, critical-event detection); scheduling/attendance alerts (missed clock-in/out, unapproved timesheet changes) are Staff/Shift-scoped instead, not every Alert has a Client.
- **Alert → target Staff (roles): many** — every alert type found targets a role-based list (Team Lead/Supervisor, Program Manager, Director of Operations, Executive Director), not individuals; item 5's resolved role list feeds this once available.
- **Lifecycle, as far as source material defines it:** generated → sent to targets → reviewed. No source document defines an explicit status enum beyond "cannot be dismissed/overridden by staff" for some types — this is a genuine gap for item 7 to raise as its own question, not something item 4 should invent a resolution for.
- **Data-breach alerts are a distinct concept from Disclosure** (below) — an alert about unauthorized/accidental exposure, not a record of an authorized release. Kept as two separate entities, not merged.

---

## 7. Disclosure

A log record of an authorized release of Client information to an external recipient — distinct from a generic access/view audit trail (every Document already needs one of those; that's not Disclosure).

- **Attributes** (PROPOSED, discovery Q20/Q22, consistent shape across both the Indigenous-body/consent-record description and the client/guardian records-request flow — modeled as one Disclosure entity type distinguished by a "recipient category" or "reason" attribute, not two separate entities): recipient (individual/organization), date, purpose, scope of information shared, consent/authorization reference, method of delivery, approving Staff member.
- **Explicitly not Disclosure:** "file access logs, sign-out records" (Q22) — that's the generic per-Document audit trail (who viewed a record), a different entity serving a different purpose. Kept separate so the two don't get conflated.
- **Consent model, OCAP/Métis governance framework, and who may approve a disclosure** — item 7, blocked on **OQ-15**.

---

## Cross-cutting relationship summary

```
Program            1 ── * Subservice
Program            * ── * Site
Site               1 ── * Placement
Client             1 ── * Placement            (sequential, single active at a time)
Client             1 ── * Document              (standing types only: Client Information, Intake Screening Tool)
Placement          1 ── * Document              (episodic types only, see §5 grain split)
Client             * ── * Excursion
Excursion          * ── * Staff                 (named roles: Trip Leader, Driver, First Aid, Medication, Attendance, Emergency Contact)
Staff              1 ── * Staff Assignment
Staff Assignment   * ── 1 Program, * ── 0..1 Site   (Program required; Site optional — concurrent/temporary assignments allowed)
Staff              1 ── * Shift
Shift              * ── 1 Program/Site
Shift              0..* ── * Client
Shift              1 ── 0..* Document           (expected documentation per shift — whether the reference actually exists is OQ-28, not the cardinality)
Document           1 ── * Version
Document           1 ── 0..1 Lock               (a Document has at most one active Lock state)
Alert              * ── 1 Document (source), or 0..1 (expected-but-missing type)
Alert              0..1 ── 1 Client
Alert              * ── * Staff role (target)
Disclosure         * ── 1 Client
```

---

## Open items this artifact surfaces or carries forward (not resolved here — register is `open-questions.md`)

- **OQ-01, OQ-02, OQ-17, OQ-33, OQ-34, OQ-35** — all resolved 2026-09-24; Staff role tier order, Site-based Team Lead/Supervisor scope, and Program Manager cardinality/design above depend on them. **OQ-30, OQ-37** — resolved 2026-09-24/25 (collaborator answered on the client's behalf; not yet relayed): full org chart in scope as Title data, Category layer confirmed as exactly three axes, and every title now has a Hierarchy Tier/Functional Group mapping (mixed client/collaborator/inferred provenance — full table above). **OQ-36** — RESOLVED (2026-09-26): interim Program-Manager-authority gap for Transportation/Training & Consultation is filled by the Director of Operations directly (client-confirmed), resolving Driver's reporting line in the OQ-37 table; the eventual-assignment deciding factor (spare capacity) is a collaborator decision, not client-confirmed. A separate non-blocking residual from OQ-33 (Supervisor Sites spanning two Programs) is carried to item 7, not tracked as a new OQ number.
- **OQ-05** — already resolved; Placement's single-active + secondary-services shape above depends on it.
- **OQ-08** — Staff Incident Report template still missing; naming variant ("Staff-Related Incident Report") noted, not resolved.
- **OQ-13, OQ-23** — already resolved; Client's External Referral ID + Referral Source shape above depends on them.
- **OQ-14** — Version retention period; item 7.
- **OQ-15** — Disclosure consent/OCAP framework; item 7.
- **OQ-16** — already resolved; Daily Log shape above depends on it.
- **OQ-21** — already resolved; deliberately excluded from the Parent/Guardian and Case Worker relationship shape above.
- **OQ-27** — Daily Log's two free-text fields; doesn't block Document's shape, affects its eventual field list.
- **OQ-28** — Document↔Shift linkage, new.
- **OQ-29** — external-party categorization (foster/kinship caregivers), new.
- **OQ-31** — Client Incident Report Facility Information vs. Site, new.
- **OQ-32** — Client Service Agreement grain: standing (one per Client relationship) or episodic (re-signed per Placement change), new, surfaced by this artifact's grain-split exercise.

No open item above blocks this artifact's structure — each is modeled with its uncertainty stated explicitly (a reference left open, a category flagged as possibly needing a third value, a linkage marked TBD) rather than guessed at, per this project's own methodology.
