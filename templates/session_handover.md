# session_handover.md template

> **What this is:** a 1-page document at your project root that the *next* session reads to pick up where you left off. Think of it as a verbal "where are we" briefing, in writing.
>
> **The discipline:** at the end of a meaningful work session (or before a context-window compression), update this file. Don't write history — write what to do next.
>
> **This is a TEMPLATE.** Delete this header in your copy.

---

# Session Handover — `<short identifier>`

**Last session ended:** `<YYYY-MM-DD HH:MM timezone>`
**Working branch:** `<branch-name>`
**Approximate context spent:** `<low / medium / high>`

---

## What was just accomplished

3-7 bullets. Concrete deliverables — tests passing, files changed, decisions made.

- `<thing accomplished>`
- `<thing accomplished>`
- `<thing accomplished>`

## What's open right now

Things in flight that are NOT in commits yet. The most important section. List by priority.

- **In progress:** `<file or task>` — `<state, e.g. "implementation done, tests still red">`
- **Stuck:** `<file or task>` — `<what we tried, why it didn't work, hypothesis>`
- **Decided to defer:** `<task>` — `<reason and revisit-trigger>`

## What's next session's first task

Be specific. "Continue feature X" is bad. "Open `src/foo.py`, fix the `KeyError` on line 47 by adding null-check; tests are at `tests/test_foo.py::test_null_input`" is good.

1. **Step 1:** `<concrete first action>`
2. **Step 2:** `<concrete second action>`
3. **Step 3 (if blocked):** `<fallback>`

## Open verifications (things to check before continuing)

State that must be true before the next session can safely build on the current work.

- [ ] `<verify X>`
- [ ] `<verify Y>`
- [ ] `<no surprises in git status>`

## Decisions made this session

Things decided that future sessions might re-litigate if not captured.

- **Decided:** `<X>`. **Why:** `<short rationale>`. **ADR (if any):** `<link>`.
- **Decided:** `<X>`. **Why:** `<short rationale>`.

## Don't re-invent (this session's outputs)

Components that were just built and shouldn't be re-derived. Save your future self from "didn't we already do this?"

- `<module/path>` — `<one-line description>`
- `<test/path>` — `<one-line description>`

## Open questions / unknowns

Things we don't know yet that affect the next session's plan.

- `<question>`
- `<question>`

## Anchor docs touched

If any anchor docs need updating in the next session (because changes are coming), list them.

- `docs/anchors/<X>.md` — needs update for `<reason>`
- `docs/anchors/<Y>.md` — needs update for `<reason>`

---

## Recovery instructions

If the next session is starting cold (you're someone else / it's been weeks / you've forgotten everything):

1. Read this file
2. Read the routing table in `CLAUDE.md`
3. For the subsystem in §"What's next session's first task", read its anchor doc
4. Run `git status` and `git log -5` to see where the working tree actually is
5. Run the project's test suite to confirm baseline (don't trust the previous session's "all tests passing" claim — verify)

Then proceed to "What's next session's first task."
