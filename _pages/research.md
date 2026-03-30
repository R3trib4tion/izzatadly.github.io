---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

{% comment %}
  This loop goes through the categories you defined in _config.yml
{% endcomment %}

{% for category in site.publication_category %}
  {% assign category_id = category[0] %}
  {% assign category_title = category[1].title %}
  
  {% comment %}
    Filter publications to only those matching the current category
  {% endcomment %}
  {% assign posts = site.publications | where: "category", category_id %}
  
  {% if posts.size > 0 %}
    <h2 id="{{ category_title | slugify }}" class="archive__subtitle">{{ category_title }}</h2>
    {% for post in posts reversed %}
      {% include archive-single.html %}
    {% endfor %}
  {% endif %}
{% endfor %}
