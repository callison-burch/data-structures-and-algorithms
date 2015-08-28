---
layout: default
title: CIS 121 Labs
active_tab: labs
---

<table class="table table-striped">
  <tbody>
    <tr>
      <th>Name</th>
      <th>Materials</th>
      <th>Due Date</th>
    </tr>
      {% for lab in site.data.labs %}
        <tr style="text-align: left">
          <!-- Homework Name -->
          <td><span>{{ lab.name }}</span></td>
          <!-- Materials -->
          <td>
            <span><a href="{{ lab.link }}">{{ lab.link_name }}</a></span>
          </td>
          <!-- Due Date -->
          <td>{{ lab.date | date: "%b %d" }}</td>
        </tr>
      {% endfor %}
  </tbody>
</table>