---
layout: page
title: Vocabulary Notebook
intro: Scan saved words and phrases fast, then open any entry for pronunciation, usage, and notes.
permalink: /
body_class: home-page
---

<div class="home-actions" role="navigation" aria-label="Homepage sections">
  <a class="home-actions__link" href="{{ "/words/" | relative_url }}">
    <span class="home-actions__label">Words</span>
    <span class="home-actions__meta">
      <span>{{ site.words | size }} entries</span>
      <span aria-hidden="true">|</span>
      <span>Last updated <time data-last-updated></time></span>
    </span>
  </a>
  <a class="home-actions__link" href="{{ "/phrases/" | relative_url }}">
    <span class="home-actions__label">Phrases</span>
    <span class="home-actions__meta">
      <span>{{ site.phrases | size }} entries</span>
      <span aria-hidden="true">|</span>
      <span>Last updated <time data-last-updated></time></span>
    </span>
  </a>
</div>
