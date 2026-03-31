---
layout: page
title: Words
permalink: /words/
intro: Browse every saved word with the meaning visible on this page.
sort_controls: true
sort_label: Sort words list
---

{% assign ordered_items = site.words | where_exp: "item", "item.order != nil" | sort: "order" %}
{% assign unordered_items = site.words | where_exp: "item", "item.order == nil" | sort: "title" %}
{% assign items = ordered_items | concat: unordered_items %}
{% for item in items %}
{% assign entry_number = forloop.index %}
<section class="entry-list-item entry-list-item--word" data-sort-title="{{ item.title | downcase | escape }}" data-source-path="{{ item.path | escape }}" data-alpha-index="{{ forloop.index0 }}">
  <p class="entry-list-item__summary">
    <span class="entry-list-item__number">{{ entry_number }}.</span>
    <a class="entry-list-item__link" href="{{ item.url | relative_url }}">{{ item.title | escape }}</a>
    {% if item.part_of_speech %}<span class="entry-list-item__sep">|</span><span class="entry-list-item__pos">{{ item.part_of_speech | escape }}</span>{% endif %}
    {% if item.meaning %}<span class="entry-list-item__sep">|</span><span class="entry-list-item__meaning-text">{{ item.meaning | escape }}</span>{% endif %}
  </p>
  {% if item.phonetic %}
    <p class="entry-list-item__subline">
      <button class="pronounce-button" type="button" data-pronounce="{{ item.title | escape }}" aria-label="Play pronunciation for {{ item.title }}">🔊</button>
      <span>{{ item.phonetic | escape }}</span>
    </p>
  {% endif %}
</section>

{% endfor %}
