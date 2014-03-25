---
layout: page
title: Danny Frencham's Blog
tagline: software development on weekdays, power tools on weekends.
---
{% include JB/setup %}

<h2>{{ site.posts.first.title }}</h2>
<p class="text-primary">{{ site.posts.first.date | date_to_string }}</p>
{% if site.posts.first.content contains '<!--more-->' %}
{{ site.posts.first.content | split:'<!--more-->' | first }}
{% else %}
{{ site.posts.first.content | truncatewords:200 | strip_html }}
{% endif %}
<a href="{{ BASE_PATH }}{{ site.posts.first.url }}" class="btn btn-default">
  Read More <span class="glyphicon glyphicon-arrow-right"></span>
</a>
<hr>
## Recent Posts

<ul class="posts">
  {% for post in site.posts %}
    <li> 
    	<a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a> 
    	<span>{{ post.date | date_to_string }}</span>
    </li>
  {% endfor %}
</ul>

