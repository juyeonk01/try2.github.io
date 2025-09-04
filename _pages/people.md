---
title: People
permalink: /people/
layout: single
classes: people-page
---

{% assign people_sorted = site.people | sort: 'joined' %}
{% assign role_order = "pi|phd|ms" | split: "|" %}

{% for role in role_order %}
{% assign members = people_sorted | where: "position", role %}
{% if members.size > 0 %}
<h3>
{% if role == "pi" %}Professor{% elsif role == "phd" %}Ph.D. Students{% elsif role == "ms" %}M.S. Students{% endif %}
</h3>

<div class="people-grid">
  {% for p in members %}
  <a class="person-card" href="{{ p.url | relative_url }}">
    {% if p.image %}
    <div class="media">
      <img src="{{ p.image | relative_url }}" alt="{{ p.name }}">
    </div>
    {% endif %}
    <div class="person-meta">
      <div class="person-name">{{ p.name }}</div>
      <div class="person-role">
        {% if p.role_label %}
          {{ p.role_label }}
        {% else %}
          {% case p.position %}
            {% when "pi" %}Professor
            {% when "postdoc" %}Postdoc
            {% when "phd" %}Ph.D. Student
            {% when "ms" %}M.S. Student
          {% endcase %}
        {% endif %}
        {% if p.joined %} ({{ p.joined }}~){% endif %}
      </div>
    </div>
  </a>
  {% endfor %}
</div>
{% endif %}
{% endfor %}

{% assign alumni = site.data.alumni | sort: "graduated" | reverse %}
{% if alumni and alumni.size > 0 %}
<h3>Alumni</h3>
<table class="alumni-table">
<thead><tr><th>Name</th><th>Degree & Year</th><th>Current Position</th></tr></thead>
<tbody>
{% for a in alumni %}
<tr>
  <td>{{ a.name }}</td>
  <td>{{ a.degree }} ({{ a.graduated }})</td>
  <td>{{ a.current }}</td>
</tr>
{% endfor %}
</tbody>
</table>
{% endif %}
