# Claude Code instructions — sentinel-methodology

> Engineering methodology toolkit for solo developers + AI assistants. Public, MIT, domain-agnostic.

## What this repo is

A pattern library for keeping AI-assisted projects honest across long-running sessions: templates +
philosophy + skills. The patterns survive the failure modes that show up around month 3–6 of any
non-trivial codebase — context loss between sessions, "feature shipped but the system doesn't work
end-to-end", lessons forgotten, anchor knowledge drifting away from code.

**Audience:** senior ICs building solo or in small teams with Claude Code, Cursor, Aider, or similar AI
coding assistants. Engineering-focused, not domain-specific.

## Public-facing discipline (strict)

This repo is public. Keep it strictly **domain-agnostic**. Hard rules:

- ❌ Do NOT reference any specific business domain, product, employer, customer, or any other project.
- ❌ Do NOT copy code verbatim from any other repo — only patterns/templates.
- ❌ Do NOT use examples that reveal any specific system. Use generic examples: caching layer, auth flow,
  data pipeline, web app, e-commerce.
- ✅ DO talk about: AI-assisted engineering, prompt patterns, session-handover discipline, ADRs, anchor
  docs, `lessons.md` as active memory, multi-agent research patterns.

## Identity

- Maintainer: Vladimir Trofimyuk
- License: MIT

## Files at a glance

- `README.md` — pitch + table of contents
- `docs/PHILOSOPHY.md` — why these patterns work for solo + AI
- `docs/HOW_TO_START.md` — 30-min onboarding for a new project
- `templates/` — 6 patterns (anchor_doc, ADR, lessons, session_handover, memory_index, claude_md_routing)

## How to work in this repo

1. **Read `README.md` first** to understand what's published vs draft.
2. **Every commit message here is publicly visible** — keep them generic, no internal references.
3. **Examples must be domain-agnostic** — if you can't make an example without referencing specific work,
   leave a `TODO: needs generic example` marker instead of a half-disguised hybrid.
4. **Templates are public API** — breaking changes need a `MIGRATION.md` note.

## Standing rule — public-facing discipline

When tempted to add an example that references a real specific system: STOP. Either invent a clean generic
example (caching layer, auth, e-commerce, etc.) or leave the slot empty with a `TODO:` marker. Do NOT
compromise — a half-disguised reference is worse than no example.
