---
layout: home
title: Best Practices
contributors: Harlan T Wood
---

{% for content_page in site.html_pages %}
{% if content_page.layout == 'page' %}
{% if content_page.status != 'unlisted' %}
<article>
  <header>
    <h1>{{ content_page.title }}</h1>
  </header>
  <div class="entry-content">
    {{ content_page.content }}
  </div>
</article>
{% endif %}
{% endif %}
{% endfor %}
