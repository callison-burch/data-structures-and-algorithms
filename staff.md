---
layout: default
title: Staff
active_tab: staff
---

<div class="container-fluid">
  {% for staff in site.data.staff %}
    <div class="row">
      <div class="col-md-3 col-xs-6" style="margin-bottom: 20px">
        <img src="{{staff.pic_left}}" style="height: 100%; width: 100%; max-height: 200px; max-width: 200px"/>
      </div>
      <div class="col-md-3 col-xs-6" style="height: 200px; padding: 20px; margin-bottom: 20px">
        <span> <b>{{ staff.name_left }}</b></span><br>
        <span> {{ staff.email_left }}</span><br>
        {% if staff.extra_title_left %}
        <span> {{ staff.extra_title_left }}</span><br>
        {% endif %}
        <br>
 	{% if staff.lab_left %}
        <span> Lab: {{ staff.lab_left }}</span><br>
        {% endif %}
 	{% if staff.office_hours_left %}
        <span> Office Hours: {{ staff.office_hours_left }}</span>
        {% endif %}
      </div>
      <div class="col-md-3 col-xs-6" style="margin-bottom: 20px">
        <img src="{{staff.pic_right}}" style="height: 100%; width: 100%; max-height: 200px; max-width: 200px"/>
      </div>
      <div class="col-md-3 col-xs-6" style="height:200px; padding: 20px; margin-bottom: 20px">
        <span> <b>{{ staff.name_right }}</b></span><br>
        <span> {{ staff.email_right }}</span><br>
        {% if staff.extra_title_right %}
        <span> {{ staff.extra_title_right }}</span><br>
        {% endif %}
        <br>
 	{% if staff.lab_left %}
        <span> Lab: {{ staff.lab_right }}</span><br>
        {% endif %}
 	{% if staff.office_hours_right %}
        <span> Office Hours:  {{ staff.office_hours_right }}</span>
        {% endif %}
        </div>
      </div>
  {% endfor %}
</div>



