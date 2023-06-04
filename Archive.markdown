---
layout: page
permalink: /categories/
title: 🗃️Archive
---

<div class="archive-section">
  <h3>Categories:</h3>
  <div class="archive-list">
    {% for category in site.categories %}
      {% capture category_name %}{{ category | first }}{% endcapture %}
      <a href="#{{ category_name | slugize }}" class="archive-link">{{ category_name }}</a>
    {% endfor %}
  </div>
  {% for category in site.categories %}
    <div class="archive-group">
      {% capture category_name %}{{ category | first }}{% endcapture %}
      <h4 id="{{ category_name | slugize }}" class="category-head">{{ category_name }}</h4>
      {% for post in site.categories[category_name] %}
        <article class="archive-item">
          <h5><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h5>
        </article>
      {% endfor %}
    </div>
  {% endfor %}
</div>

<div class="archive-section">
  <h3>Tags:</h3>
  <div class="archive-list">
    {% for tag in site.tags %}
      {% capture tag_name %}{{ tag | first }}{% endcapture %}
      <a href="#{{ tag_name | slugize }}" class="archive-link">{{ tag_name }}</a>
    {% endfor %}
  </div>
  {% for tag in site.tags %}
    <div class="archive-group">
      {% capture tag_name %}{{ tag | first }}{% endcapture %}
      <h4 id="{{ tag_name | slugize }}" class="tag-head">{{ tag_name }}</h4>
      {% for post in site.tags[tag_name] %}
        <article class="archive-item">
          <h5><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h5>
        </article>
      {% endfor %}
    </div>
  {% endfor %}
</div>

