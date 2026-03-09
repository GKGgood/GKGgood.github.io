# Words And Phrases Site Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Turn the default Jekyll blog into a vocabulary site with dedicated `words` and `phrases` sections, overview pages, and per-entry detail pages.

**Architecture:** Use Jekyll collections for `_words/` and `_phrases/` so each entry is its own Markdown file with a stable URL like `/words/apple/`. Render overview pages from collection data so users can see all meanings at once, then click through to dedicated detail pages with pronunciation, part of speech, examples, and notes.

**Tech Stack:** Jekyll 4.4, Minima theme, Liquid templates, Markdown front matter.

### Task 1: Configure Collections

**Files:**
- Modify: `_config.yml`

**Step 1: Add collection definitions**

Add `words` and `phrases` collections with `output: true` and permalinks `/words/:name/` and `/phrases/:name/`.

**Step 2: Add defaults for detail layout**

Set a default layout for collection documents so each entry uses the same detail page template.

**Step 3: Verify config shape**

Check that the YAML structure is valid and indentation is consistent.

### Task 2: Build Shared Entry Layout

**Files:**
- Create: `_layouts/entry.html`

**Step 1: Create a reusable detail layout**

Render title, meaning, pronunciation, part of speech, examples, notes, and a backlink to the parent collection page.

**Step 2: Keep fallback handling simple**

Only show sections when data exists so words and phrases can share the same template.

### Task 3: Replace Homepage With Section Navigation

**Files:**
- Modify: `index.markdown`

**Step 1: Replace default blog home layout**

Use a simple landing page that introduces the site and links clearly to `/words/` and `/phrases/`.

**Step 2: Avoid blog-style post listing**

Make the homepage a content gateway rather than a chronological article feed.

### Task 4: Add Overview Pages

**Files:**
- Create: `words.md`
- Create: `phrases.md`

**Step 1: Build the words overview page**

Loop through `site.words` and show each word, meaning, pronunciation, and a link to its detail page.

**Step 2: Build the phrases overview page**

Loop through `site.phrases` and show each phrase, meaning, pronunciation if present, and a link to its detail page.

**Step 3: Show meanings directly on the page**

Make sure users can read all recorded meanings without opening each detail page.

### Task 5: Add Starter Content

**Files:**
- Create: `_words/apple.md`
- Create: `_words/brave.md`
- Create: `_phrases/break-the-ice.md`
- Create: `_phrases/in-the-long-run.md`

**Step 1: Add two sample words**

Include front matter fields for meaning, phonetic, part of speech, examples, and notes.

**Step 2: Add two sample phrases**

Use the same general structure so the shared layout works for both collections.

### Task 6: Verify The Site

**Files:**
- Verify: `_config.yml`
- Verify: `index.markdown`
- Verify: `words.md`
- Verify: `phrases.md`
- Verify: `_layouts/entry.html`
- Verify: `_words/*.md`
- Verify: `_phrases/*.md`

**Step 1: Run a Jekyll build**

Run: `bundle exec jekyll build`

Expected: build succeeds and generates pages for the homepage, both overview pages, and all sample entries.

**Step 2: Spot check generated URLs**

Confirm expected output paths exist under `_site/words/` and `_site/phrases/`.

**Step 3: Document future content workflow**

Explain that new entries are added by creating Markdown files in `_words/` or `_phrases/` using lowercase names and hyphens.
