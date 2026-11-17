---
layout: default
title: Home
---
Assistant Professor (Adiunkt) at Institute of Physical Chemistry, Polish Academy of Sciences. Primary research interest is network science, encompassing biological networks and chemical reaction networks. 

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
