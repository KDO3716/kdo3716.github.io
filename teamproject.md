---
layout: page
title: TeamProject
description: This page records a team project.
---

{% assign all_team_posts = site.posts | where: "tags", "team" %}
{% assign team_posts = all_team_posts | slice: 0, paginator.per_page %}

{% for post in team_posts %}
  {% assign filename = post.path | split: '/' | last %}
  {% assign title = filename | split: '.' | first | remove_first: "YY-MM-DD-" %}
  {% assign date = filename | split: '-' %}
  {% assign year = date[0] %}
  {% assign month = date[1] %}
  {% assign day = date[2] %}

  <article>
    <h2><a href="{{ post.url }}">{{ title }}</a></h2>
    <p>{{ year }}-{{ month }}-{{ day }}</p>
    <p>{{ post.excerpt }}</p>
  </article>
{% endfor %}

<div class="pagination">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path }}" class="previous">Previous</a>
  {% endif %}
  {% for page in (1..paginator.total_pages) %}
    <a href="{{ paginator.page_path page }}" class="{% if page == paginator.page %}active{% endif %}">{{ page }}</a>
  {% endfor %}
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path }}" class="next">Next</a>
  {% endif %}
</div>
