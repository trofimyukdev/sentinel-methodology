# CLAUDE.md routing pattern

> **What this is:** `CLAUDE.md` (or `AGENTS.md`, or any tool-specific instruction file) at the project root, used as a *router* — not a config dump. The first thing an AI assistant reads when starting a session.
>
> **The discipline:** keep CLAUDE.md short. It points to the docs that have the actual content. When something doesn't fit, it goes into a doc that CLAUDE.md links to.
>
> **This is a TEMPLATE.** Replace placeholders and tune to your project's shape.

---

# `<Project name>` — routing instructions

## What this project is

`<one-paragraph description — what we're building, who it's for, key constraint>`

## How to work in this codebase

- `<one or two opinionated rules — e.g., "plan first, implement small">`
- `<test discipline — e.g., "run `make test` frequently">`
- `<doc discipline — e.g., "update anchor doc in same commit as code change">`

## Required reading at session start (before non-trivial work)

The 4-6 documents that orient any new session. Keep this list short — every entry is loaded into context.

- [`docs/ROADMAP.md`](docs/ROADMAP.md) — current plan with checkboxes
- [`docs/lessons.md`](docs/lessons.md) — accumulated lessons (active memory)
- [`docs/SESSION_HANDOVER.md`](docs/SESSION_HANDOVER.md) — what to do next
- [`docs/architecture/`](docs/architecture/) — Architecture Decision Records

## Anchor docs — read FIRST when touching the matching subsystem

Per-subsystem ground truth. Update the anchor in the same commit as the code.

| If you're working on … | Read first |
|---|---|
| `<subsystem A>` | `docs/anchors/<A>.md` |
| `<subsystem B>` | `docs/anchors/<B>.md` |
| `<subsystem C>` | `docs/anchors/<C>.md` |

## Standing rules

- When you change a subsystem with an anchor doc, update the anchor in the same commit. If the anchor change feels too large to fit, the code change is too large.
- When the user corrects an approach or a non-obvious decision is validated, write the lesson to `docs/lessons.md`.
- Don't introduce architecture beyond what the task requires. No half-finished implementations.

## Key commands

- `<build>`
- `<test>`
- `<lint>`
- `<run>`
- `<debug>`

## Repo map

Top-level layout in 5-10 lines. Just enough to navigate.

- `<top-folder>/` — `<one-line role>`
- `<top-folder>/` — `<one-line role>`
- `<top-folder>/` — `<one-line role>`

## Safety / domain notes

If your project has critical-safety or regulatory shape, surface it here. One paragraph.

`<safety considerations the assistant must respect>`

---

## What NOT to put in CLAUDE.md

- Long architecture explanations → put in anchor doc, link from here
- Long lists of conventions → put in `docs/conventions.md`, link
- Build / deploy details → put in `Makefile` or `docs/runbook.md`, link
- Anything that changes more than once a month → it'll get stale; link instead

## How to keep this file healthy

- Re-read the whole file every 6-8 weeks. If you wouldn't write something this way today, rewrite it.
- If a section grew past ~10 lines, split it into a separate doc and link.
- If the file approaches 200 lines, split it. CLAUDE.md is a lobby, not a library.
