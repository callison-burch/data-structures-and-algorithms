---
layout: default
title: Staff
active_tab: staff
---

<div class="table-responsive">
<table class="table">
  <tbody>
  {% for staff in site.data.staff %}
    <tr style="text-align: left"> 
      <td><img src="{{staff.pic_left}}" style="height: 200px; width: 200px"/></td>
      <td>
        <span> <b>{{ staff.name_left }}</b></span><br>
        <span> {{ staff.email_left }}</span><br><br>
        <span> {{ staff.lab_left }}</span><br>
        <span> {{ staff.office_hours_left }}</span>



      </td>

      <td><img src="{{staff.pic_right}}" style="height: 200px; width: 200px"/></td>
      <td>
        <span> <b>{{ staff.name_right }}</b></span><br>
        <span> {{ staff.email_right }}</span><br><br>
        <span> {{ staff.lab_right }}</span><br>
        <span> {{ staff.office_hours_right }}</span>
      </td>

    </tr>
  {% endfor %}
  </tbody>
  
</table>
</div>



