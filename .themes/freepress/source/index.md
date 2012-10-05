---
layout: home
title: Best Practices
contributors: Harlan T Wood
---

{% for content_page in site.html_pages %}
  {% if content_page.title == 'Site Introduction' %}
<article>
  <div class="entry-content">
    {{ content_page.content }}
  </div>
</article>
  {% endif %}
{% endfor %}

{% include set_max_rank %}
{% for rank in (1..max_rank) %}
  {% for content_page in site.html_pages %}
    {% if content_page.rank == rank %}
      {% if content_page.layout == 'page' %}
        {% if content_page.status != 'unlisted' %}
<article id="{{ content_page.title | replace: ' ', '-' }}">
  <header>
    <h1>{{ content_page.title }}</h1>
  </header>
  <div class="entry-content">
    {{ content_page.content }}
  </div>
</article>
        {% endif %}
      {% endif %}
    {% endif %}
  {% endfor %}
{% endfor %}
