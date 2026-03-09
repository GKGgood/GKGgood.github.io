# Mint Vocabulary Redesign Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Restyle the vocabulary site so it keeps the existing `words` and `phrases` structure while adopting a mint-accent, minimal editorial look inspired by the reference Jekyll site.

**Architecture:** Keep the current collections and URLs unchanged, then override Minima's default presentation with local layouts, includes, and a custom stylesheet. Build a dedicated landing page, cleaner section index pages, and a more polished entry detail layout that uses English-first UI labels and restrained interactions.

**Tech Stack:** Jekyll 4.4, Liquid templates, Markdown front matter, SCSS/CSS overrides on top of Minima.

### Task 1: Add Local Layout Foundation

**Files:**
- Create: `_layouts/default.html`
- Create: `_layouts/page.html`
- Modify: `_layouts/entry.html`

**Step 1: Create a site-owned default layout**

Add a custom HTML shell with English-first metadata, local navigation, stylesheet link, and a clean centered content wrapper.

**Step 2: Create a local page layout**

Make a reusable page layout for the homepage and section pages so they no longer depend on Minima defaults.

**Step 3: Refactor the entry layout**

Render fields like meaning, phonetic, part of speech, examples, and notes with stronger hierarchy and a quieter dictionary-like reading flow.

### Task 2: Add Shared Theme Styles

**Files:**
- Create: `assets/css/site.css`

**Step 1: Define theme variables**

Add mint accent, soft background, text colors, border colors, and spacing tokens inspired by the reference site.

**Step 2: Style the shell**

Implement typography, width constraints, nav, footer, and subtle link hover states.

**Step 3: Style all content types**

Add dedicated styles for the landing page, section list items, and dictionary entry sections.

### Task 3: Rebuild The Homepage

**Files:**
- Modify: `index.markdown`

**Step 1: Replace plain Markdown-only structure**

Add semantic sections for hero text, quick explanation, and two strong entry links for `Words` and `Phrases`.

**Step 2: Keep copy English-first**

Use concise English UI text that matches the vocabulary-site purpose.

### Task 4: Rebuild The Overview Pages

**Files:**
- Modify: `words.md`
- Modify: `phrases.md`

**Step 1: Upgrade the list markup**

Output each item as a structured block with title, meaning, phonetic, and a details link.

**Step 2: Preserve direct meaning visibility**

Keep the key requirement that users can read all meanings on the overview page without opening detail pages.

### Task 5: Polish Site Content And Config

**Files:**
- Modify: `_config.yml`

**Step 1: Update site metadata**

Replace placeholder site description and social placeholders with vocabulary-site appropriate values.

**Step 2: Keep compatibility**

Do not remove the existing collections setup or detail page defaults.

### Task 6: Verify The Redesign

**Files:**
- Verify: `_layouts/default.html`
- Verify: `_layouts/page.html`
- Verify: `_layouts/entry.html`
- Verify: `assets/css/site.css`
- Verify: `index.markdown`
- Verify: `words.md`
- Verify: `phrases.md`
- Verify: `_config.yml`

**Step 1: Run a full Jekyll build**

Run: `bundle exec jekyll build`

Expected: build succeeds with the local layouts and stylesheet applied.

**Step 2: Verify generated pages exist**

Check that `_site/index.html`, `_site/words/index.html`, `_site/phrases/index.html`, and sample entry pages are generated.

**Step 3: Spot check visual structure in output HTML**

Read generated files to confirm the custom wrapper, navigation, and section markup are present.
