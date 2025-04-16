---
layout: page
permalink: /blog/
title: Blog
description: Research insights and technical explorations.
nav: true
nav_order: 3
---

<div class="publications">
  {% for post in site.posts %}
  <div class="publication">
    <div class="row">
      {% if post.image %}
      <div class="col-sm-3">
        <div class="image-container">
          <img src="{{ post.image | relative_url }}" class="img-fluid" alt="{{ post.title }}">
        </div>
      </div>
      <div class="col-sm-9">
      {% else %}
      <div class="col-sm-12">
      {% endif %}
        <div class="title">
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </div>
        <div class="author">
          {{ post.date | date: "%B %-d, %Y" }}
          {% if post.author %} • {{ post.author }}{% endif %}
        </div>
        <div class="periodical">
          {{ post.description }}
        </div>
        <div class="links">
          <a href="{{ post.url | relative_url }}" class="btn btn-sm z-depth-0" role="button">View Post</a>
          {% if post.arxiv %}
          <a href="http://arxiv.org/abs/{{ post.arxiv }}" class="btn btn-sm z-depth-0" role="button">arXiv</a>
          {% endif %}
          {% if post.code %}
          <a href="{{ post.code }}" class="btn btn-sm z-depth-0" role="button">Code</a>
          {% endif %}
          {% if post.website %}
          <a href="{{ post.website }}" class="btn btn-sm z-depth-0" role="button">Website</a>
          {% endif %}
        </div>
      </div>
    </div>
  </div>
  {% endfor %}
</div>
