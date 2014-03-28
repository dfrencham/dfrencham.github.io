---
layout: page
---
{% include JB/setup %}

<div>
<div class="fleft">
<h3>{{ site.categories["tech"].first.title }}</h3>
<p class="text-primary">{{ site.categories["tech"].first.date | date_to_string }} 
	<span class="label label-success">Tech</span></p>
{% if site.categories["tech"].first.content contains '<!--more-->' %}
{{ site.categories["tech"].first.content | split:'<!--more-->' | first }}
{% else %}
{{ site.categories["tech"].first.content | truncatewords:200 | strip_html }}
{% endif %}
<a href="{{ BASE_PATH }}{{ site.categories["tech"].first.url }}" class="btn btn-default">
  Read More <span class="glyphicon glyphicon-arrow-right"></span>
</a>
</div>

<div class="fright">
<h3>{{ site.categories["diy"].first.title }}</h3>
<p class="text-primary">{{ site.categories["diy"].first.date | date_to_string }}
<span class="label label-danger">DIY</span></p>
{% if site.categories["diy"].first.content contains '<!--more-->' %}
{{ site.categories["diy"].first.content | split:'<!--more-->' | first }}
{% else %}
{{ site.categories["diy"].first.content | truncatewords:200 | strip_html }}
{% endif %}
<a href="{{ BASE_PATH }}{{ site.categories["diy"].first.url }}" class="btn btn-default">
  Read More <span class="glyphicon glyphicon-arrow-right"></span>
</a>
</div>
</div>
<p style="clear:both;" />
<hr style="margin-top:5px;border-top: dashed 1px; border-color:#808080;">
## Recent Posts

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

<hr style="margin-top:5px;border-top: dashed 1px; border-color:#808080;">
## About

Danny Frencham is a 30-something software developer, based in Brisbane Australia. Danny works primarily in the .Net space, and is currently writing Single-Page-Apps for large enterprise clients. On weekends, you can find him attempting DIY projects (badly), or integrating things in odd ways (ever seen a RaspberryPi reading a home power meter with a webcam and OCR?).
