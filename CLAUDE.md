# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Intent Engineering — a static site and documentation project introducing the "Ship intent, not code." paradigm. Proposes a workflow where humans define intent via INTENT.md (Why/What/Not/Learnings) and delegate implementation to AI.

## Team & Tooling

- **Solo developer** — all work is done locally using Claude Code or Claude Code SDK
- Leverage LLM for implementation, translation, and verification; final judgment rests with the developer

## Architecture

- **Pure HTML/CSS static site** — no build tools or JS frameworks (intentional design decision)
- **GitHub Pages deployment** — served from `docs/` folder on the main branch
- Deploy URL: `https://roboco-io.github.io/intent-engineering/`

## File Structure

```
docs/                    # GH Pages serving folder
├── .nojekyll            # Disable Jekyll
├── index.html           # Landing page (Hero, Problem, Framework, Lifecycle, Pipeline, Principles)
├── assets/              # Static assets
└── guide/
    ├── quickstart.html  # 5-minute quickstart guide
    └── concept.html     # Full paradigm concept explanation
INTENT.template.md       # Distributable INTENT.md template
HANDOFF.md               # Project status and next steps
```

## Development

Edit HTML files directly — no build step. Preview locally by opening `docs/index.html` in a browser.

```bash
# Local preview (optional)
open docs/index.html

# Deploy — push to main triggers GH Pages update
git push origin main
```

## Design Decisions

- **Minimal dark theme** — clean, distraction-free design for developer audience
- **English default + multilingual translations** — English is the source, with ko/zh/ja translation pages under `docs/{lang}/`
- **Mobile responsive** — CSS Grid + `clamp()`
- No build tools by design, aligned with Intent Engineering philosophy (minimal, eliminate the unnecessary)

## i18n Rules

- **English is the source of truth** — all content is authored in English first
- Translation pages are placed under `docs/ko/`, `docs/zh/`, `docs/ja/` mirroring the same file structure
- Technical terms (Intent, seed, exploring, clarified, killed, etc.) must remain untranslated
- Changes to English originals must be propagated to all translation pages

## Core Concept

Intent evolves through a lifecycle: seed → exploring → clarified → killed. Humans intervene at exactly two points in the pipeline: writing intent (top) and learning/judging (bottom).
