---
layout: page
title: Methods
permalink: /methods/
---

<div class="wrapper">

<div class="mgrid">
	{% for post in site.categories['methods'] %}
		<div class="box">
			<strong>
				<a href="{{ post.url  | prepend: site.url }}">{{ post.title }}</a>
			</strong>
			{% if post.spic %} 
			<img src="/{{ post.spic | prepend: site.url }}" alt="{{ post.title }}" class="nv" />
			{% else %}
			<img src="{{ '/assets/images/site/cities/earth_default_reduced.jpg' | prepend: site.url }}" alt="{{ post.title }}" class="nv"/>
			{% endif %}
			<p class="post-abstract">{{ post.abstract }} </p>
			<a href="{{ post.url | prepend: site.url }}">Read More &raquo;</a>
		</div>
	{% endfor %}
</div>

</div>