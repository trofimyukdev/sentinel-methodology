# ADR-`NNN` — `<short decision title>`

> **What an ADR is:** a record of a *decision* made at a moment in time. Captures context, the choice, the alternatives, and the consequences. Adapted from [Michael Nygard's 2011 format](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions).
>
> **When to write one:** for any decision you'd otherwise re-discuss in 6 months. Architecture changes, technology adoption, deprecations, opinionated trade-offs.
>
> **Delete this header before publishing.**

---

**Status:** Proposed | Accepted | Deprecated | Superseded by ADR-`NNN`
**Date:** `<YYYY-MM-DD>`
**Deciders:** `<names>`
**Related:** `<previous ADRs, anchor docs, issues>`

---

## Context

What is the problem we're solving? What forces are at play? Be concrete — link to a specific incident, a specific user request, a specific scaling pressure. "We need a faster system" is not context; "Request P95 hit 800ms last Friday during the Y campaign" is.

State the **constraints** that any solution must respect:

- Constraint 1
- Constraint 2

State the **non-negotiables** — properties no solution may give up:

- Non-negotiable 1
- Non-negotiable 2

## Decision

What did we decide? **State it as a present-tense fact.** "We will use X" — not "We propose to consider possibly using X."

The decision should fit in 1-3 paragraphs. If it requires a 10-paragraph explanation, the ADR is doing too much — split it.

## Alternatives considered

For each, one paragraph: what it was, why it was tempting, why we rejected it.

### Alternative 1 — `<name>`
What it was. Why it was tempting. Why we rejected it.

### Alternative 2 — `<name>`
Same structure.

### Alternative 3 — `<name>`
Same structure.

If you considered fewer than 2 alternatives, you probably didn't try hard enough — go think for another 30 minutes before committing.

## Consequences

### Positive

- What gets better. Be specific.
- What new capabilities are unlocked.
- What tech debt this pays down.

### Negative

- What gets worse. Be honest — every decision has costs.
- What new tech debt this incurs.
- What we'll regret in 18 months if X happens.

### Neutral / changes-in-shape

- Things that aren't strictly better or worse, but different.
- New skills required.
- New surfaces to monitor.

## Implementation notes

Pointers to where the work lives — not the work itself. The work goes in code + anchor doc; the ADR captures *why* it was done that way.

- Migration plan / rollout sequence
- Code touchpoints (file paths, modules)
- Anchor docs that need updating

## How we'll know this was right

What's the signal — 3, 6, 12 months out — that says "this decision worked"? What signal would say "we should have picked Alternative N"?

If you can't articulate this, the decision isn't testable, and you may be making it on vibes.

## Supersession

This ADR is superseded by `<ADR-NNN>` on `<date>` because `<reason>`. (Add this section only when superseded; otherwise delete.)
