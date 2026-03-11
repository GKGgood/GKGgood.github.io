# AGENTS.md

This file gives agentic coding assistants the working rules for this repository.
It is intentionally specific to this Jekyll vocabulary notebook.

## Repository Summary

- Project type: Jekyll static site
- Runtime: Ruby + Bundler
- Theme base: `minima`, with local layout/style overrides
- Deployment target: GitHub Pages at `https://gkggood.github.io/`
- Main content model:
  - `_words/` for word entries
  - `_phrases/` for phrase entries
  - `words.md` and `phrases.md` for generated list pages

## Rules Files

- No `.cursor/rules/` directory found
- No `.cursorrules` file found
- No `.github/copilot-instructions.md` file found

If any of those files are added later, update this document and follow them.

## Core Commands

Run all commands from the repository root.

### Install dependencies

```bash
bundle install
```

### Start local dev server

```bash
bundle exec jekyll serve
```

Default local URL:

```text
http://127.0.0.1:4000
```

### Full production-style build

```bash
bundle exec jekyll build
```

This is the main verification command for most changes.

## Lint / Test Status

This repository does not currently have a dedicated lint or test suite.

- No ESLint
- No Prettier workflow
- No RuboCop config in repo
- No unit test framework

Use build verification plus targeted HTML inspection instead.

## “Single Test” Equivalent

There is no single-test runner because there are no automated tests.

Use one of these narrower checks depending on the change:

### Verify the whole site still builds

```bash
bundle exec jekyll build
```

### Verify one generated page by inspecting output

After a build, inspect the relevant output file in `_site/`.

Examples:

```text
_site/index.html
_site/words/index.html
_site/phrases/index.html
_site/words/apple/index.html
```

### Verify a specific content entry

1. Edit one entry under `_words/` or `_phrases/`
2. Run `bundle exec jekyll build`
3. Check the matching generated page under `_site/`

This is the closest equivalent to a single test in this codebase.

## Git Workflow

Typical update flow:

```bash
git add .
git commit -m "Describe the content or site change"
git push
```

Do not edit `_site/` directly.
Treat `_site/` as build output only.

## File and Directory Responsibilities

### Content

- `_words/*.md`: individual word entries
- `_phrases/*.md`: individual phrase entries
- Each entry is one file

### Lists

- `words.md`: word index page
- `phrases.md`: phrase index page

### Layouts

- `_layouts/default.html`: site shell, metadata, global scripts
- `_layouts/page.html`: generic page wrapper
- `_layouts/entry.html`: detail page layout for words and phrases

### Styles

- `assets/css/site.css`: primary local stylesheet

### Config

- `_config.yml`: site title, collections, default layouts, Jekyll settings

## Content Entry Schema

### Required front matter

- `title`
- `meaning`
- `definition`

### Common optional fields

- `phonetic`
- `part_of_speech`
- `examples`

### Notes body

Any Markdown content below the front matter becomes the Notes section on the detail page.

## Naming Conventions

### Files

- Use lowercase file names
- Use hyphens instead of spaces
- Keep file names close to the word or phrase

Examples:

- `_words/apple.md`
- `_phrases/in-the-long-run.md`

### Collections and URLs

- Words render to `/words/:name/`
- Phrases render to `/phrases/:name/`

Do not introduce custom per-entry permalinks unless there is a strong reason.

## Formatting Style

### General

- Follow existing formatting in touched files
- Keep edits minimal and local
- Prefer ASCII unless the file already contains non-ASCII content
- Preserve current line endings and indentation style

### Markdown and front matter

- Use YAML front matter at the top of entry files
- Keep keys simple and lowercase with underscores
- Keep examples as YAML lists
- Do not add unused metadata fields

### HTML / Liquid

- Match the existing Liquid style in layouts and pages
- Use `{% if ... %}` guards for optional fields
- Use `relative_url` for internal links and assets
- Avoid introducing complex Liquid logic when simple markup loops are enough

### CSS

- Reuse existing CSS variables from `:root`
- Prefer extending current utility/component classes over adding one-off overrides
- Keep selectors readable and moderately scoped
- Do not add flashy effects; the site style is restrained and editorial

## Typography and Visual Language

This site intentionally uses:

- soft mint accents
- off-white surfaces
- editorial spacing
- restrained hover states
- rounded UI accents in selected controls

When changing UI, preserve that direction.
Do not convert the site into a generic app dashboard.

## JavaScript Guidelines

There is no JS build pipeline.
All JavaScript is inline in `_layouts/default.html`.

When editing JS:

- Keep it dependency-free
- Use small self-contained IIFEs
- Avoid framework-style abstractions
- Gracefully handle missing browser APIs
- Prefer feature detection before using APIs

Current scripts handle:

- last-updated display
- pronunciation playback via `speechSynthesis`

## Error Handling Expectations

- Guard optional data in Liquid before rendering
- Guard browser APIs in JavaScript before calling them
- Fail quietly for non-essential progressive enhancement features
- Do not crash the page because pronunciation or analytics is unavailable

## Change Strategy for Agents

When making changes:

1. Read the relevant layout/content/style files first
2. Change the smallest responsible surface
3. Run `bundle exec jekyll build`
4. Inspect the affected generated file under `_site/`
5. Report exact files changed

## Things To Avoid

- Do not hand-edit `_site/`
- Do not add new frameworks or frontend toolchains
- Do not add test infrastructure unless explicitly requested
- Do not add tags/category systems back in; they were intentionally removed
- Do not add heavy plugins without confirming GitHub Pages compatibility

## Useful Verification Targets

For homepage changes:

- `_site/index.html`

For word list changes:

- `_site/words/index.html`

For phrase list changes:

- `_site/phrases/index.html`

For detail layout changes:

- `_site/words/apple/index.html`
- `_site/phrases/break-the-ice/index.html`

## Final Note

This repository behaves more like a curated notebook than an application backend.
Optimize for clarity, maintainability, and polished reading experience rather than abstraction or over-engineering.
