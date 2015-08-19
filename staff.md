---
layout: default
img: textbook.jpg
img_link: http://algs4.cs.princeton.edu/home/
caption: The course textbook
title: staff
active_tab: staff
---

<div class="container-fluid">
  <div class="row">
  {% for staff in site.data.staff %}
      <div class="col-md-3 col-xs-6" style="margin-bottom: 20px">
        <img src="{{staff.pic}}" style="height: 100%; width: 100%; max-height: 200px; max-width: 200px"/>
      </div>
      <div class="col-md-3 col-xs-6" style="height: 200px; padding: 20px; margin-bottom: 20px">
        <span> <b>{{ staff.name }}</b></span><br>
        <span> {{ staff.email }}</span><br>
        {% if staff.extra_title %}
        <span> {{ staff.extra_title }}</span><br>
        {% endif %}
        <br>
 	{% if staff.lab %}
        <span> Lab: {{ staff.lab }}</span><br>
        {% endif %}
 	{% if staff.office_hours %}
        <span> Office Hours: {{ staff.office_hours }}</span>
        {% endif %}
      </div>
  {% endfor %}
  </div>
</div>



