# NextGen Support Services — Staff Portal Planning Workspace

Welcome. This repository is where we're figuring out, in detail, what the NextGen staff portal actually needs to do — before any of it gets built. If you're new to this repo, this page is your starting point.

## What this repository is (and isn't)

This is a **planning workspace**, not the software itself. There is no working application in here, and there won't be — the actual portal will live in a separate codebase once this planning work is done. Think of this repository as the shared notebook where we work through everything NextGen has sent us (forms, discovery answers, follow-up conversations) and turn it into a clear, agreed-upon plan.

The reason we work this way: digitizing a paper form without first understanding the real process behind it just moves the same confusion into a computer system — it doesn't remove it. So before writing any code, we're reading everything carefully, writing down what's actually clear, and flagging what isn't, so the eventual build reflects how NextGen actually works rather than a guess.

## How we got here

1. The original plan was straightforward: take about 19 existing paper and digital forms (Daily Logs, Case Notes, Incident Reports, the Medication Administration Record, and so on) and turn them into a web application.
2. Early on, it became clear that just digitizing those forms wouldn't be enough — many of them only make sense in the context of a workflow, a decision, or a rule that isn't written down anywhere. So instead of digitizing first, we ran a structured set of discovery questions with NextGen to understand the real people, roles, and processes behind the paperwork.
3. That discovery process revealed the project is bigger than originally scoped: not just a documentation tool, but the foundation for how the organization runs day to day — case management, staff scheduling, time tracking, internal messaging, automatic alerts for time-sensitive situations, and support for funder billing and reporting. NextGen confirmed this larger scope going forward.
4. After that, NextGen sent a second, more refined batch of forms. Some of this second batch has already been worked through directly with NextGen (for example, the Client Intake Form has already been redrafted and approved).
5. We're now in the **distillation phase**: working through all of this material — the original forms, the discovery answers, the second batch of forms — to remove ambiguity and produce a clear specification. Only once that's done does actual software design and development pick back up.

## How to find your way around

- **`NextGen_Portal_Discovery.txt`** and **`NextGen_Scope_Confirmation_Memo.txt`** — these are, in effect, your own words: the discovery questions and answers, and the memo confirming the expanded project scope. They're the primary source of truth for what NextGen has told us so far.
- **`original-forms/`** and **`recently-sent-forms/`** — the two batches of forms as they were sent to us, kept exactly as provided.
- **`distillation/`** — this is where the actual analysis work lives. A few files in here are worth knowing about specifically:
  - **`distillation/open-questions.md`** — **this is the one file worth reading and responding to.** As we work through the material, we run into places where something is unclear, where two documents seem to say different things, or where a question was asked but never really answered. Rather than guessing, we write each of these down as a specific, answerable question. This file is a living list — it grows as we do more work, and questions get marked resolved once we have a clear answer.
  - **`distillation/glossary.md`** — a plain dictionary of terms. Across the forms and discovery answers, the same thing is sometimes called two or three different names (for example, a role, a program, or a document type). This file settles on one name for each thing so everything else in this workspace — and eventually the software itself — uses consistent language.
  - **`distillation/forms/`** — a factual, form-by-form review of everything sent to us: what fields exist, where things don't line up between forms, where something looks incomplete. This is intentionally just observation, not opinion — any judgment calls that come out of it go into the open questions file instead.
  - **`distillation/entity-model.md`** and **`distillation/permission-matrix.md`** — these describe, respectively, the core "things" the system needs to keep track of (clients, staff, programs, documents, and how they relate to each other) and who should be able to see or do what with each type of document. These are more technical planning documents, useful mainly for context — you're not expected to read them in detail.

## A note on how we handle uncertainty

Some of the material we've been given describes what's actually happening today, and some of it describes what NextGen would _like_ the new system to do — those aren't always the same thing, and it isn't always obvious which is which from the wording alone. Some material occasionally states two different things about the same question. Rather than paper over that, we tag each significant claim we work with — roughly, as something confirmed, something proposed but not yet confirmed, or something contradictory — so it's always clear how solid a given piece of information is.

If you see a note flagging an inconsistency in something your own team sent us, that's a completely normal and expected part of this process, not a criticism — forms and answers written by different people at different times almost always end up with small mismatches, and catching them now is much cheaper than catching them after the software is built.

## Where things stand right now

Work completed so far:

- Full factual review of both batches of forms (24 forms in total)
- A shared glossary of terms
- A conceptual model of the system's core information (clients, staff, programs, documents, and so on)
- A first pass at who should have access to what

Still ahead: mapping out the full journey a client takes through NextGen's services (from referral through to discharge), working through some cross-cutting rules (recordkeeping requirements, data privacy, and Indigenous data governance in particular), and then — once all of that is settled — designing the actual screens and structure of the portal, followed by development.

The open-questions file is the best up-to-date source for exactly what's settled and what's still being worked through.

## Questions

If anything here is unclear, or you'd like more context on any of this, please reach out on our side rather than editing files directly in this repository.
