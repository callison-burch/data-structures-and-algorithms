---
layout: default
title: CIS 121 Staff
active_tab: staff
---

<div class="container-fluid">
  <div class="row">
  {% for staff in site.data.staff %}
      <div class="col-lg-4 col-md-6 col-xs-12" style="margin-bottom: 20px">
        {% if staff.pic %}<img src="assets/img/staff/{{staff.pic}}" class="img-circle" style="height: 100%; width: 100%; max-height: 250px; max-width: 250px"/><br />
        {% else %}<img src="assets/img/staff/profile-pic.png" class="img-circle" style="height: 100%; width: 100%; max-height: 250px; max-width: 250px"/><br />{% endif %}
        <b>{{ staff.name }}</b><br>
        {% if staff.extra_title %}<b>{{ staff.extra_title }}</b>
        {% endif %}
        <br />
        {{ staff.email }}<br>
       	{% if staff.lab %}Lab: {{ staff.lab }}<br />{% endif %}
       	{% if staff.office_hours %}Office Hours: {{ staff.office_hours }}{% endif %}
      </div>
  {% endfor %}
  </div>
</div>



