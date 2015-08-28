---
layout: default
title: CIS 121 Homework Assignments
active_tab: homework
---

<table class="table table-striped">
  <tbody>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Materials</th>
      <th>Release Date</th>
      <th>Due Date</th>
    </tr>
      {% for homework in site.data.homeworks %}
        <tr style="text-align: left">
          <!-- Homework Name -->
          <td><span>{{ homework.assignment }}</span></td>
          <!-- Type -->
          <td>
            <span>{{ homework.type }}</span>
          </td>
          <!-- Materials -->
          <td>
            <ul class="list-unstyled">
              {% if homework.active %}
                {% if homework.writeup %}<li><a href="{{ homework.writeup }}">Write-up</a></li>{% endif %}
                {% if homework.zip %}<li><a href="{{ homework.zip }}">Files (zip)</a></li>{% endif %}
              {% else %}
                 <li>Coming soon!</li>
              {% endif %}
            </ul>
          </td>
          <!-- Dates -->
          <td>{{ homework.release_date | date: "%b %d" }}</td>
          <td>{{ homework.due_date | date: "%b %d" }}</td>
        </tr>
      {% endfor %}
  </tbody>
</table>
