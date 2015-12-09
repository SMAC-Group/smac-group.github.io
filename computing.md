---
layout: page
title: Computing
permalink: /computing/
---

<div class="wrapper">

{% if site.categories.computing == null %}

<p>We're working on providing content that details the computing methods.</p>

<p>Please check back later...</p>
{% else %}

<div class="mgrid">
	{% for post in site.categories['computing'] %}
		<div class="box">
			<strong>
				<a href="{{ post.url | prepend: site.url }}">{{ post.title }}</a>
			</strong>
			{% if post.spic %} 
			<img src="{{ post.spic | prepend:'/' | prepend: site.url }}" alt="{{ post.title }}" class="nv" />
			{% else %}
			<img src="{{ 'assets/images/site/cities/earth_default_reduced.jpg' | prepend: site.url }}" alt="{{ post.title }}" class="nv"/>
			{% endif %}
			<p class="post-abstract">{{ post.abstract }} </p>
			<a href="{{ post.url | prepend: site.url }}">Read More &raquo;</a>
		</div>
	{% endfor %}
</div>

{% endif %}


</div>