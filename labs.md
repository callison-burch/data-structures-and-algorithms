---
layout: default
title: CIS 121 Labs
active_tab: labs
---

<table class="table table-striped">
  <tbody>
    <tr>
      <th>Week of</th>
      <th>Name</th>
      <th>Materials</th>
      <th>Solutions</th>
    </tr>
      {% for lab in site.data.labs %}
        <tr style="text-align: left">
          <td>{{ lab.date | date: "%b %d" }}</td>
          <td><span>{{ lab.name }}</span></td>
          <td>
            <span><a href="{{ lab.link }}">{{ lab.link_name }}</a></span>
          </td>
          <td>{% if lab.solutions_link %}<a href = "{{ lab.solutions_link }}">Solutions</a>{% else %}Coming soon!{% endif %}</td>
        </tr>
      {% endfor %}
  </tbody>
</table>
