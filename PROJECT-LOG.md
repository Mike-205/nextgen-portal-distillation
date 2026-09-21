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
- ~~OQ-16~~ (shift handover mechanism) → Daily Log's existing "Follow Through Notes" field, not a separate Shift Log. One workflow question left open (ack/read-receipt for handover), deferred to item 7.

Full detail and exact resolution text: `distillation/open-questions.md`, inline at each OQ number, plus the 2026-09-21 batch entry in the resolved-items log at the bottom.

**Net effect: item 4 (Entity Model) is no longer blocked.** All five structural decisions needed to start it are answered.

### New — surfaced while resolving the above

- **OQ-17** ("Program Manager" title, not previously seen in the org chart) — added to Roles & Org Structure section, feeds the same permission-matrix gate as OQ-01/OQ-02 below.

### Will become immediate soon — don't block item 4, but block item 5 (Permission Matrix), right after

- **OQ-01** (Team Lead vs. Supervisor — one role or two tiers) — the matrix is role × document × action × scope; can't build the role axis with this unresolved.
- **OQ-02** (Director of Operations / Program Director / Director of Programs & Operations — same position?) — same reason, at the top of the approval chain.
- **OQ-17** (Program Manager, new) — same reason; now a third title needing reconciliation, not just two.

### Later — block item 7 (Cross-Cutting Concerns), not yet urgent

- **OQ-14** (actual required retention period, not the placeholder 7-year figure) — blocks the retention & legal-hold sub-section outright.
- **OQ-15** (has Indigenous consultation on data handling happened yet) — blocks the Indigenous data governance sub-section outright.

## Active background research

- **`distillation/legal-context-research.md`** (in progress, launched 2026-09-21) — collaborator flagged that Canadian privacy/data law and Indigenous data governance need substantial grounding before item 7 gets designed, not just decided ad hoc. Covers: (1) Canadian/Alberta child-welfare custody & case-worker terminology, to ground the Parent/Guardian vs. Case Worker distinction from OQ-03; (2) how government/community-issued client IDs actually work in Alberta, to ground OQ-13; (3) the applicable federal/provincial privacy framework (PIPEDA, Alberta PIPA/FOIP, Child, Youth and Family Enhancement Act, Health Information Act if relevant) and OCAP Indigenous data sovereignty principles. This is background research to inform item 7, not a client answer — anything it surfaces that only the client/counsel can settle goes into `open-questions.md`, not decided here.

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
