---
layout: default
title: TeamProject
description: This page records a team project.
---

{% assign team_posts = site.posts | where: "tags", "team" %}
{% for post in team_posts %}
  <article>
    <h2><a href="{{ post.url }}">{{ post.path | split: '/' | last | split: '.' | first }}</a></h2>
    <p>{{ post.excerpt }}</p>
    <p>{{ post.date | date: "%Y-%m-%d" }}</p>
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
