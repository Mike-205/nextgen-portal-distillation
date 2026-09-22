# Glossary — Canonical Vocabulary

Purpose: every later distillation artifact (entity model, permission matrix, lifecycle, IA/sitemap) uses ONLY the canonical term from this list. Where the client's own material collides on a term, this file either resolves it (RESOLVED, with the deciding source cited) or flags it for the open-questions register (OPEN).

Sources: `NextGen_Portal_Discovery.txt` (D), `NextGen_Scope_Confirmation_Memo.txt` (M), `distillation/forms/*.md` (F#).

---

## Organization structure

**Program / Service** — RESOLVED (superseding the earlier "exactly five" reading of the discovery doc — that count was wrong). There are **six**: Respite Care, Transportation, Group Care Services, Family Reunification Support, Supported Independent Living (SIL), and **Training & Consultation Services**. The discovery doc's "Additional System Requirements" section only listed five and omitted Training & Consultation Services — but that service is already live on NextGen's public site (`next_gen_services/app/programs/training-consulting-services`) and is confirmed as the 6th by direct client conversation. Mental Health is still NOT one of the six — it doesn't appear even as a subservice; it's addressed as clinical content inside other documents (Client Intake Form §9 Medical/§11 Behavioural Support), consistent with D's "cross-program service component" framing.
- **Subservice — new canonical concept, RESOLVED.** Each of the 6 Programs/Services has its own fixed set of subservices, confirmed by direct client conversation and implemented in the redrafted, client-approved Client Intake Form (`recently-sent-forms/CLIENT INTAKE FORM.txt`, print version `Client intake form - print.pdf`), §13 "Service Requested":
  - Respite Care → In-home Respite, Out-of-home/Overnight Respite, Emergency Respite
  - Transportation → Medical Appointments, Family Visits, School Transportation
  - Group Care Services → Residential Group Homes, Therapeutic Support, Life Skill Development
  - Family Reunification Support → Supervised Visits, Reunification Planning, Indigenous-Led Support
  - Supported Independent Living (SIL) → Supervised Housing, Life Skill Training, Employment Support
  - Training & Consultation Services → Professional Development, Workplace/Organizational Training, Professional Records
  - Plus a free-text "Other" option at the top level.
  This two-level model **resolves** the "Program dropdown has 4+ incompatible variants" cross-cutting finding from the forms audit going forward — it's the new canonical taxonomy. It does NOT retroactively fix the inconsistent lists already sitting in the original 19 forms or the other 4 recently-sent forms; reconciling those against this model is entity-model/open-questions-register work, not glossary work.
  - **RESOLVED (2026-09-21, client call):** §13's multi-select at intake collapses into **one primary/main service** (single active Placement, confirmed — D Q7's rule stands). Other services selected that facilitate the main one (e.g. Transportation to medical appointments under a Respite Care placement) are **secondary/facilitating services**, billed inclusively under the main placement rather than creating a second concurrent Placement. Carry "Secondary/facilitating service" into the entity model as an attribute of the active Placement, not a new Placement.
- Variants seen and superseded as program names: "Group Home" (F18/19 — informal name for a Group Care site, not a program), "Mental Health Unit" (appears as a program in F15 sharp-count.html and in the old `PROGRAMS` enum — **RESOLVED 2026-09-21:** scrapped entirely, not a Program, Site, or subservice; any surviving preset referencing it is stale), "Youth Program" (used interchangeably with Group Care in D — treat as the same program).
- Spelling of SIL across the 19 forms is inconsistent: "Supported Independent Living" (majority), "Supportive Independent Living" (F17 grocery-list.html), "Supportive Living" (F13 medication-administration-record.html). Canonical: **Supported Independent Living (SIL)**, per the confirmed 6-service list.

**Site / House / Location** — RESOLVED as synonyms; canonical term **Site**. D uses "houses or service locations" and "site" interchangeably; a Site sits under exactly one or more Programs and is admin-created (e.g., Ravens Nest, Eagles Nest, Golden Bear, Whispering Harmony under Group Care). Not present as a concept in any of the 19 forms — this is a new structural entity the portal introduces.

**Placement** — new term, not used anywhere in the client's material. Introduced here to name the entity that ties a Client to a Program + Site for a date range (see entity model). Client's language has no equivalent word; every mention of "which program/site a client is in" is really describing a Placement. OPEN whether NextGen wants a client-facing name for this concept, or whether it stays purely internal/technical.

**Worker / Staff / Front-Line Staff / Support Worker** — RESOLVED as synonyms for the same tier: any staff member below Team Lead with no supervisory role, working one-on-one with clients (D Q2). Canonical: **Front-Line Staff**. "Worker" alone is ambiguous across the forms (e.g., "Worker Name" field on Client Case Note could mean any staff role) — treat generically as "the staff member completing this form" unless a form specifies otherwise.

