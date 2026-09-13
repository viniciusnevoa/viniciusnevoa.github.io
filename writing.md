---
layout: default
permalink: /writing/
title: Writing
---

Notes, expository pieces, and the occasional argument. Anything here is less careful than a paper and
more careful than a seminar question.

{% if site.posts.size > 0 %}
<ul class="entries">
{% for post in site.posts %}
  <li>
    <span class="entry-date">{{ post.date | date: "%-d %B %Y" }}</span>
    <a class="entry-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {% if post.summary %}<span class="pub-meta">{{ post.summary }}</span>{% endif %}
  </li>
{% endfor %}
</ul>
{% else %}
<p>Nothing here yet.</p>
{% endif %}
