# sentinel-methodology

> Engineering methodology for solo developers and small teams building with AI coding assistants.

A working set of patterns, templates, and skill bundles I've extracted from running long-lived AI-assisted projects. The patterns survive the failure modes that show up around month 3-6 of any non-trivial codebase: context loss between sessions, "feature shipped but system doesn't work end-to-end", lessons forgotten, anchor knowledge drifting away from code.

This repo is an extraction — the templates and patterns are domain-agnostic. They came from real production engineering, not from theory.

## What's here

```
sentinel-methodology/
├── templates/      # copy-paste starting points
│   ├── anchor_doc.md           # subsystem-anchored docs that travel with the code
│   ├── adr.md                  # Architecture Decision Record (Nygard-adapted)
│   ├── lessons.md              # active-memory format (vs. passive history)
│   ├── session_handover.md     # multi-session continuity for solo+AI work
│   ├── memory_index.md         # auto-memory entry index for assistants
│   └── claude_md_routing.md    # CLAUDE.md as a routing table, not config
├── examples/       # generic, non-domain-specific examples
├── skills/         # multi-agent orchestration patterns
│   └── research-council/       # 5-7 expert critique pattern
└── docs/
    ├── PHILOSOPHY.md           # why these patterns work for solo+AI
    └── HOW_TO_START.md         # 30-min onboarding for a new project
```

## Who this is for

You, if you:
- Run a non-trivial codebase mostly with an AI coding assistant
- Have hit "I forgot why I built this" or "tests pass but the integration broke"
- Are tired of starting every session from scratch
- Want patterns that compose, not a framework that locks you in

You're probably **not** the target reader if:
- You're shipping single-week prototypes — overhead exceeds value
- You're on a 50+ person team with a Tech Writing org — you have other patterns
- You want a polished SaaS — this is just markdown templates

## Quickstart (30 minutes)

1. Copy `templates/anchor_doc.md` into your project's `docs/anchors/` folder for ONE safety-critical subsystem you've been afraid to touch.
2. Fill it in. Just that one.
3. Add a routing line in your `CLAUDE.md` (see `templates/claude_md_routing.md`).
4. Next time you (or your assistant) modify that subsystem, update the anchor in the same commit.

That's the whole loop. The other templates are upgrades you adopt when the underlying pain shows up.

## Status

This is v0 — early extraction. Templates are working but rough. PRs welcome but **understand the philosophy first** (`docs/PHILOSOPHY.md`) — naively-applied templates do more harm than no templates.

## License

MIT. Use it, fork it, adapt it. Attribution appreciated, not required.

## Acknowledgements

The ADR format is from [Michael Nygard's original 2011 post](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions). Anchor docs as a discipline are an evolution of "living documentation" patterns. The active-memory `lessons.md` pattern is original to this repo as far as I know.

---

**Maintainer:** Vladimir Trofimyuk · [GitHub](https://github.com/) · _public profile links to be added when going public_
