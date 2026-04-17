---
layout: default
title: Home
---
Project Fellow at Sikkim University focusing on Computational Biology, Graph Neural Networks, and Chemical Reaction Network Theory.

---

### Key Projects
* **[Zinapse](/projects/zinapse)** A high-performance profiler for Protein-Protein Interaction (PPI) networks. Built in Zig using optimized CSR formats to handle large-scale multi-modal biomedical data.

---

### Recent Articles
<div class="item-list">
  {% for post in site.posts limit:5 %}
  <div class="item-row">
    <a href="{{ post.url }}">{{ post.title }}</a>
    <span class="date">{{ post.date | date: "%Y-%m-%d" }}</span>
  </div>
  {% endfor %}
</div>
