---
layout: default
title: CIS 121 Staff
active_tab: staff
---

<div class="container-fluid">
  <div class="row">
  {% for staff in site.data.staff %}
      <div class="col-lg-4 col-md-6 col-xs-12" style="margin-bottom: 20px">
        <img src="{{staff.pic}}" class="img-circle" style="height: 100%; width: 100%; max-height: 200px; max-width: 200px"/><br />
        <b>{{ staff.name }}</b><br>
        {% if staff.extra_title %}<b>{{ staff.extra_title }}</b><br />{% endif %}
        {{ staff.email }}<br>
 	{% if staff.lab %}Lab: {{ staff.lab }}<br />{% endif %}
 	{% if staff.office_hours %}Office Hours: {{ staff.office_hours }}{% endif %}
      </div>
  {% endfor %}
  </div>
</div>



