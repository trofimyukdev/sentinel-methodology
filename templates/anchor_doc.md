# Anchor doc — `<subsystem-name>`

> **What an anchor doc is:** a single page that holds the *current state* of one subsystem. Not history. Not architecture. The thing the next reader (you, your assistant, a teammate) needs to not break it.
>
> **The discipline:** when you change the subsystem, you update the anchor in the same commit.
>
> **Delete this header before publishing.** Replace `<subsystem-name>` with the actual subsystem.

---

**Subsystem:** `<subsystem-name>`
**Last updated:** `<YYYY-MM-DD>`
**Owner / primary editor:** `<name>`
**Code lives at:** `<path/to/main/files>`

---

## What this subsystem does

One short paragraph. State the *purpose* in plain language. If you can't explain the purpose in 4 sentences, the subsystem is probably too big for one anchor — split it.

## What it MUST NOT do (invariants)

The two-to-five things that, if violated, are bugs (often subtle, often costly). These are the rules the subsystem is meant to enforce.

- Invariant 1 — `<short statement>`. Why: `<reason / past incident / safety property>`.
- Invariant 2 — `<short statement>`. Why: `<reason>`.
- Invariant 3 — `<short statement>`. Why: `<reason>`.

If a future change weakens any invariant, that's a load-bearing decision — write an ADR.

## Public contract

What other subsystems can rely on this one to do.

- **Inputs:** `<types, sources, preconditions>`
- **Outputs / side effects:** `<types, destinations, postconditions>`
- **Failure modes exposed:** `<exceptions, error states, recovery hints>`
- **Performance / correctness guarantees:** `<latency budget, ordering, idempotency>`

Don't list every function — list the *contract*. If the contract changes, downstream callers change.

## Internal structure (briefly)

3-7 bullets. Just enough to navigate the code without re-discovering the layout.

- `<file_or_module>` — `<one-line role>`
- `<file_or_module>` — `<one-line role>`
- `<file_or_module>` — `<one-line role>`

Don't paste class diagrams. The code IS the diagram.

## Recent decisions

Last 3-5 changes that affected how this subsystem works. Each: date, one-line summary, link to ADR or commit.

- `<YYYY-MM-DD>` — `<change>` — see `<ADR-XXX>` / `<commit-hash>`
- `<YYYY-MM-DD>` — `<change>` — see `<ADR-XXX>` / `<commit-hash>`

When this list grows past 5, prune the oldest into a `## Decision history` section at the bottom.

## Open known issues

Things that are partially fixed, or known-broken-but-bounded, or planned. These are the landmines.

- `<issue>` — current workaround / blast radius / planned resolution
- `<issue>` — current workaround / blast radius / planned resolution

If the list grows long, that's a signal — schedule a session to close issues, not to add features.

## How to test changes

Tests that pin the invariants. Not "all tests" — the specific tests that will catch a regression *of this subsystem's contract*.

- `<test_path>` — covers invariant 1
- `<test_path>` — covers invariant 2
- Manual smoke step: `<command or check>` — when automated coverage is incomplete

## Operator runbook (if applicable)

For subsystems that show up in production: what to do when alerts fire.

- Alert / symptom 1 → likely cause → first action → escalation path
- Alert / symptom 2 → likely cause → first action → escalation path

If this subsystem doesn't run in production, delete this section.

## Deliberate non-goals

What this subsystem **doesn't** try to do (and why), to forestall well-meaning future contributions that scope-creep it.

- We don't `<X>` because `<Y>`.
- We don't `<X>` because `<Y>`.

---

## Decision history (older)

Pruned from "Recent decisions" once it grows past 5. Append-only. Date-ordered, oldest first. One-line summaries with ADR/commit links.

`<YYYY-MM-DD>` — `<change>` — `<ADR-XXX / commit>`
