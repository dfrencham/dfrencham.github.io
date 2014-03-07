---
layout: page
title: Danny Frencham's Blog
tagline: software development and other stuff.
---
{% include JB/setup %}


## Recent Posts

<ul class="posts">
  {% for post in site.posts %}
    <li> 
    	<a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a> 
    	<span>{{ post.date | date_to_string }}</span>
    </li>
  {% endfor %}
</ul>
