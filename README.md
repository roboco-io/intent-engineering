# Intent Engineering

**Ship intent, not code.**

A practical paradigm for the age of vibe coding. Document your intent precisely — Why, What, Not — and delegate everything else to AI.

## What is this?

Intent Engineering is the discipline of capturing **what to build** and **what not to build** in a single markdown file (`INTENT.md`), then letting AI handle implementation, verification, and deployment.

It's not a framework. It's not a tool. It's a file and a discipline.

## The Intent Document

```markdown
# INTENT — [Project Name]

> status: seed | exploring | clarified | killed

## Why       ← Why does this exist?
## What      ← What are we building?
## Not       ← What will we never do?
## Learnings ← What did we discover along the way?
```

**Why** defines the reason this project exists. In early stages it's a hypothesis; once validated, it's conviction.

**What** describes features and user flows concretely, without prescribing implementation.

**Not** sets hard boundaries AI must not cross — security, scope, quality bars.

**Learnings** is a living log of experiments and their outcomes, tracking how intent evolves through exploration.

## The Lifecycle

Intent evolves through four states:

```
seed → exploring → clarified → build
  │        │            │
  └────────┴────────────┴──→ killed
```

- **seed**: Just an idea. Write a hypothesis, start experimenting.
- **exploring**: Actively validating through prototypes, interviews, research.
- **clarified**: All sections filled with conviction. Ready to build.
- **killed**: Evidence says stop. Record why — that knowledge is valuable.

## Quick Start

1. Create `INTENT.md` at your project root
2. Pick your starting state (seed / exploring / clarified)
3. Fill in Why. Be honest about What and Not — mark unknowns with `(?)`
4. Explore, learn, update. Or kill when evidence says so.
5. Once clarified, hand off to AI.

Full guide: [intentengineering.dev](https://roboco-io.github.io/intent-engineering/) (or see `docs/`)

## Links

- [Landing Page](https://roboco-io.github.io/intent-engineering/)
- [Quick Start Guide](https://roboco-io.github.io/intent-engineering/guide/quickstart.html)
- [Full Concept](https://roboco-io.github.io/intent-engineering/guide/concept.html)

## License

MIT
