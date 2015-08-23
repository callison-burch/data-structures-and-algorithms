---
layout: default
img: textbook.jpg
img_link: http://algs4.cs.princeton.edu/home/
caption: The course textbook
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
            <span><a href="{{ homework.link }}">Download</a></span>
          </td>
          <!-- Dates -->
          <td>{{ homework.release_date | date: "%b %d" }}</td>
          <td>{{ homework.due_date | date: "%b %d" }}</td>
        </tr>
      {% endfor %}
  </tbody>
</table>

