---
layout: page
title: TeamProject
description: This page records a team project.
---

{% assign team_posts = site.posts | where: "tags", "team" %}
{% for post in paginator.posts %}
  {% if post.tags contains "team" %}
    <article>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <time datetime="{{ post.date | date_to_xmlschema }}" class="by-line"> <i>{{ post.date | date: "%Y-%m-%d" }}</i> </time>
      <p>{{ post.content | strip_html | truncatewords:50 }}</p>
    </article>
  {% endif %}
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

