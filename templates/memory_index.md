# MEMORY.md — auto-memory index template

> **What this is:** a top-level index of memory entries that an AI assistant maintains across sessions. Each entry is a separate file; this file is just the index, kept short enough to load into every conversation.
>
> **The discipline:** keep this file under 200 lines. Each entry is one line, under ~150 characters. Memory content lives in the linked files, not here.
>
> **Why this exists:** AI assistants don't have memory across conversations by default. Some tools provide auto-memory — when they do, the index file is what gets loaded into every conversation, while detailed memories are loaded on demand. This template gives that auto-memory system a structure.
>
> **This is a TEMPLATE.** Delete this header in your project's copy.

---

# Project Memory Index

## ⚡ Read first (current state)

The most recent state-of-the-project pointer. Replace as work progresses.

- **`<YYYY-MM-DD>`:** [`<latest-handover-file.md>`](./latest-handover-file.md) — `<one-line state summary>`

## Project basics

Stable facts that change rarely.

- **What this is:** `<one-line project description>`
- **Tech stack:** `<top 3-5 technologies>`
- **Key constraints:** `<deployment / regulatory / domain constraints that shape decisions>`

## Conventions

Things the project does that aren't standard practice or where the project picks one option from many.

- [`<convention-name>`](./convention-file.md) — `<one-line summary>`
- [`<convention-name>`](./convention-file.md) — `<one-line summary>`

## Active work

Time-sensitive memory entries about ongoing initiatives.

- [`<initiative>`](./initiative-file.md) — `<status + next milestone>`
- [`<initiative>`](./initiative-file.md) — `<status + next milestone>`

## Feedback rules

Lessons / preferences / corrections from the human operator that should shape future sessions.

- [`<rule-name>`](./rule-file.md) — `<one-line summary>`
- [`<rule-name>`](./rule-file.md) — `<one-line summary>`

## External references

Where information lives outside this repo.

- [`<system>`](./reference-file.md) — `<what's there + why it matters>`
- [`<system>`](./reference-file.md) — `<what's there + why it matters>`

## Session history

Reverse-chronological. Most recent at top. Older entries pruned out periodically.

- **`<YYYY-MM-DD>`:** [`<session-file>`](./session-file.md) — `<one-line summary>`
- **`<YYYY-MM-DD>`:** [`<session-file>`](./session-file.md) — `<one-line summary>`
- **`<YYYY-MM-DD>`:** [`<session-file>`](./session-file.md) — `<one-line summary>`

---

## How memory entries are structured

Each linked file uses the format:

```markdown
---
name: <memory name>
description: <one-line description for relevance matching>
type: <project | feedback | reference | convention>
---

<memory content — usually 50-300 words>

For "feedback" or "convention" types:
**Why:** <reason — past incident, strong preference, etc.>
**How to apply:** <when this kicks in, edge cases>
```

## Curation rules

- Keep this index file < 200 lines (loaded every session — long index burns context)
- Each individual memory file: 50-500 words ideal, 1500 max
- Update or remove memory entries that become stale; don't just append
- Avoid duplicate memories — first check for an existing entry to update
- Memory entries are point-in-time; verify against current code before acting on them

## What NOT to put in memory

- Code patterns, conventions, file paths, or project structure that can be derived by reading the project itself
- Git history — `git log` / `git blame` are authoritative
- Debugging recipes — the fix is in the code; the commit message has the context
- Anything already documented in your CLAUDE.md or anchor docs
- Ephemeral conversation context that won't matter next session
