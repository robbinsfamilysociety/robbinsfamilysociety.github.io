---
layout: page
title: Tod Robbins
permalink: /about/tod-robbins
---

<img class="avatar" src="/assets/images/tod-robbins.jpg" alt="{{ page.author }}"/>

**Tod Robbins** is a co-founder of the Robbins Family Society.
<br><br>
<hr>
<h1 class="page-heading">Recent posts by Tod</h1>
  <ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        </h2>
      </li>
    {% endfor %}
  </ul>