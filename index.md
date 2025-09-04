---
layout: home
title: Causal Inference Lab
permalink: /
author_profile: false
entries_layout: list
---

Welcome to our lab!

{% assign news = site.data.news %}
{% if news and news.size > 0 %}
<h3>Latest News</h3>
<ul>
  {% assign news_items = news | sort: "date" | reverse | slice: 0, 3 %}
  {% for item in news_items %}
    <li><strong>{{ item.date }}</strong>: {{ item.text | markdownify }}</li>
  {% endfor %}
</ul>
<p><a href="{{ '/news/' | relative_url }}">See all News →</a></p>
{% endif %}
