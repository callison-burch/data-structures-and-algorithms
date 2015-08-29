---
layout: default
title: CIS 121 Homework Assignments
active_tab: homework
---

Written homeworks *must* include our [cover
sheet](content/hw/cover_sheet_15fa.pdf) with the requisite information filled
out in order for them to be graded. Written homeworks *must* be typeset in
LaTeX. Written homeworks must be submitted online as well as offline in paper
form in class.

For your convenience, we have a LaTeX homework template for you to use.

* [Cover sheet](content/hws/cover_sheet_15fa.pdf)
* [hw.cls](content/hws/hw.cls)
* [sample_hw.tex](content/hws/sample_hw.tex)
* [sample_hw.pdf](content/hws/sample_hw.pdf)

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
