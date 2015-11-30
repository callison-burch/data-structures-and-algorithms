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
            <ul class="list-unstyled">
              <li><a href="{{ lab.link }}">{{ lab.link_name }}</a></li>
              {% if lab.extra_link %}
                <li><a href="{{ lab.extra_link }}">{{ lab.extra_link_name }}</a></li>
            </ul>
              {% endif %}
          </td>
          </td>
          </td>
          <td>{% if lab.solutions_link %}<a href = "{{ lab.solutions_link }}">Solutions</a>{% else %}Coming soon!{% endif %}</td>
        </tr>
      {% endfor %}
  </tbody>
</table>
