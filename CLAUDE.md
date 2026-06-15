# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Intent Engineering — a static site introducing the "Ship intent, not code." paradigm. Humans define intent via INTENT.md (Why/What/Not/Learnings) and delegate implementation to AI. Intent evolves through a lifecycle: seed → exploring → clarified → dropped.

## Architecture

- **Pure HTML/CSS static site** — no build tools, no JS frameworks (intentional design decision aligned with the paradigm's philosophy)
- **GitHub Pages** — served from `docs/` on main branch
- Deploy URL: `https://intent.roboco.io/`
- **No build step** — edit HTML files directly, `open docs/index.html` to preview

## Key Files

| Path | Role |
|------|------|
| `docs/index.html` | Landing page (English, **source of truth**) |
| `docs/guide/quickstart.html` | 5-minute quickstart guide |
| `docs/guide/concept.html` | Full paradigm concept explanation |
| `docs/ko/`, `docs/zh/`, `docs/ja/` | Translated pages (mirror English structure) |
| `INTENT.template.md` | Distributable INTENT.md template |
| `.claude/commands/translate.md` | `/translate` skill definition |

## i18n Rules

- **English is the source of truth** — author content in English first, then translate
- A PostToolUse hook auto-reminds you to run `/translate` after editing English docs
- `/translate` launches parallel agents (one per language) to regenerate `docs/{ko,zh,ja}/`
- **Untranslatable terms**: seed, exploring, clarified, dropped, INTENT.md, CLAUDE.md, Why, What, Not, Learnings
- **Korean exception**: translate 'Intent' as '의도' (but keep 'Intent Engineering' and 'INTENT.md' as-is)
- Other languages (zh, ja) keep 'Intent' untranslated
- Each page footer has a translate-bar linking to the other language versions
- When adding a new English page, add corresponding pages in all 3 language directories

## Contribution Policy

- **External PRs are not accepted** — `.github/PULL_REQUEST_TEMPLATE.md` redirects contributors to open issues instead
- Solo developer workflow: all work done locally via Claude Code
