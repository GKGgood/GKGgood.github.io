# Sorting And Footer Update Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add user-selectable sorting for the `Words` and `Phrases` pages, and update the footer copy and links to match the new site ownership wording.

**Architecture:** Keep the existing Jekyll-generated list markup, but add a lightweight client-side sorting control so the page can switch between alphabetical order and a GitHub-backed `Recently updated` order. Use front-end JavaScript in the existing global layout to fetch commit metadata for `_words/*.md` and `_phrases/*.md`, then reorder already-rendered list items without adding a build plugin or second page variant.

**Tech Stack:** Jekyll 4.4, Liquid templates, Markdown front matter, inline vanilla JavaScript in `_layouts/default.html`, CSS in `assets/css/site.css`, GitHub public commits API.

### Task 1: Add Sort Control Markup To List Pages

**Files:**
- Modify: `words.md`
- Modify: `phrases.md`

**Step 1: Add sort controls above each list**

Render two options for each page: `A-Z` and `Recently updated`.

**Step 2: Add stable data attributes**

For each list item, include data needed for client-side sorting, including title, source content path, and original alphabetical order.

**Step 3: Keep no-JS fallback sensible**

The page should still render in alphabetical order if JavaScript does not run.

### Task 2: Implement Client-Side Sorting Logic

**Files:**
- Modify: `_layouts/default.html`

**Step 1: Add a focused sorting script**

Use a small self-contained script alongside the existing inline scripts.

**Step 2: Support alphabetical sorting**

Alphabetical order should use the server-rendered default ordering and restore it quickly.

**Step 3: Support recently updated sorting**

Fetch commit metadata from GitHub for files in `_words/` and `_phrases/`, map commit dates to list items, and sort newest first.

**Step 4: Fail gracefully**

If GitHub commit data cannot be fetched, keep the page usable and leave alphabetical ordering intact.

### Task 3: Style The Sorting Controls

**Files:**
- Modify: `assets/css/site.css`

**Step 1: Add sorting control styles**

Match the site's current mint editorial style, with quiet controls and a clear active state.

**Step 2: Preserve mobile readability**

The sorting UI should wrap cleanly on narrow screens.

### Task 4: Update Footer Copy And Links

**Files:**
- Modify: `_layouts/default.html`

**Step 1: Replace footer wording**

Change `Built by jekyll` to `Built by GKGgood with Jekyll`.

**Step 2: Update links**

Make `GKGgood` link to `https://github.com/GKGgood`.

**Step 3: Keep wording natural**

Use capitalized `Jekyll` because it is a proper product name.

### Task 5: Verify Behavior And Output

**Files:**
- Verify: `words.md`
- Verify: `phrases.md`
- Verify: `_layouts/default.html`
- Verify: `assets/css/site.css`
- Verify: `_site/words/index.html`
- Verify: `_site/phrases/index.html`
- Verify: `_site/index.html`

**Step 1: Run a full build**

Run: `bundle exec jekyll build`

Expected: build succeeds without introducing template errors.

**Step 2: Verify generated markup**

Confirm sort controls and footer copy exist in generated HTML.

**Step 3: Spot check runtime assumptions**

Make sure the GitHub repository path used by the sorting script matches `GKGgood/GKGgood.github.io` and the actual content file paths.
