# lessons.md — active memory format

> **What this is:** rules learned from failures, written as *current constraints* — not historical narratives. Future sessions consult this file as if it were a list of things they must respect.
>
> **The discipline:** when a mistake recurs (you, your assistant, a teammate hits a bug that's been hit before), promote the fix into a lesson here. When a new lesson contradicts an old one, supersede the old entry — don't just append.
>
> **This is a TEMPLATE.** The actual `lessons.md` lives in your project root. Delete this header in your project's copy.

---

## How to read this file

- Each entry is a **rule that applies now**, not a story.
- Entries are dated for traceability.
- A newer entry can supersede an older one — when in doubt, follow the newest applicable rule.
- If you (or your assistant) are about to violate a lesson without strong new evidence, **stop and discuss**, don't just push through.

## How to write a new entry

Format:

```markdown
## YYYY-MM-DD — <short rule name>

**Rule:** <what to do or not do, in present tense>

**Why:** <the past incident / cost / failure that this prevents — be specific, the why is what survives>

**How to apply:** <when this rule kicks in, edge cases, exceptions if any>
```

Three things matter:
1. **Rule first.** Future readers should know the constraint in the first line.
2. **Why with specifics.** "We had an outage" doesn't help. "Request X took 30s because of N+1 query in module Y" helps.
3. **Application scope.** A rule with no edge-case discussion will be misapplied.

## Anti-patterns to avoid

- ❌ "We made a mistake when..." (history, not rule)
- ❌ "Try to remember to..." (vague, not enforceable)
- ❌ "Use best practices when..." (means nothing)
- ❌ Long entries. If the rule needs 3 paragraphs to state, it's two rules.
- ❌ Tactical "always run `make test`" entries that belong in CI, not lessons.

## When to supersede vs append

- **Append** when: new domain, new subsystem, new failure class. Different rule.
- **Supersede** when: same situation, different conclusion. Mark the old entry `~~strikethrough~~ — superseded by <date>` and write the new one with a `**Supersedes:** <date> entry "<name>"` line.
- **Delete** when: the rule is now wrong (rare) or the underlying system was removed (cleanup).

## Curation cadence

- Once a quarter: skim the file. Are there 5+ entries that haven't been referenced in actual work? Either they're load-bearing (keep), or they're noise (delete or archive into `lessons-archive.md`).
- Don't let `lessons.md` grow past ~150 entries — at that size it stops being read.

---

## Example entries (delete in your project's copy)

## 2026-04-15 — Don't trust anchor doc claims without verification

**Rule:** When working in a subsystem, verify the anchor doc's "code lives at" line by actually opening those files. Don't take the doc's word for it.

**Why:** On 2026-04-15 a refactor 3 weeks earlier had moved a key module; the anchor still pointed to the old path. An assistant trusted the anchor, generated code referencing the wrong import, and tests failed in a confusing way (the module name still resolved via a re-export, so the failure mode was nonobvious).

**How to apply:** Anchor docs are a *summary*, not a *source of truth*. If you're about to make a structural change based on what an anchor says, verify against `git ls-files | grep <module>` first.

## 2026-03-22 — Tests must hit a real database for migration code paths

**Rule:** Don't mock the DB in tests that exercise migration logic. Use the real database (sqlite-in-memory for unit; real Postgres for integration).

**Why:** On 2026-03-22 a migration that passed all mocked tests failed in production because the mock returned `None` where the real driver returned `0` for an empty `count(*)`. The semantic difference was load-bearing for the migration's "is the column already populated?" check.

**How to apply:** Any test that calls into migration / schema-aware code uses a real DB. Mocks are fine for service-layer logic that doesn't care about driver semantics.
