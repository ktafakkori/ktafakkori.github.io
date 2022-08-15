---
layout: page
permalink: /categories/
title: 🗃️Archive
---

<b>Categories:</b>

<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>
    <h5 class="category-head">{{ category_name }}</h5>
    <a name="{{ category_name | slugize }}"></a>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <h5><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h5>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>

<b>Tags:</b>

<div id="archives">
{% for tag in site.tags %}
  <div class="archive-group">
    {% capture tag_name %}{{ tag | first }}{% endcapture %}
    <div id="#{{ tag_name | slugize }}"></div>
    <p></p>
    <h5 class="tag-head">{{ tag_name }}</h5>
    <a name="{{ tag_name | slugize }}"></a>
    {% for post in site.tags[tag_name] %}
    <article class="archive-item">
      <h5><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h5>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>
