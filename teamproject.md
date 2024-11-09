---
layout: page
title: TeamProject
description: This page records a team project.
---

{% assign all_team_posts = site.posts | where: "tags", "team" %}
{% assign team_posts = all_team_posts | slice: 0, paginator.per_page %}

{% for post in team_posts %}
  <article>
    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    <p>{{ post.content | truncate: 150, "..." }}</p>
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
