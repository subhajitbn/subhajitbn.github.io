---
layout: default
title: Home
---
PhD in Math. Currently working as a project fellow at Sikkim University, funded by the Department of Biotechnology (DBT). Research interests include Network Science, Combinatorics, Computational Biology, and ML.

---

### Key Projects
* **[Genelit](/projects/genelit)** A small but handy tool, built to help scientists quickly perform a literature review on a set of genes associated with a particular cancer type.

---

### Recent Articles
<ul class="articles">
  {% for post in site.posts limit:5 %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
    <span class="date">{{ post.date | date: "%Y-%m-%d" }}</span>
  </li>
  {% endfor %}
</ul>
