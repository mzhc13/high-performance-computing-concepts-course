---
layout: single
title: "Debug"
permalink: /debug/
---

{{ site.programme | size }} sessions found.

<ul>
  {% for s in site.programme %}
    <li>{{ s.title }} ({{ s.path }})</li>
  {% endfor %}
</ul>


