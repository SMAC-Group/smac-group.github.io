---
layout: page
title: Methods
permalink: /methods/
---

SMAC has a very strong methods background. Below are methods based posts:

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