---
layout: page
title: TeamProject
description: This page records a team project.
---

{% assign all_team_posts = site.posts | where: "tags", "team" %}
{% assign team_posts = all_team_posts | slice: 0, paginator.per_page %}

<ul id="posts">
{% for post in team_posts %}
  <li class="post">
    <h2><a href="{% if site.baseurl == "/" %}{{ post.url }}{% else %}{{ post.url | prepend: site.baseurl }}{% endif %}">{%if post.header %}{{ post.header }}{% else %}{{ post.title }}{% endif %}</a></h2>
    <time datetime="{{ post.date | date_to_xmlschema }}" class="by-line"><i>{{ post.date | date: "%Y-%m-%d" }}</i></time>
    <p>{{ post.content | strip_html | truncatewords:50 }}</p>
  </li>
{% endfor %}
</ul>

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
