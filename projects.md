---
layout: default
title: Projects
permalink: /projects/
---

# Projects

## AI learning path

Three hands-on projects, each building on the last: build something with Claude, then measure it properly.

{% assign learning_path = site.projects | where_exp: "p", "p.learning_path" | sort: "learning_path" %}
<div class="project-list">
{% for project in learning_path %}
  <a class="project-card" href="{{ project.url | relative_url }}">
    <span class="project-card__step">Step {{ project.learning_path }}</span>
    <h3>{{ project.title }}</h3>
    <p>{{ project.summary }}</p>
  </a>
{% endfor %}
</div>

## Work

{% assign work = site.projects | where_exp: "p", "p.learning_path == nil" %}
<div class="project-list">
{% for project in work %}
  <a class="project-card" href="{{ project.url | relative_url }}">
    <h3>{{ project.title }}</h3>
    <p>{{ project.summary }}</p>
  </a>
{% endfor %}
</div>
