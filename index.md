---
layout: page
---
{% include JB/setup %}

<div>
	<div class="fleft">
	{% for techpost in site.categories["tech"] limit: 2 %}
	<h3 class="post-title"><a href="{{techpost.url}}">{{ techpost.title }}</a></h3>
	<p class="text-primary">{{ techpost.date | date_to_string }}
		<span class="label label-success">Tech</span></p>
	{% if techpost.skip_title != null %}
	{{ techpost.description }}
	{% endif %}
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
	<h3 class="post-title"><a href="{{diypost.url}}" class="post-title">{{ diypost.title }}</a></h3>
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

{% assign diy = 0 %}
{% assign tech = 0 %}

<div class="row">
	<div class="col-xs-12 col-sm-6">


	<h3>Build It</h3>
	{% for tag in site.tags %}
		{% if tag[0] contains 'build-it' %}
	  <ul>
	    {% assign pages_list = tag[1] %}
	    {% include JB/pages_list %}
	  </ul>
		{% endif %}
	{% endfor %}

	<h3>Demolish It</h3>
	{% for tag in site.tags %}
		{% if tag[0] contains 'demolition' %}
	  <ul>
	    {% assign pages_list = tag[1] %}
	    {% include JB/pages_list %}
	  </ul>
		{% endif %}
	{% endfor %}

	<h3>Fix It</h3>
	{% for tag in site.tags %}
		{% if tag[0] contains 'fix-it' %}
	  <a class="tag-anchor" id="{{ tag[0] }}-ref"></a>
	  <ul>
	    {% assign pages_list = tag[1] %}
	    {% include JB/pages_list %}
	  </ul>
		{% endif %}
	{% endfor %}

	<h3>Reviews</h3>
	{% for tag in site.tags %}
		{% if tag[0] contains 'review' %}
	  <ul>
	    {% assign pages_list = tag[1] %}
	    {% include JB/pages_list %}
	  </ul>
		{% endif %}
	{% endfor %}

	</div>
	<div class="col-xs-12 col-sm-6">

	<h3>Code It</h3>
	{% for tag in site.tags %}
		{% if tag[0] contains 'programming' %}
	  <ul>
	    {% assign pages_list = tag[1] %}
	    {% include JB/pages_list %}
	  </ul>
		{% endif %}
	{% endfor %}

	<h3>Tech Guides</h3>
	{% for tag in site.tags %}
		{% if tag[0] contains 'tech-guide' %}
	  <ul>
	    {% assign pages_list = tag[1] %}
	    {% include JB/pages_list %}
	  </ul>
		{% endif %}
	{% endfor %}

	</div>
</div>

<hr style="margin-top:5px;border-top: dashed 1px; border-color:#808080;">
<div class="row">
	<div class="col-md-6 col-xs-12">
		<h2>Tags</h2>
	<!-- start tag cloud -->
	<div>
		{% include JB/tag_cloud %}
	</div>
	<!-- end tag cloud -->
	</div>

	<div class="col-md-6 col-xs-12">
		<h2>About</h2>
Danny Frencham is a 30-something software developer, based in Brisbane Australia. Danny works primarily in the .Net space, and is currently writing Single-Page-Apps for large enterprise clients. On weekends, you can find him attempting DIY projects (badly), or integrating things in odd ways (ever seen a RaspberryPi reading a home power meter with a webcam and OCR?).
	</div>
</div>
