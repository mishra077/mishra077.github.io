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
          <a href="{{ post.url | relative_url }}" class="btn btn-sm z-depth-0" role="button">Read</a>
          {% if post.arxiv %}
          <a href="http://arxiv.org/abs/{{ post.arxiv }}" class="btn btn-sm z-depth-0" role="button">arXiv</a>
          {% endif %}
          {% if post.code %}
          <a href="{{ post.code }}" class="btn btn-sm z-depth-0" role="button">Code</a>
          {% endif %}
        </div>
      </div>
    </div>
  </div>
  {% endfor %}
  
  {% if site.external_sources %}
  <h2 class="mt-4">External Articles</h2>
  {% for source in site.external_sources %}
    <div class="publication">
      <div class="row">
        <div class="col-sm-3">
          <div class="image-container">
            {% if source.name == "medium.com" %}
            <img src="{{ '/assets/img/external/medium-logo.svg' | relative_url }}" class="img-fluid" alt="Medium Logo">
            {% elsif source.name == "Google Blog" %}
            <img src="{{ '/assets/img/external/google-blog-logo.svg' | relative_url }}" class="img-fluid" alt="Google Blog Logo">
            {% elsif source.name == "Substack" %}
            <img src="{{ '/assets/img/external/substack-logo.svg' | relative_url }}" class="img-fluid" alt="Substack Logo">
            {% else %}
            <img src="{{ '/assets/img/external/external-source.svg' | relative_url }}" class="img-fluid" alt="External Source">
            {% endif %}
          </div>
        </div>
        <div class="col-sm-9">
          <div class="source-name">{{ source.name }}</div>
          {% if source.rss_url %}
          <div class="periodical">
            Articles available via <a href="{{ source.rss_url }}" target="_blank">RSS Feed</a>
          </div>
          {% endif %}
          
          {% if source.posts %}
            {% for post in source.posts %}
            <div class="external-source">
              <div class="title">
                <a href="{{ post.url }}" target="_blank">{{ post.url | split: '/' | last | replace: '-', ' ' | capitalize }}</a>
              </div>
              {% if post.published_date %}
              <div class="post-date">
                Published: {{ post.published_date | date: "%B %-d, %Y" }}
              </div>
              {% endif %}
            </div>
            {% endfor %}
          {% endif %}
        </div>
      </div>
    </div>
  {% endfor %}
  {% endif %}
</div>

<script>
  // Check if SVG images are supported, if not fall back to PNG
  document.addEventListener('DOMContentLoaded', function() {
    var testImg = document.createElement('img');
    testImg.setAttribute('src', 'data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPjwvc3ZnPg==');
    
    // If SVG not supported, replace with PNG versions
    testImg.onerror = function() {
      var images = document.querySelectorAll('.image-container img[src*=".svg"]');
      images.forEach(function(img) {
        var src = img.getAttribute('src');
        img.setAttribute('src', src.replace('.svg', '.png').replace('/external/', '/external/png/'));
      });
    };
  });
</script>
