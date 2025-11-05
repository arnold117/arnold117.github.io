---
layout: default
permalink: /tags/
title: Tags
nav: false
nav_order: 2
---

<div class="tags-page">
  <h1>All Tags</h1>
  <div class="tags-container" style="display: flex; flex-wrap: wrap; gap: 1rem;">
    {% for tag in site.tags %}
      {% assign tag_slug = tag[0] | slugify %}
      <div style="flex: 0 1 calc(25% - 1rem); box-sizing: border-box;">
        <a href="{{ '/blog/tag/' | append: tag_slug | relative_url }}">
          <i class="fa-solid fa-hashtag fa-sm"></i> {{ tag[0] }}
        </a>
        <small class="text-muted">&nbsp;({{ tag[1].size }})</small>
      </div>
    {% endfor %}
  </div>
</div>