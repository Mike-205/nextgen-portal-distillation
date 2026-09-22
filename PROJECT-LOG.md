# Project Log — Status, Blockers, Deviations

Living tracking doc for the distillation effort. Update this whenever an artifact completes, a blocker opens/closes, or the actual work diverges from what `CLAUDE.md`'s artifact set originally assumed. This file is about *process state*; `distillation/open-questions.md` is about *content gaps to send to the client*. Don't duplicate entries between them — cross-reference by OQ number instead.

---

## Done so far

- Original 19 forms audited → `distillation/forms/01–19.md` + `00-index.md`
- Recently-sent 5 forms audited → `distillation/forms/20–24.md`
- Glossary (canonical vocabulary) → `distillation/glossary.md`
- Open Questions & Decisions Register started → `distillation/open-questions.md` (16 entries)
- Git repo initialized for this workspace (was untracked until now)

## Not started (per `CLAUDE.md` artifact set, in dependency order)

4. Entity model — **next up**
5. Permission matrix
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

### New — surfaced while resolving the above

- **OQ-17** ("Program Manager" title, not previously seen in the org chart) — added to Roles & Org Structure section, feeds the same permission-matrix gate as OQ-01/OQ-02 below.

### Will become immediate soon — don't block item 4, but block item 5 (Permission Matrix), right after

- **OQ-01** (Team Lead vs. Supervisor — one role or two tiers) — the matrix is role × document × action × scope; can't build the role axis with this unresolved.
- **OQ-02** (Director of Operations / Program Director / Director of Programs & Operations — same position?) — same reason, at the top of the approval chain.
- **OQ-17** (Program Manager, new) — same reason; now a third title needing reconciliation, not just two.

### Later — block item 7 (Cross-Cutting Concerns), not yet urgent

- **OQ-14** (actual required retention period, not the placeholder 7-year figure) — blocks the retention & legal-hold sub-section outright. Checked against research 2026-09-21, still genuinely unresolved — needs the client directly, not researchable from public sources.
- **OQ-15** (has Indigenous consultation on data handling happened yet) — blocks the Indigenous data governance sub-section outright. Research added a second dimension: OCAP is First-Nations-specific, not universal — Métis/Inuit governance is separate and needs its own answer.
- **OQ-18** (PIPA coverage bucket — full vs. commercial-activity-only, depends on NextGen's incorporation structure) — needs counsel.
- **OQ-19** (HIA custodian/affiliate status for MAR data) — needs counsel; research leans toward "not a custodian, PIPA applies instead" but flagged as inference only.
- **OQ-20** (funding-agreement Canadian-residency clauses) — needs a contract review only the client can do.

### New — surfaced by research, not yet urgent but tracked

- **OQ-21** (does the entity model need court-order-type granularity — Supervision/TGO/PGO/Custody Agreement — or is Parent/Guardian-vs-Case-Worker enough) — a scope call for items 4–5.
- **OQ-22** (Delegated First Nations Agency referral title conventions) — worth asking the client directly.
- **OQ-23** (Client ID: one generic External Referral ID + Referral Source field, vs. per-agency fields) — NEEDS DECISION, ours to make when building item 4, flagged not silently decided.

## Background research — completed

- **`distillation/legal-context-research.md`** (launched and completed 2026-09-21) — covers Alberta child-welfare custody/case-worker terminology (grounds OQ-03), how referral client IDs actually work (grounds OQ-13/OQ-23), and the applicable privacy/health-information/Indigenous-data-sovereignty framework (PIPEDA, PIPA, the 2025 FOIP→ATIA/POPA split, HIA, OCAP). One correction propagated back into `glossary.md` and `open-questions.md`: the ministry is currently named **"Children and Family Services,"** not "Children's Services" (renamed 2023) — fixed everywhere that had the old name. Findings folded into OQ-03/13/15 as nuance and opened OQ-18 through OQ-23 above. Nothing in the research was treated as a client answer — every "needs confirmation" item became a register entry, not a silent decision.

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
