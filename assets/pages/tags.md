---
title: Tags
permalink: /tags/
include_nav: true
---

<div class="tags" itemscope itemtype="http://schema.org/Blog">
{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}