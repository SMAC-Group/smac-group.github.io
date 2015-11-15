---
layout: page
title: Methods
permalink: /methods/
---

SMAC has a very strong methods background. Below are methods based posts:


{% for post in site.posts %}
  {% if post.categories contains 'postcategory' %}
    <h1>Do nothing</h1>
  {% else %}
    <h2>{{ post.title }}</h2>
  {% endif %}
{% endfor %}

{% for category in site.categories %}
  {% if post.categories contains 'methods' %}
	<ul class="posts-list">
	{% for post in site.categories[cat] %}
		<li>
			<strong>
				<a href="{{ post.url | remove_first: '/' | prepend: site.baseurl }}">{{ post.title }}</a>
			</strong>
			<span class="post-date">- {{ post.date | date_to_long_string }}</span>
		</li>
	{% endfor %}
	</ul>
    {% endif %}
{% endfor %}