**Team Lead / Supervisor / Team Lead/Supervisor** — OPEN. D almost always writes "Team Lead/Supervisor" as one combined role, but the org hierarchy (D Q1) lists "Team Leaders / Supervisors" as a role tier separate from "Program Managers" above and "Front Line Staff" below, without clarifying whether Team Lead and Supervisor are the same position or two adjacent ones. Needs a decision before the permission matrix can assign distinct scopes.

**Director of Operations / Director of Programs / Director of Programs & Operations** — OPEN. The org hierarchy (D Q1) names the role "Director of Programs & Operations" (singular position). Most later answers shorten this to "Director of Operations." A few answers (Q2 clinical documents table) instead say "Program Director" as the approver. Treat all three as the same single role for now — **canonical: Director of Operations** — but flag in open-questions register since "Program Director" could imply a per-program directorship that doesn't exist elsewhere in the doc.

**Executive Director (ED) / CEO** — RESOLVED as the same person/role ("Executive Director / Chief Executive Officer (CEO)" per D Q1 org chart). Canonical: **Executive Director**.

**Client / Youth / Family** — RESOLVED. Canonical: **Client**, regardless of program (a Client in Family Reunification is still a Client, not a separate "Family" entity). Individual form field labels use "Family/Youth Name" (intake-screening.html) or "Child Youth" (incident-report.txt) — these are form-specific labels for the same Client entity, not different entity types.

**Client ID** — RESOLVED (2026-09-21, client call). Not a portal/dev-generated identifier. It's an identifier the referring government body or community agency has *already issued* to the client before intake (e.g., an Alberta Children and Family Services file/case number — ministry renamed from "Children's Services" in 2023, use the current name) — the Intake Form's "Client ID" field captures that pre-existing external ID, it doesn't create one. Whatever internal primary key the portal needs for its own record-keeping is a separate, unrelated concern — don't conflate the two. Research (`distillation/legal-context-research.md`) found no standardized external ID format across referral sources — leans toward one generic "External Referral ID" + "Referral Source" field pair over per-agency fields; formalized as **OQ-23** (NEEDS DECISION) in the register.

---

## Documents / forms

**Case Note vs. Individual Contact Note** — RESOLVED per M open-issues resolution: **Case Note** = staff-to-external-party communication (guardians, family, schools, healthcare, CFS, community agencies). **Individual Contact Note** = client-to-external-party contact (family visits, calls, community visits). F05/F06 show both forms are structurally near-identical blank templates — the distinction is entirely about *who is the subject of the contact*, not the form fields.

**Noteworthy Update / Noteworthy Report** — RESOLVED as the same document; both names appear across D/M. Canonical: **Noteworthy Update** (matches the source form title in F08).

**Daily Log / Client Daily Log Update / "(CU)"-prefixed fields** — RESOLVED. "(CU)" = "Client Update" per D's Open Issues section, but the abbreviation should NOT appear in the portal UI — display as plain "Daily Log" field labels. Canonical document name: **Daily Log**.

**Shift Log** — new document, CONFIRMED to exist as a concept but not yet designed (2026-09-22, client call). **Correction to an earlier entry here (2026-09-21) that said handover was just the Daily Log's Follow Through Notes field with no separate document — that was wrong; the discovery doc independently describes a distinct "staff communication log," reviewed at the start of every shift, separate from Daily Log review.** Confirmed scope: **per-Client** (not per-Site), no existing paper/prior version — needs designing from scratch, and does **not** replace the Shift Checklist's (F14) "Shift Exchange" checkboxes (both exist; the checklist stays a pure confirmation gate). Still open: what actually distinguishes its content from the Daily Log's, given the client described them as "similar in some way" — see `open-questions.md` OQ-24. Do not treat Daily Log's "(CU) Follow Through (notes)" field as the handover mechanism going forward; that reading is retracted.

**Incident Report (Client) vs. Staff Incident Report** — RESOLVED as two separate documents going forward (M Open Issues): **Client Incident Report** = the existing form (F09, confirmed incomplete — ends after Section 2) plus an attachment slot for the official Government of Alberta incident form. **Staff Incident Report** = a new, fully digital form using a NextGen template not yet provided (OPEN — blocked on that template).

**MAR / MAR Sheet / Medication Administration Record** — RESOLVED per M: keep the title **Medication Administration Record (MAR)**. Note the forms audit found F12 (mar-sheet.html) and F13 (medication-administration-record.html) are NOT byte-identical despite M's claim — see open-questions register; the *title* decision stands regardless of which file's exact layout is kept.

**Monthly Activity / Activity Calendar / Monthly Activity Report** — OPEN, do not treat as resolved. M says "remove the Monthly Activity Form," but F18/F19 show "Monthly Activity" and "Activity Calendar" are literally the same file under two filenames (byte-identical), and D's Q2 shift-walkthrough still lists "Monthly Activity Report" as a live front-line document staff complete for client participation/community engagement. There is exactly one form here, not two competing ones — the open question is whether it survives at all, not which duplicate to keep. Canonical name pending resolution: **Monthly Activity Report**.

