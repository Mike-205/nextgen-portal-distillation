# Project Log — Status, Blockers, Deviations

Living tracking doc for the distillation effort. Update this whenever an artifact completes, a blocker opens/closes, or the actual work diverges from what `CLAUDE.md`'s artifact set originally assumed. This file is about *process state*; `distillation/open-questions.md` is about *content gaps to send to the client*. Don't duplicate entries between them — cross-reference by OQ number instead.

---

## Done so far

- Original 19 forms audited → `distillation/forms/01–19.md` + `00-index.md`
- Recently-sent 5 forms audited → `distillation/forms/20–24.md`
- Glossary (canonical vocabulary) → `distillation/glossary.md`
- Open Questions & Decisions Register started → `distillation/open-questions.md` (OQ-01–OQ-37 issued, 20 open, 15 resolved)
- **Entity model (item 4)** → `distillation/entity-model.md` (2026-09-23). Built from two provenance-tagged evidence files gathered via background forks: a document inventory grounded in all 24 form audits (`distillation/research/entity-model-input-documents.md`, 22 distinct documents) and an entity-bearing-statement extract from the discovery doc/scope memo (`distillation/research/entity-model-input-discovery.md`). Covers Program/Subservice, Site, Client, Parent/Guardian & Case Worker, Placement, a new **Excursion** entity (required by the Trip Risk Assessment form — many-Clients-per-record, not in `CLAUDE.md`'s original illustrative entity list), Staff/Staff Assignment/Shift, Document/Version/Lock, Alert, and Disclosure. Explicitly scoped as shape-only, deferring policy (who/when/retention/consent) to item 7. Five new open questions surfaced and registered (OQ-28–OQ-32 — including OQ-32, a per-Client-vs-per-Placement grain question for the Client Service Agreement found while splitting the Document grain table into standing vs. episodic buckets), three existing ones strengthened (OQ-01, OQ-08, OQ-17); none block the model's structure — each is modeled with its uncertainty stated explicitly rather than guessed. A methodological caveat was also added to the register: NextGen currently has **zero active clients** (Scope Memo §2), so the discovery doc's "current process" language describes intended/designed process, not tested practice.
- Git repo initialized for this workspace (was untracked until now)

## Not started (per `CLAUDE.md` artifact set, in dependency order)

5. Permission matrix — **next up, unblocked with real values.** OQ-30 and OQ-37 both resolved (2026-09-24/25): full org chart in scope as Staff.Title data, Category confirmed as exactly three axes (Hierarchy Tier / Functional Group / Engagement Type), and every title now has a Hierarchy Tier/Functional Group mapping — full per-title table in `entity-model.md`, mixed client/collaborator/inferred provenance per cell. Only **OQ-36** remains open — who covers Program-Manager-level authority for Transportation/Training & Consultation (also blocks Driver's specific reporting line in that table); doesn't block the matrix's structure. OQ-01/OQ-02/OQ-17/OQ-33/OQ-34/OQ-35 all resolved 2026-09-24, see Blockers below.
6. Client lifecycle state machine
7. Cross-cutting concerns (locking/versioning, alerts, retention, Indigenous data governance, residency)
9. Information architecture + sitemap
10. UX/UI guides
11. Dev guides
12. Independent review of collaborator-redrafted Client Intake Form (deferred, low priority)

---

## Blockers

### Resolved 2026-09-21 (client call, relayed by collaborator) — entity model unblocked

- ~~OQ-05~~ (Placement cardinality) → single-active, confirmed. Secondary/facilitating services bill inclusively under the main Placement.
- ~~OQ-04~~ (Mental Health Unit) → scrapped entirely; not a Program, Site, or subservice.
- ~~OQ-13~~ (Client ID) → externally-issued referral ID (government/community), not portal-generated. Portal still needs its own internal key regardless — standard system design, no client input needed there.
- ~~OQ-03~~ (Case Manager role) → external role = Case Worker (= Case Manager = legal guardian, in client's framing); internal usage maps to Team Lead/Program Manager. Opened **OQ-17** as a result (see below).
- ~~OQ-16~~ (shift handover mechanism) → **initially** resolved as "Daily Log's existing Follow Through Notes field, not a separate Shift Log" — **this was wrong, corrected 2026-09-22 below.**

Full detail and exact resolution text: `distillation/open-questions.md`, inline at each OQ number, plus the 2026-09-21 batch entry in the resolved-items log at the bottom.

**Net effect: item 4 (Entity Model) is no longer blocked.** All five structural decisions needed to start it are answered — with one of them (OQ-16) later corrected, see immediately below.

### Correction, 2026-09-22 — OQ-16 was resolved wrong; process note

Collaborator took the OQ-16 resolution back to the client and flagged the alternative (a separate Shift Log) as something still worth weighing. Client pushed back: a Shift Log is real and distinct. Going back to the discovery doc surfaced a **"staff communication log"** mentioned 4 separate times, independently of this conversation, that the original OQ-16 resolution missed entirely — a genuine miss, not new information the client withheld. Corrected via three follow-up questions, answered 2026-09-22:

- Shift Log is **per-Client** (not per-Site/House).
- **No existing version** — needs designing from scratch. Client's words: "will serve similar to daily log in some way."
- Does **not** replace the Shift Checklist's exchange checkboxes — both exist.

**New blocker opened: OQ-24** — what actually distinguishes Shift Log content from Daily Log content. Both are now per-Client and described by the client as "similar," so this needs a real answer before the entity model can treat them as two genuinely separate document types, rather than risking an unstated-difference duplicate like several already found in the original 19-form audit.

**Process lesson, not just a content correction:** worth double-checking future "resolved via client call" entries against the discovery doc's own text before marking them settled — this one would have propagated a wrong document model into the entity model (item 4) if the collaborator hadn't tested it with the client first.

### Second correction, 2026-09-22 (advisor review) — the 2026-09-22 fix above was itself wrong

The "corrected" version immediately above conflated two different things: it treated the discovery doc's "staff communication log" as *the same thing* the client meant by "Shift Log." On review, that's very unlikely — the discovery doc's staff communication log is consistently described as a site/shift-level artifact (grouped with medication/narcotic count and sharp count, no client tie; the Shift Checklist's "Staff Communication Log Read" task row sits on a form with no client field at all). The client's "Shift Log" is per-Client, which the client stated directly.

Separately, re-reading the client's actual trigger phrase — *"new logs are started at the beginning of every shift and there can be 2 or more shifts in a day"* — is at least as consistent with **"the Daily Log's name is wrong"** as with **"we need a second document."** The Daily Log (form 07) is already shift-grained (has its own AM/PM/Overnight box), and the three follow-up questions asked on 2026-09-22 never actually tested the rename hypothesis against the separate-document hypothesis — both readings fit all three answers equally.

**Corrected split, now in `open-questions.md`:**
- **OQ-24** — rewritten as the actual discriminating question: is "Shift Log" the Daily Log renamed, or a second form alongside it? Framed as a one-line either/or for the client.
- **OQ-25** — new, MISSING MATERIAL: the discovery doc's "staff communication log" is a real, likely site/shift-level artifact, referenced 4× but never provided as a form and never asked about directly. It surfaced by accident while chasing the Shift Log question.

`glossary.md`'s "Shift Log" entry downgraded from an assertive "CONFIRMED to exist as a new document" to explicitly unresolved, with the rename-vs-separate question stated directly. Neither OQ-24 nor OQ-25 blocks item 4 from starting on everything else, but the Document entity list for item 4 needs one of these two answered before it can be finalized.

### Final resolution, 2026-09-22 — one document all along

Client answered OQ-24 and OQ-25 directly: **there is one document, not two or three.** "Shift Log" is the Daily Log, correctly understood as shift-grained (matches its existing AM/PM/Overnight structure). The discovery doc's "staff communication log" also turned out to be the same Daily Log, not a third artifact — client's explicit instruction: retire that term entirely to avoid this exact confusion recurring. Handover runs through the Daily Log's existing "Follow Through (notes)" field — which is, in substance, where the very first (2026-09-21) resolution landed before two rounds of overcorrection.

**Net effect on item 4 (Entity Model):** simpler than it looked mid-investigation — one Document type (Daily Log), created once per shift. No new Shift Log or Staff Communication Log entities needed. OQ-16, OQ-24, and OQ-25 are all closed.

**Why the false starts were still worth it:** the first "resolved" answer (Follow Through Notes) was correct in substance but hadn't actually been tested with the client — it took reopening it, then the advisor catching a real conflation in the correction itself, to get a client answer precise enough to close this properly. Worth keeping the habit of testing "resolved" register entries against the client rather than trusting our own inference, especially where a discovery-doc phrase (like "staff communication log") could plausibly name something real that was never actually provided.

### New — surfaced while resolving the above

- **OQ-17** ("Program Manager" title, not previously seen in the org chart) — added to Roles & Org Structure section, feeds the same permission-matrix gate as OQ-01/OQ-02 below.

### Resolved 2026-09-24 (client call, relayed by collaborator, three batches) — role hierarchy fully settled, item 5 almost unblocked

**First batch:**
- ~~OQ-01~~ (Team Lead vs. Supervisor) → two distinct tiers confirmed, Supervisor supervises Team Leads. New sub-question opened: **OQ-33** (scope unit — Programs or Sites?).
- ~~OQ-02~~ (Director of Operations / Program Director / Director of Programs & Operations) → confirmed same single position ("Yes, same"). Canonical: Director of Operations.
- ~~OQ-17~~ (Program Manager) → confirmed distinct tier, supervises Supervisors. Client said Transportation and Training & Consultation "report to the existing program managers" (no dedicated 5th/6th) — **later reconciled in the third batch below as intent language, not a current assignment.** New sub-questions opened: **OQ-34** (which specific one(s)), **OQ-35** (design provisioning for a not-yet-existing Program Manager, which the client also asked about unprompted).

**Second batch, same conversation continued:**
- ~~OQ-33~~ → **resolved: the scope unit is Site, not Program.** Client's words: "several sites," then clarified "Team lead is one site." Corrects OQ-01's original "program" wording to "Site." Full confirmed hierarchy: **Director of Operations > Program Manager > Supervisor > Team Lead > Front-Line/Support Staff**, with Team Lead = one Site, Supervisor = several Sites. One residual (Site↔Program is many-to-many, so a Supervisor's Sites could span two Programs) carried to item 7, not a new OQ number.
- **OQ-34** → client had no answer as of this call. At the collaborator's request (per `CLAUDE.md`'s "distill and present options" working preference), four options (A/B/C/D) drafted in `distillation/open-questions.md`, tagged PROPOSED — **superseded in the third batch below.**
- ~~OQ-35~~ → **resolved: client approved** ("cool") our design framing — Program Manager modeled as data assignable per Program, not a fixed four-seat enum — including the collaborator's own framing of what that makes possible: **"1 program will map to 1 program manager"** (one-to-one is the target, collaborator's exact words). The 0..1 half (a Program can have *none* assigned) comes from OQ-34's client fact, not from this exchange; the possibility of one PM temporarily holding more than one Program is our own PROPOSED design inference, not stated by either party — an earlier write-up conflated all three into one client-stated cardinality, caught on advisor review and corrected in `open-questions.md`, `glossary.md`, and `entity-model.md`. Client did independently add: "another program manager can be appointed to" — i.e. dedicated per-program PMs are the expected direction over time.

**Third batch — collaborator asked OQ-34 directly:** "is there a specific existing Program Manager(s) Transportation and Training & Consultation report to, or is it any Program Manager with spare capacity?"
- ~~OQ-34~~ → **resolved: client said "there's none currently."** No existing Program Manager is actually assigned to either program today — this reconciles OQ-17's original "report to the existing program managers" as intent, not current state (consistent with the register's zero-active-clients caveat). The second batch's four options assumed an existing assignment already existed; that premise was wrong, so they're superseded, kept for traceability, not presented to the client.
- Collaborator then floated "so any of the program managers who has spare capacity" — client said **"kind of."** Recorded as a hedge (collaborator's proposed mechanism, only partially agreed), not a confirmed policy. New item opened: **OQ-36** — who exercises Program-Manager-level authority for the two programs in the meantime, and what actually decides the eventual assignment. This is the one still worth relaying to the client.

**Still blocking item 5:** nothing structurally — see the fourth/fifth/sixth batches below, OQ-30 and OQ-37 are both resolved. OQ-36 remains open and feeds item 7's delegation work (plus one cell in OQ-37's table, Driver's reporting line); it doesn't block the matrix's shape, but the matrix does need to represent "Program with no Program Manager assigned" as a real state. Full detail: `distillation/open-questions.md`.

### Resolved 2026-09-24 (fourth batch, collaborator answered on the client's behalf, not yet relayed to the client) — item 5's scope question settled, axis set still open

- ~~OQ-30~~ → **resolved: full ~25-title org chart is in scope**, as Staff.Title data (not a fixed enum, same pattern as Program Manager). The permission matrix doesn't key off Title directly — it keys off a separate **Category** layer. Collaborator's words: "the entity/permission model is going to build out the full org chart now then categorize them, such that we have operationally-referenced categories/tiers among others" — confirmed on follow-up ("several") that this means multiple category axes, not one. Asked directly whether Hierarchy Tier / Functional Group / Engagement Type was the complete set: collaborator answered **"no thats it"** — axis set **confirmed at exactly these three, no more.** Values on Functional Group and Engagement Type remain PROPOSED, not confirmed (glossary's "Staff Title vs. Category" entry has the candidate values). New item opened: **OQ-37** — now scoped to those axis values, plus which specific title maps to which value; several placements (the five senior/functional managers, the seven Clinical Professional titles, the ungrouped Family Support Workers/CYCWs/Support Workers cluster, System Administrator having no org-chart title at all) are genuinely unclear from the source material and need either a client answer or a further internal call.

**No longer blocking item 5 structurally — both the scope question and the axis set are settled.** OQ-37 blocks the matrix's *axis values and populated cells* only. The matrix can start on the confirmed Hierarchy Tier chain now; Functional Group and Engagement Type need their values confirmed before the matrix leans on them. OQ-36 still feeds item 7's delegation work as before.

### Resolved 2026-09-25 (sixth batch, client answers relayed by the collaborator) — item 5 fully populated, OQ-37 closed

Collaborator took the drafted client-facing question (three parts: Reporting Level, Department, Employment Type) to the client and relayed the answers:
1. The five senior/functional managers "report to the director of operations" — resolves their reporting line. Does **not** confirm they share Program Manager's Hierarchy Tier; that label stays our own inference.
2. Department groupings: "everything is corrected [correctly] listed" — confirms Clinical, Direct Care (its own group, not folded into Clinical — resolves the org chart's ambiguous ungrouped cluster), Administrative & Compliance, Cultural, and Executive/Corporate exactly as drafted.
3. Volunteers: "have their own category cos it can be full time, part time, relief but on voluntary basis and that's right, they need restricted portal access" — client-confirmed as its own category (not folded into a schedule list) with restricted portal access; modeling it as two attributes (schedule basis + an orthogonal Paid/Voluntary flag) is our own INFERRED read, pending the collaborator's OK.

Collaborator then added their own call, not relayed from the client: "for the questions that are left hanging i think we can infer and/or try to map them correctly i.e., sth like system administrator its there, and its a title that someone actually holds and not a permission that can be granted to any staff member" — authorizing inference for the remaining gaps, with System Administrator's realness as a title (not on D Q1's org chart at all) as their own example.

- ~~OQ-37~~ → **resolved, mixed provenance.** Full per-title Hierarchy Tier/Functional Group table now in `entity-model.md`'s Staff section, every cell tagged CLIENT, COLLABORATOR, or INFERRED. Well-grounded inferences (Family Support Workers/CYCWs/Support Workers → Front-Line-equivalent tier) sit alongside weak guesses (Training & Staff Development Coordinator, Maintenance & Facilities Coordinator's reporting lines) and one deliberately unguessed cell (Driver's reporting line, blocked on OQ-36, not inferred).

**Item 5 (Permission Matrix) is no longer blocked on populated Staff Category values.** Only OQ-36 remains open, and it affects one cell (Driver) plus item 7's delegation work, not the matrix's overall shape. **Follow-up owed to the collaborator, not yet sent:** the list of INFERRED cells for review, and confirmation that the Volunteer model (kept inside Engagement Type as a paid/voluntary attribute, not folded into schedule basis) is the right call.

### Later — block item 7 (Cross-Cutting Concerns), not yet urgent

- **OQ-14** (actual required retention period, not the placeholder 7-year figure) — blocks the retention & legal-hold sub-section outright. Checked against research 2026-09-21, still genuinely unresolved — needs the client directly, not researchable from public sources.
- **OQ-15** (has Indigenous consultation on data handling happened yet) — blocks the Indigenous data governance sub-section outright. Research added a second dimension: OCAP is First-Nations-specific, not universal — Métis/Inuit governance is separate and needs its own answer.
- **OQ-18** (PIPA coverage bucket — full vs. commercial-activity-only, depends on NextGen's incorporation structure) — needs counsel.
- **OQ-19** (HIA custodian/affiliate status for MAR data) — needs counsel; research leans toward "not a custodian, PIPA applies instead" but flagged as inference only.
- **OQ-20** (funding-agreement Canadian-residency clauses) — needs a contract review only the client can do.

### Resolved 2026-09-23 — both feed directly into item 4

- ~~OQ-21~~ (court-order-type granularity) — **client answer.** Not needed now; Parent/Guardian-vs-Case-Worker split is sufficient for NextGen's purposes. Client explicitly asked that the order-type research not be discarded — keep the entity model open to adding it later, don't build it now.
- ~~OQ-23~~ (Client ID field structure) — **internal decision, collaborator-confirmed** (this was always ours to make, per its NEEDS DECISION tag, not the client's — not a client call). Confirmed: one generic External Referral ID field + a paired Referral Source field, not per-agency fields.

### New — surfaced by research, not yet urgent but tracked

- **OQ-22** (Delegated First Nations Agency referral title conventions) — worth asking the client directly.

### New — surfaced while gathering entity-model evidence, 2026-09-23 — none block item 4 outright, modeled with the uncertainty flagged instead

- **OQ-28** (does a Daily Log reference a real scheduled/clocked Shift record, or stay a free-standing marker) — entity model will treat Shift as first-class and note the exact Document↔Shift link as open, per this OQ.
- **OQ-29** (foster/kinship caregiver access — Parent/Guardian vs. distinct external-user category) — a genuine discovery-doc self-contradiction (Q1 vs. Q18/Q25). Affects the entity model's external-party categories and item 5's permission matrix.
- ~~OQ-30~~ (is the full ~25-title org chart in scope now, or just the ~7 operationally-referenced tiers) — **resolved 2026-09-24, see below.**
- **OQ-31** (Client Incident Report's "Facility Information" — a NextGen Site, or an external caregiver's location) — affects how that one document's Site-like field gets modeled.
- **OQ-32** (Client Service Agreement — standing per-Client document, or episodic per-Placement) — surfaced by the entity model's own grain-split exercise, not the forks; doesn't block the model, the document is just marked open in the grain table.
- ~~OQ-37~~ (the Category axis set OQ-30 calls for, its values, and which of the ~25 org-chart titles maps to which value) — **resolved 2026-09-25, see sixth batch below.**

## Background research — completed

- **`distillation/research/legal-context-research.md`** (launched and completed 2026-09-21) — covers Alberta child-welfare custody/case-worker terminology (grounds OQ-03), how referral client IDs actually work (grounds OQ-13/OQ-23), and the applicable privacy/health-information/Indigenous-data-sovereignty framework (PIPEDA, PIPA, the 2025 FOIP→ATIA/POPA split, HIA, OCAP). One correction propagated back into `glossary.md` and `open-questions.md`: the ministry is currently named **"Children and Family Services,"** not "Children's Services" (renamed 2023) — fixed everywhere that had the old name. Findings folded into OQ-03/13/15 as nuance and opened OQ-18 through OQ-23 above. Nothing in the research was treated as a client answer — every "needs confirmation" item became a register entry, not a silent decision.

### Later still — block item 9 (IA/Sitemap) and item 11 (Dev Guides), content-completeness rather than shape

- **OQ-06** (Monthly Activity Report in or out) — affects the Document list a sitemap would enumerate.
- **OQ-07 – OQ-12** (Incident Report internal narrative scope, Staff Incident Report template, Discharge Form, Behaviour Support Plan, Sharp Count/Shift Checklist task lists for 4 of 6 programs, Medicine Wheel goal areas) — these are missing-material gaps, not structural ones; the entity model and lifecycle can be built around them, but the IA/sitemap and dev guides need the actual lists/templates to enumerate real screens.

---

## Deviations from the original plan

- **Scope changed from "digitize 19 forms" to "build the full agency operating system."** This is the big one and it's already the accepted premise of the whole project (see `CLAUDE.md` history), not a live risk — logged here only for traceability.
- **Client sent a second, unplanned round of 5 forms** (`recently-sent-forms/`) after discovery had already concluded. Original plan assumed one form set; this added a second audit pass (item 2) and revealed a third, still-different program taxonomy in the Client Service Agreement (see `distillation/forms/21-client-service-agreement.md`).
- **Programs/Services count changed 5 → 6** with a Program→Subservice hierarchy, confirmed directly by the client outside the discovery doc — not something the discovery doc itself settled. Logged in `open-questions.md`'s resolved-items log.
- **The Client Intake Form was redrafted and client-approved outside the normal audit → open-questions → decision flow.** My collaborator drafted it directly and got sign-off before the independent factual review this workspace's methodology calls for. Deferred, tracked as item 12 — means one client-facing artifact is already live without having gone through the same scrutiny as everything else here.
- **The Scope Confirmation Memo contains at least one factual claim the forms audit later refuted** — it asserted the two MAR files were byte-identical; the audit found they weren't (naming decision stood anyway, see resolved-items log). Worth remembering the memo is a planning artifact, not infallible ground truth either — it gets audited like everything else, not taken at face value.
- **The Open Questions Register itself became a bigger, more formal deliverable than originally scoped** — it started as scattered notes inside `glossary.md` and session context, then got promoted to its own client-facing artifact (item 8) with a provenance-tagging convention. Process addition, not in the original 12-item list until this happened.
