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
				<a href="{{ post.url | remove_first: '/' | prepend: site.baseurl }}">{{ post.title }}</a>
			</strong>
			{% if page.spic %} 
			<img src="{{ post.spic | prepend: site.baseurl }}" alt="{{ post.title }}" class="nv" />
			{% else %}
			<img src="{{ 'assets/images/site/cities/earth_default_reduced.jpg' | prepend: site.baseurl }}" alt="{{ post.title }}" class="nv"/>
			{% endif %}
			<span class="post-date">{{ post.date | date_to_long_string }}</span>
			<span class="post-abstract">{{ post.abstract }} </span>
			<a href="{{ post.url | remove_first: '/' | prepend: site.baseurl }}">Read More &raquo;</a>
		</div>
	{% endfor %}
</div>

</div>