**Behavior Tracker / Behaviour Tracker** — RESOLVED as spelling only (Canadian client-facing spelling): canonical **Behaviour Tracker**. Same document referenced in code/schema as "BehaviorTracker."

**Sharp Count Checklist / Monthly Sharp Count Checklist** — RESOLVED as the same document. Canonical: **Monthly Sharp Count Checklist**.

**Shift Checklist** — RESOLVED, single form, no naming collision. Note the discovery doc's claim that it has "no tasks listed" is REFUTED by the forms audit (F14) — it has full fixed task lists; the real gap is the tasks aren't program-specific yet.

**Personal Mileage / Mileage Form / Personal Mileage Log** — RESOLVED as the same document, two granularities (a Personal Mileage record contains many Personal Mileage Log entries, per the existing schema's own structure, confirmed consistent with F16).

**Client Information / Face Sheet** — RESOLVED as the same document (F01 on-page title is "CLIENT INFORMATION" / "FACE SHEET" used interchangeably in intake terminology). Canonical: **Client Information**.

**Discharge Form / Discharge Checklist** — described in detail in D (Q5) but no source file exists among the 19 forms provided. Treat as a **new document to be designed**, not an existing one to be digitized.

---

## Actions / states

**Lock / Save & Lock / Finalize** — RESOLVED as one action: a staff member marking their own documentation as complete and no longer editable by them (D Q13). Locking is NOT the same as approval.

**Approve / Review / Sign-off / Co-sign** — RESOLVED as a separate, later action performed by a supervisor/reviewer on top of an already-locked document. Not all documents require it — only the high-risk category listed in D Q13 (Incident Reports, medication-related documentation, clinical assessments/plans, discharge documentation).

**Unlock / Correction / Addendum** — RESOLVED as a restricted action (System Administrator by default, delegable) that never edits the original locked record — it creates a new version and preserves the original (D "Document Locking and Record Integrity").

**Escalate / Escalation** — used loosely throughout D for "notify someone more senior" — not yet a distinct system state; folds into the alert/notification model (cross-cutting concerns doc).

---

**Case Worker (external) vs. "Case Manager" (internal)** — RESOLVED (2026-09-21, client call). "Case Manager," "Case Worker," and "legal guardian" are, in the client's own framing, effectively one external role: when a family isn't functioning (abuse/neglect/addiction) and a court removes children from parental care, a Children and Family Services employee is assigned to act and make decisions in the parents' place. Where the parent retains guardianship, the parent continues to function as parent/guardian instead. **Canonical term: Case Worker** (client's explicit instruction, for clarity). Internally, if "Case Manager" is used at all, it refers to a **Team Lead or Program Manager acting in that capacity** — not a distinct standalone NextGen role.
- **Entity-model implication:** a Client needs two distinct external-party relationship concepts — **Parent/Guardian** and **Case Worker** — not one collapsed field, since custody status determines which applies (possibly both, at different points in the client's history).
- **New open item surfaced:** "Program Manager" is a title not previously seen in the org chart or discovery doc — see `open-questions.md` OQ-17.
- **Research nuance (2026-09-21, `legal-context-research.md`):** "Case Worker" matches Alberta's own public-facing "caseworker" term and the formal job title "Child Intervention Caseworker" — well-supported. But a caseworker's actual authority varies by court order type (Supervision Order / Temporary Guardianship Order / Permanent Guardianship Order / Custody Agreement) — under a PGO the Director is the child's sole guardian; under lighter orders the parent retains real authority. Whether the portal needs this granularity is **OQ-21** (open). Also open: whether referrals ever come through a Delegated First Nations Agency with different title conventions (**OQ-22**).

**Funding Source** — new canonical list, RESOLVED as of the Client Intake Form: PDD, FSCD, AISH, Jordan's Principle, Private Pay, Insurance, Other. Not previously captured anywhere in the discovery doc or original 19 forms — feed into the entity model as a Client attribute.

## Still-collision terms carried to the open-questions register (not resolved here)

- Team Lead vs. Supervisor (distinct roles or one role, two names?)
- Director of Operations vs. Program Director (one role or two?)
- "Program Manager" as a title — newly surfaced (2026-09-21 client call), not previously seen in the org chart; needs reconciling with the two items above (OQ-17)
- Monthly Activity Report's survival (remove per memo vs. still-live per discovery doc walkthrough)
- Undefined "Behaviour Support Plan" document (referenced in Trip Risk Assessment, doesn't exist anywhere across all 24 form files audited)
- Shift Log vs. Daily Log content distinction — both per-Client, client called them "similar in some way," but the actual difference in what each should capture is unanswered (OQ-24)
