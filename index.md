---
layout: page
---
{% include JB/setup %}

<div>
<div class="fleft">
{% for techpost in site.categories["tech"] limit: 2 %}
<h3>{{ techpost.title }}</h3>
<p class="text-primary">{{ techpost.date | date_to_string }} 
	<span class="label label-success">Tech</span></p>
{% if techpost.content contains '<!--more-->' %}
{{ techpost.content | split:'<!--more-->' | first }}
{% else %}
{{ techpost.content | truncatewords:200 | strip_html }}
{% endif %}
<a href="{{ BASE_PATH }}{{ techpost.url }}" class="btn btn-default">
  Read More <span class="glyphicon glyphicon-arrow-right"></span>
</a>
{% endfor %}
</div>

<div class="fright">
{% for diypost in site.categories["diy"] limit: 2 %}
<h3>{{ diypost.title }}</h3>
<p class="text-primary">{{ diypost.date | date_to_string }}
<span class="label label-danger">DIY</span></p>
{% if diypost.content contains '<!--more-->' %}
{{ diypost.content | split:'<!--more-->' | first }}
{% else %}
{{ diypost.content | truncatewords:200 | strip_html }}
{% endif %}
<a href="{{ BASE_PATH }}{{ diypost.url }}" class="btn btn-default">
  Read More <span class="glyphicon glyphicon-arrow-right"></span>
</a>
{% endfor %}
</div>
</div>
<p style="clear:both;" />
<hr style="margin-top:5px;border-top: dashed 1px; border-color:#808080;">
## All Posts

<div class="recentposts">
<ul class="posts">
  {% for post in site.posts %}
    <li> 
    	<a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a> 
    	<div style="padding-left:10px;padding-bottom:10px;">
    		<span>{{ post.date | date_to_string }}</span>
    		{% if post.categories contains 'tech' %}
			<span class="label label-success">Tech</span>
	    	{% endif %}
	    	{% if post.categories contains 'diy' %}
				<span class="label label-danger">DIY</span>
	    	{% endif %}
    	</div>
    </li>
  {% endfor %}
</ul>
</div>

<hr style="margin-top:5px;border-top: dashed 1px; border-color:#808080;">
## About

Danny Frencham is a 30-something software developer, based in Brisbane Australia. Danny works primarily in the .Net space, and is currently writing Single-Page-Apps for large enterprise clients. On weekends, you can find him attempting DIY projects (badly), or integrating things in odd ways (ever seen a RaspberryPi reading a home power meter with a webcam and OCR?).
