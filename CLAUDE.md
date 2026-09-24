# NextGen Support Services — Portal Distillation Workspace

**This is not a code repository.** No application code lives or gets written here. This is a planning/analysis workspace for distilling client-provided material into an unambiguous specification before any build starts. Read this file at the start of every session in this directory — it exists so the human doesn't have to re-explain the project from scratch each time.

## What this project actually is

NextGen Support Services is a non-profit in Edmonton, Alberta (Treaty 6 territory) providing trauma-informed, culturally responsive support to Indigenous and marginalized children, youth, and families. They engaged a dev team to build a staff portal.

**History, in order:**
1. Original engagement: digitize ~19 existing paper/HTML forms (Daily Logs, Case Notes, Incident Reports, MAR, Behaviour Tracker, etc.) into a web app. This was built as `../next_gen_services` (sibling directory, Next.js 16 + Prisma 7 + NextAuth) — see that repo's `ABOUT.md` for a full technical overview.
2. My human collaborator pushed back on "just digitize the forms" — argued that without understanding the real workflows behind each form, digitizing 1:1 just moves paper-form ambiguity into database columns. Ran a two-round discovery process with the client instead.
3. Discovery produced `NextGen_Portal_Discovery.txt` (extracted from a `.docx`; non-technical discovery Q&A covering people/roles, client lifecycle, per-form workflows, compliance/privacy/Indigenous data sovereignty, and portal expectations) and `NextGen_Scope_Confirmation_Memo.txt` (documents that discovery blew the scope open: this is no longer a "documentation portal," it's the org's full operating system — case management, staff scheduling, GPS time clock/attendance, payroll timesheet export, in-house messaging, automated critical-event detection, funder billing support).
4. **Client confirmed the full re-scope** (not a phased/priority-list path) — build toward the complete platform vision described in the discovery doc and memo.
5. Client then sent a **second round of forms** post-discovery (`recently-sent-forms/`) — more refined than the original 19, but still with overlap/disorganization/misplaced fields. My collaborator personally redrafted the Client Intake Form from this batch and got client sign-off on it already; it still needs my independent review (pending — low priority, do later, not a redesign critique of the whole batch).
6. Current phase: **distillation, not code.** Break down every detail the client provided, remove ambiguity, register open confusions, then produce information architecture + sitemap + UX/UI guides + dev guides (illustrative snippets only, never actual implementation code).

## Critical rule: `next_gen_services`'s schema/code is NOT a requirements source

