---
layout: default
title: Projects
permalink: /projects/
---

# Projects

<div class="project-list">
{% for project in site.projects %}
  <a class="project-card" href="{{ project.url | relative_url }}">
    <h3>{{ project.title }}</h3>
    <p>{{ project.summary }}</p>
  </a>
{% endfor %}
</div>
