# Translate English docs to ko/zh/ja

Translate all English HTML pages in `docs/` to Korean, Chinese (Simplified), and Japanese.

## Input

`$ARGUMENTS` — Optional: specific language code(s) to translate (e.g., "ko", "zh ja"). If omitted, translates all 3 languages.

## Workflow

### Step 1: Detect changed English pages

Compare English source files against their translated versions:

```
docs/index.html           → docs/{ko,zh,ja}/index.html
docs/guide/quickstart.html → docs/{ko,zh,ja}/guide/quickstart.html
docs/guide/concept.html    → docs/{ko,zh,ja}/guide/concept.html
```

If `$ARGUMENTS` is empty, translate all 3 languages. Otherwise, only the specified language(s).

### Step 2: Translate in parallel

Launch one agent per language using the Agent tool with `run_in_background: true`. Each agent must:

1. Read the English source file fully
2. Translate ALL visible text content to the target language
3. Preserve ALL HTML structure, CSS, and code examples exactly as-is
4. Keep technical terms untranslated: seed, exploring, clarified, killed, INTENT.md, CLAUDE.md, Why, What, Not, Learnings
   - Exception for Korean (ko): translate 'Intent' as '의도' (but keep 'Intent Engineering' and 'INTENT.md' as-is)
5. Set `<html lang="{lang}">` appropriately (`ko`, `zh-CN`, `ja`)
6. Fix relative paths:
   - `{lang}/index.html`: `guide/` links stay, translate-bar links to `../` (English) and sibling `../{other-lang}/`
   - `{lang}/guide/*.html`: nav links to `../index.html` ({lang} root), translate-bar to `../../guide/*.html` (English) and `../../{other-lang}/guide/*.html`
7. Translate-bar shows English + 2 other languages (exclude current language)
8. Write the translated file to `docs/{lang}/`

### Step 3: Verify

After all agents complete, verify:
- All expected files exist
- Each file has correct `lang` attribute
- Translate-bar links are correct (no self-link)

Report which files were created/updated.

## Rules

- Never modify English source files
- Code examples inside `<pre>` or `<code>` blocks must stay in English
- If a new English page is added to `docs/`, create corresponding translated pages in all 3 language directories
