---
layout: default
title: CIS 121 Lectures
active_tab: lectures
---

Subject to change as the term progresses.

<table class="table table-striped">
  <tbody>
    <tr>
      <th>Date</th>
      <th>Topic</th>
      <th>Readings</th>
    </tr>
    {% for lecture in site.data.lectures %}
      <tr>
        <td>{{ lecture.date | date: "%b %d" }}</td>
        <td>
          {% if lecture.profile %}
          Company Profile:
          {% endif %}
          {% if lecture.slides %}<a href="{{ lecture.slides }}">{{ lecture.title }}</a>
          {% else %}{{ lecture.title }}{% endif %}

          {% if lecture.speaker %}
          {% if lecture.speaker_url %} by <a href="{{ lecture.speaker_url }}">{{ lecture.speaker }}</a>
          {% else %} by {{ lecture.speaker }}{% endif %}
          {% endif %}

          {% if lecture.highlights %}
            <ul>
             {% for highlight in lecture.highlights %}
               <span class="text-muted"><li>{{ highlight }}</li></span>
             {% endfor %}
            </ul>
          {% endif %}
        </td>
        <td>
          {% if lecture.reading %}
            <ul class="fa-ul">
              {% for reading in lecture.reading %}
                <li>
                  {% if reading.optional %}
                    <i class="fa-li fa fa-star"> </i>
                  {% else %}
                    <i class="fa-li fa"> </i>
                  {% endif %}
                  {% if reading.url %}
                    <a href="{{ reading.url }}">{{ reading.title }}</a>
                  {% else %}
                    {{ reading.title }}
                  {% endif %}
                  {% if reading.author %}
                    by {{ reading.author }}
                  {% endif %}
                </li>
              {% endfor %}
            </ul>
          {% endif %}
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>

Big thanks to [Kevin Wayne](http://www.cs.princeton.edu/~wayne/contact/) for sharing the slides!  If you are an instructor and would like the Keynote versions of the slides, please contact Kevin directly.
