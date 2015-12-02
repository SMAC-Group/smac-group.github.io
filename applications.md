---
layout: page
title: Applications
permalink: /applications/
---

<div class="wrapper">

{% if site.categories.applications == null %}

We're working on providing application cases.

{% else %}

<div class="mgrid">
	{% for post in site.categories['applications'] %}
		<div class="box">
			<strong>
				<a href="{{ post.url | remove_first: '/' | prepend: site.baseurl }}">{{ post.title }}</a>
			</strong>
			{% if post.spic %} 
			<img src="{{ post.spic | prepend: site.baseurl }}" alt="{{ post.title }}" class="nv" />
			{% else %}
			<img src="{{ 'assets/images/site/cities/earth_default_reduced.jpg' | prepend: site.baseurl }}" alt="{{ post.title }}" class="nv"/>
			{% endif %}
			<span class="post-date">{{ post.date | date_to_long_string }}</span>
			<p class="post-abstract">{{ post.abstract }} </p>
			<a href="{{ post.url | remove_first: '/' | prepend: site.baseurl }}">Read More &raquo;</a>
		</div>
	{% endfor %}
</div>

{% endif %}


</div>
