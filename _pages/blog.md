---
layout: page
permalink: /blog/
title: Blog
description: Thoughts, ideas, and explorations.
nav: true
nav_order: 3
---

<div class="publications">
  {% for post in site.posts %}
    <div class="publication">
      <div class="publication-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </div>
      <div class="publication-authors">
        {{ post.date | date: "%B %-d, %Y" }}
      </div>
      <div class="publication-info">
        {{ post.description }}
      </div>
    </div>
  {% endfor %}
</div>
