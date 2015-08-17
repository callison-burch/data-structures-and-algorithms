---
layout: default
img: textbook.jpg
img_link: http://algs4.cs.princeton.edu/home/
caption: The course textbook
title: homework
active_tab: homework
---

<table class="table table-striped"> 
  <tbody>
    <tr>
      <th>Name</th>
      <th>Materials</th>
      <th>Due Date</th>
    </tr>
      {% for homework in site.data.homeworks %}
        <tr style="text-align: left">
          <!-- Homework Name -->
          <td><span>{{ homework.name }}</span></td>
          <!-- Materials -->
          <td>
            <span><a href="{{ homework.link }}">{{ homework.link_name }}</a></span>
          </td>
          <!-- Due Date -->
          <td>{{ homework.date | date: "%b %d" }}</td>
        </tr>
      {% endfor %}
  </tbody>
</table>

