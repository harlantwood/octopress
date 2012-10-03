---
layout: home
title: Best Practices
contributors: Harlan T Wood
---

{% capture page_urls %}
  {{ site.html_pages | sort:'url' | map:'url' | join:' ' }}
{% endcapture %}

{% capture num_urls %}
  {{ page_urls | number_of_words }}
{% endcapture %}


{% for index in (1..num_urls) %}
  {% capture page_url %}{{ page_urls | truncatewords:index | remove:'...' | split:' '  | last }}{% endcapture %}

  {% for content_page in site.html_pages %}
    {% if content_page.url == page_url %}
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


