---
layout: page
title: Words
permalink: /words/
intro: Browse every saved word with the meaning visible on this page.
---

{% assign items = site.words | sort: "title" %}
{% for item in items %}
{% assign entry_number = forloop.index %}
<section class="entry-list-item entry-list-item--word">
  <p class="entry-list-item__summary">
    <span class="entry-list-item__number">{{ entry_number }}.</span>
    <a class="entry-list-item__link" href="{{ item.url | relative_url }}">{{ item.title }}</a>
    {% if item.part_of_speech %}<span class="entry-list-item__sep">|</span><span class="entry-list-item__pos">{{ item.part_of_speech }}</span>{% endif %}
    {% if item.meaning %}<span class="entry-list-item__sep">|</span><span class="entry-list-item__meaning-text">{{ item.meaning }}</span>{% endif %}
  </p>
  {% if item.phonetic %}
    <p class="entry-list-item__subline">
      <button class="pronounce-button" type="button" data-pronounce="{{ item.title | escape }}" aria-label="Play pronunciation for {{ item.title }}">🔊</button>
      <span>{{ item.phonetic }}</span>
    </p>
  {% endif %}
</section>

{% endfor %}
