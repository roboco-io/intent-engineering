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
├── index.html           # Landing page (English, source of truth)
├── assets/              # Static assets
├── guide/
│   ├── quickstart.html  # 5-minute quickstart guide
│   └── concept.html     # Full paradigm concept explanation
├── ko/                  # Korean translation (mirrors English structure)
├── zh/                  # Chinese (Simplified) translation
└── ja/                  # Japanese translation
INTENT.template.md       # Distributable INTENT.md template
HANDOFF.md               # Project status and next steps
.claude/commands/translate.md  # /translate skill for i18n automation
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
- Static translation pages under `docs/ko/`, `docs/zh/`, `docs/ja/` mirror the English file structure
- Run `/translate` to regenerate translations after editing English sources (hook reminds you automatically)
- Technical terms (seed, exploring, clarified, killed, etc.) must remain untranslated
- Exception: Korean (ko) uses '의도' instead of 'Intent'; other languages keep 'Intent' as-is
- Each page footer has a translate-bar linking to the other language versions
- When adding a new English page, add corresponding pages in all 3 language directories

## Core Concept

Intent evolves through a lifecycle: seed → exploring → clarified → killed. Humans intervene at exactly two points in the pipeline: writing intent (top) and learning/judging (bottom).
