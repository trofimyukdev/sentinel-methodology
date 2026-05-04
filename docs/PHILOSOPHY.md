# Philosophy

Why these patterns exist and when to use them.

## The four problems they solve

These templates exist because four specific failure modes show up reliably in solo-developer + AI-assistant projects past month 3:

### 1. The drift problem
Documentation, code, and the developer's mental model drift apart. A doc says "module X handles Y", but X was refactored two months ago and no longer does Y. Future sessions trust the doc and produce wrong work.

**Anchor docs** solve this by attaching a doc to a *subsystem* (not to the system as a whole) and requiring the doc be updated in the same commit as the code. The blast radius is small enough that the discipline holds.

### 2. The repeated-mistake problem
You hit a tricky bug, debug it for an hour, fix it. Three weeks later, you (or your assistant) commits the same bug again. The lesson was never captured.

**Active lessons.md** solves this by recording lessons as *current rules* ("we always do X because of incident Y"), not as historical narratives. Future sessions consult lessons.md as if it were a constraint, not a memoir.

### 3. The session-loss problem
Every conversation with an AI assistant starts cold. Without a transfer mechanism, you re-explain the architecture, the stuck issue, the rationale, every single time.

**Session handover** + **MEMORY index** + **CLAUDE.md routing** together create a 30-second cold-start: the assistant reads the routing table, finds the relevant anchor, picks up where the last session ended.

### 4. The "feature shipped, system broke" problem
Tests pass. The new feature works in isolation. The integration broke silently because no one held the whole picture in their head.

**Multi-agent research-council** addresses this — when the whole picture matters (architecture decisions, post-incident reviews, big refactors), one assistant isn't enough. Split the question across 5-7 angle-specific reviewers, then synthesize. The pattern is heavyweight; reserve it for decisions you'd otherwise convene a meeting about.

## Why solo + AI specifically?

These patterns are sized for projects where:
- One human is the primary keeper of intent
- An AI assistant does most of the typing
- There is no Tech Writing team, no QA org, no PM checking integration

In that environment, the cost of drift compounds quickly. A 5-person team has 5 chances to catch a drifting doc; a solo dev + assistant has zero, because the assistant trusts the doc.

## When NOT to use these patterns

- **Throwaway prototypes.** Don't write an ADR for a 100-line Hacker News submission.
- **Strict single-session work.** If you're not coming back tomorrow, skip the handover.
- **Large teams with formal processes.** You probably have your own anchor-doc equivalent — don't add a second discipline.
- **As a checklist for credentialism.** "We have ADRs!" without commit-time updates is theater.

## Composition rules

The patterns compose, but in this order:

1. **CLAUDE.md routing** is the entry point. It's a router from "I'm working on X" to "read Y first."
2. **Anchor docs** are the leaves of that router — the ground-truth subsystem docs.
3. **ADRs** capture *decisions* (one-time, time-stamped). Anchors capture *current state* (lossy summary, evergreen).
4. **lessons.md** is orthogonal — it's rules learned from failures, applicable across subsystems.
5. **Session handover** + **memory index** are the across-session glue.
6. **Research-council** is the heavy lifting tool — only when needed.

You can adopt 1-2 patterns and benefit. You don't need all six on day one.

## What success looks like

Three months in, with these patterns properly applied:
- A new session can pick up complex work with <15 minutes of cold-start
- "Why did we choose X?" has a one-paragraph answer in an ADR
- "What's the current state of subsystem Y?" has a one-page answer in an anchor
- Recurring mistakes don't recur — they hit a lesson rule

If you're not seeing these effects after 3 months of disciplined use, the patterns aren't fitting your project. Drop them or adapt — don't perform compliance.
