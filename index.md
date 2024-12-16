---
title: TIL
---

<ul>
  {% for post in site.posts %}
    <li>
      <h4><a href="{{ site.baseurl }}/{{ post.url }}">{{ post.title }}</a></h4>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
