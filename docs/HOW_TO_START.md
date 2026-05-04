# How to start (30 minutes to first value)

You don't adopt the whole methodology at once. You adopt **one pattern** for **one subsystem** and let it earn the next adoption.

## The 30-minute path

### Step 1 (5 min) — Pick your most-feared subsystem

Look at your codebase. Find the one piece you're afraid to touch. The one where:
- You hesitate before opening the file
- Bugs there always take 2-3× longer than expected
- Your AI assistant repeatedly suggests changes that break invariants

That's where anchor docs pay off first.

### Step 2 (15 min) — Write the anchor

Copy `templates/anchor_doc.md` into `<your-repo>/docs/anchors/<subsystem>.md`. Fill in:

- **What this subsystem does** (one paragraph)
- **What it MUST not do** (the invariants you've burned yourself on)
- **Where the code lives** (file paths)
- **Recent decisions** (the last 3-5 ADRs or commits that changed how this works)
- **Open known issues** (things half-fixed)

Don't write history. Don't write architecture astronaut prose. Write what the next person needs to not break it.

### Step 3 (5 min) — Wire the routing

Edit your `CLAUDE.md` (create one if you don't have it). Add a routing table:

```markdown
## Read FIRST when working on...

| Subsystem | Anchor doc |
|---|---|
| <your subsystem> | docs/anchors/<subsystem>.md |
```

That's it. From now on, when you (or your assistant) work on this subsystem, you read the anchor first. When you change the subsystem, you update the anchor in the same commit.

### Step 4 (5 min) — Set the discipline

Add this to your `CLAUDE.md` near the top:

```markdown
## Standing rule
When you change a subsystem with an anchor doc, **update the anchor in the same commit**. If the anchor change feels too large to fit, the subsystem change is too large.
```

That's the whole 30-minute loop.

## The next 90 days

After 2-3 weeks of using just one anchor doc, you'll naturally feel where the next pattern fits. Most likely:

- **lessons.md** — when you catch yourself making the same mistake twice
- **ADRs** — when you make a decision you don't want to rehash
- **session handover** — when sessions are getting long and context-loss starts to hurt
- **research-council skill** — when an architecture decision feels too big for a single conversation

Don't adopt them on a schedule. Adopt them when the pain is acute. The patterns are sized for solo+AI projects, but they're not free — each adds friction. The friction must pay for itself in caught-bugs / preserved-context / faster-cold-starts.

## What to NOT do at first

- Don't write anchor docs for *every* subsystem. The discipline collapses if you have 30 anchors and most are stale.
- Don't write a 50-page lessons.md on day 1. It grows organically — that's the point.
- Don't migrate your existing wiki/Notion/Confluence to anchor docs. These templates work because they live next to code; they don't work in a separate tool.
- Don't enforce the patterns on collaborators who aren't sold. The patterns reward voluntary discipline.

## When to read the philosophy doc

If after 3 weeks of anchor docs you're not seeing benefit — *before* dropping the pattern, read [PHILOSOPHY.md](./PHILOSOPHY.md). The patterns make assumptions about your project shape (solo+AI, long-lived, integration-heavy). If your project doesn't fit those assumptions, the patterns won't fit either, and that's fine.
