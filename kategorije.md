---
layout: default
title: Kategorije
---

<p>Postovi iz kategorije "linux" su:</p>

<ul>
  {% for post in site.categories.linux %}
    {% if post.url %}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>

<p>Postovi iz kategorije "ruby" su:</p>

<ul>
  {% for post in site.categories.ruby %}
    {% if post.url %}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
