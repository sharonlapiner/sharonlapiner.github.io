---
layout: page
title: projects
permalink: /projects/
description: 
nav: true
nav_order: 3
display_categories: [current, past]
horizontal: false
---

<style>
:root {
  --global-theme-color: #e8612c !important;
}
.navbar.navbar-light .navbar-nav .nav-item .nav-link:hover {
  color: #e8612c !important;
}
</style>


<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>


<!-- <style>
  h2.category { color: var(--global-text-color) !important; }
  hr { border-color: var(--global-divider-color) !important; }
</style> -->
<style>
h2.category { color: var(--global-theme-color) !important; }
hr.category { border-color: var(--global-theme-color) !important; border-top-width: 1px !important; opacity: 1 !important; }
/* .card-title { font-size: 0.99rem !important; }
.card-text { font-size: 0.88rem !important; } */
</style>

