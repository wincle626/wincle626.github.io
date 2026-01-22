---
layout: page
title: News
permalink: /news/
---

<h2>Latest News</h2>

<ul>
  {% assign items = site.news | sort: "date" | reverse %}
  {% for item in items %}
    <li>
      <span>{{ item.date | date: "%Y-%m-%d" }}</span> —
      <a href="{{ item.url | relative_url }}">{{ item.title }}</a>
      {% if item.tags and item.tags.size > 0 %} <em>(tags: {{ item.tags | join: ", " }})</em>{% endif %}
    </li>
  {% endfor %}
</ul>

<!-- Optional tag anchors -->
{% if false %}
<h3>Tags</h3>
{% assign all_tags = site.news | map: 'tags' | compact | flatten | uniq | sort %}
<ul>
  {% for t in all_tags %}
    <li id="tag-{{ t }}"><strong>#{{ t }}</strong></li>
    <ul>
      {% for item in items %}
        {% if item.tags contains t %}
          <li><a href="{{ item.url | relative_url }}">{{ item.title }}</a> <small>({{ item.date | date: "%Y-%m-%d" }})</small></li>
        {% endif %}
      {% endfor %}
    </ul>
  {% endfor %}
</ul>
{% endif %}
