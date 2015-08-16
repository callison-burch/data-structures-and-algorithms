---
layout: default
img: textbook.jpg
img_link: http://algs4.cs.princeton.edu/home/
caption: The course textbook
title: resources
active_tab: resources
---


<div>
    {% for resource in site.data.resources %}
    <h3>{{ resource.header }}</h3>
        <ul>
            {% for link in resource.links %}
            <li><a href="{{ link.link }}">{{ link.text }}</a></li>
            {% endfor %}
        </ul>
    {% endfor %}
</div>