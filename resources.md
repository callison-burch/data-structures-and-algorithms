---
layout: default
img: textbook.jpg
img_link: http://algs4.cs.princeton.edu/home/
caption: The course textbook
title: resources
active_tab: resources
---



<div>
	<ul class="resource-header-list">
    {% for resource in site.data.resources %}
		<li>
	        <h3 class="resource-header">{{ resource.header }}</h3>
	        <ul class="resource-content">
	        {% for link in resource.links %}
	            <li><a href="{{ link.link }}">{{ link.text }}</a></li>
	        {% endfor %}
	       </ul>
	    </li> 
    {% endfor %}
    </ul>
</div>