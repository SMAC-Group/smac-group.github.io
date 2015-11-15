---
layout: page
title: Methods
permalink: /methods/
---


<ul class="posts-list">
	{% for post in site.categories['methods'] %}
		<li>
			<strong>
				<a href="{{ post.url | remove_first: '/' | prepend: site.baseurl }}">{{ post.title }}</a>
			</strong>
			<span class="post-date">{{ post.date | date_to_long_string }}</span>
		</li>
	{% endfor %}
</ul>