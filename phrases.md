---
layout: page
title: Phrases
permalink: /phrases/
intro: Browse every saved phrase with the meaning visible on this page.
---

{% assign items = site.phrases | sort: "title" %}
{% for item in items %}
{% assign entry_number = forloop.index %}
<section class="entry-list-item entry-list-item--phrase">
  <p class="entry-list-item__summary">
    <span class="entry-list-item__number">{{ entry_number }}.</span>
    <a class="entry-list-item__link" href="{{ item.url | relative_url }}">{{ item.title }}</a>
    {% if item.meaning %}<span class="entry-list-item__sep">|</span><span class="entry-list-item__meaning-text">{{ item.meaning }}</span>{% endif %}
  </p>
</section>

{% endfor %}
