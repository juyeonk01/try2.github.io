---
title: News
permalink: /news/
layout: single
classes: wide
---

{% assign news = site.data.news %}
{% if news and news.size > 0 %}
<h3>News</h3>
<table class="news-table">
  <thead>
    <tr>
      <th>Date</th>
      <th>Event</th>
    </tr>
  </thead>
  <tbody>
    {% assign news_items = news | sort: "date" | reverse %}
    {% for item in news_items %}
      <tr>
        <td>{{ item.date }}</td>
        <td>{{ item.text | markdownify }}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>
{% else %}
<p>No news yet. Check back soon!</p>
{% endif %}