That sibling repo is the *first pass's interpretation* of the original forms — the very artifact this distillation is auditing. Its Prisma schema baked in the original forms' ambiguity (e.g., the Healing Plan schema only has 3 of the source form's 4 Medicine Wheel goal areas — Emotional Wellbeing was silently dropped). Never cite it as ground truth for what a field means or what a workflow does. Ground truth is: the original form files, the discovery doc, the scope memo, and direct client answers only.

## Directory map

```
nexgen-portal/
├── CLAUDE.md                          this file
├── PROJECT-LOG.md                      process tracking: done/not-started, blockers (now vs. later), deviations from plan
├── NextGen_Portal_Discovery.txt        discovery Q&A (source of truth for workflows/roles/rules)
├── NextGen_Scope_Confirmation_Memo.txt scope change memo (source of truth for what's in/out of scope)
├── original-forms/                     19 form files, round 1 (pre-discovery), .html/.txt
├── recently-sent-forms/                 5 form files, round 2 (post-discovery), .txt
└── distillation/                        client-facing deliverables live directly here; supporting evidence goes in research/ (below)
    ├── glossary.md                      canonical vocabulary — every other artifact uses ONLY these terms
    ├── open-questions.md                client-facing register of unresolved questions, living document
    ├── entity-model.md                  conceptual entity model (item 4)
    ├── forms/                           one factual spec-sheet per source form + 00-index.md
    └── research/                        background research + scratch evidence files feeding a deliverable above — not themselves numbered artifacts, kept for traceability
        ├── legal-context-research.md    Alberta child-welfare/privacy-law research (feeds OQ-03/13/14/15/18–23)
        ├── entity-model-input-documents.md   document inventory used to build entity-model.md
        └── entity-model-input-discovery.md   discovery-doc/memo entity-bearing statements used to build entity-model.md
```

This is now a git repo (initialized 2026-09-21). Check `PROJECT-LOG.md` at the start of every session alongside this file — it tracks what's actually done, what's blocking what, and where real work diverged from this file's plan.

## File-handling convention

Client sends forms as `.docx`. Convert to `.txt` immediately (zipfile + regex on `word/document.xml`, no external deps needed — read `document.xml`, replace `</w:p>` with `\n`, `<w:tab/>` with `\t`, strip remaining XML tags, unescape entities) and **delete the `.docx` once the `.txt` exists** — everything in this repo should stay plain-text/greppable. `.html` source files are read as-is.

## Distillation methodology

**Provenance tagging** — every claim pulled from the discovery doc into any interpretive artifact (open-questions register, entity model, etc.) gets one of four tags:
- **CONFIRMED** — client described their actual current practice.
- **PROPOSED** — written in "the system should..." voice; this is *our own* vendor language that landed in the answer field and was never actually confirmed by the client. Most of the discovery doc's answers are PROPOSED, not CONFIRMED — do not treat them as settled requirements without flagging this.
- **CONTRADICTED** — conflicts with another answer elsewhere in the material.
- **UNANSWERED** — question was asked; no real answer was given (including answers that describe desired system behavior instead of actually answering the question asked).

**Per-form audits are purely factual** — field inventory, structural issues (duplicates, empty presets, incomplete sections, misplaced fields), and claim-verification against anything the discovery doc/memo said about that specific form. No fixes, no resolutions, no design opinions get written into a form's spec sheet — every ambiguity found goes to the open-questions register instead.

**Heavy-reading audit tasks run as background subagents (forks)** that write their findings directly to files in `distillation/`, then report back a short summary — this keeps raw form/document text out of the main conversation while the actual output (the files) persists. Pattern used three times already (original 19 forms, the 5 recently-sent forms, and gathering entity-model evidence into `distillation/research/`) — reuse it for future large-batch reading tasks in this project. When a fork's output is supporting evidence for a later synthesis step rather than a client-facing deliverable itself, write it to `distillation/research/`, not `distillation/` directly.

## Artifact set (dependency order) — status

1. [x] **Original 19 forms audit** → `distillation/forms/01–19.md` + `00-index.md`
2. [x] **Recently-sent 5 forms audit** → `distillation/forms/20–24.md` (appended to `00-index.md`)
3. [x] **Glossary** → `distillation/glossary.md`
4. [x] **Entity model** (conceptual, not a schema) → `distillation/entity-model.md` — Program, Subservice, Site, Client, Parent/Guardian, Case Worker, Placement, Excursion (new), Staff, Staff Assignment, Shift, Document, Version, Lock, Alert, Disclosure
5. [ ] **Permission matrix** — role × document × action × scope, collapsed from the discovery doc's several inconsistent versions of this
6. [ ] **Client lifecycle state machine** — referral → screening → eligibility → accepted/declined → active placement → transition → discharge → archived
7. [ ] **Cross-cutting concerns** — locking/versioning/unlock-with-audit-trail, alert & escalation matrix, retention & legal hold, Indigenous data governance (OCAP, consent, disclosure log), Canadian data residency
8. [~] **Open questions & decisions register** → `distillation/open-questions.md` — living document (OQ-01–OQ-36 issued, 21 open, 13 resolved, as of last update), append as later artifacts surface more; every entry tagged per the provenance system above
9. [ ] **Information architecture + sitemap** — derived last; every node must trace back to something in 4–7, nothing invented
10. [ ] **UX/UI guides**
11. [ ] **Dev guides** — illustrative snippets only, never real implementation code
12. [ ] **Review of the human-redrafted Client Intake Form** (`recently-sent-forms/CLIENT INTAKE FORM.txt`, already client-approved) — independent quality check, deferred/low-priority per collaborator

## Known open tensions

Full list with context and citations lives in `distillation/open-questions.md` (OQ-01–OQ-36 issued, 21 open, 13 resolved, as of last update, living document). Do not duplicate that list here — check that file directly.

## Working preferences

- No code gets written in this repo. If a "dev guide" needs an illustration, use short labeled snippets, clearly marked as illustrative, not a working implementation.
- Confirm before renaming/restructuring directories or making any decision that's genuinely the client's or the human collaborator's to make (e.g., which open tension to resolve which way) — distill and present options, don't silently pick one.
- Big reads (form batches, long discovery docs) go through background subagents that write to files; keep the main session's context for synthesis and decisions, not raw source text.
