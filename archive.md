---
layout: default
title: Anthony Vadala - Archive
permalink: /archive
---

<h1>Archive ({{ site.posts | size }} posts)</h1>

<ul class="posts">
	{% for post in site.posts %}
		{% assign currentdate = post.date | date: "%Y" %}
	{% if currentdate != date %}
		{{ currentdate }}
		{% assign date = currentdate %}
	{% endif %}
	<li><span>{{ post.date | date: "%b %d" }}</span> &raquo; <a href="{{ post.url }}" rel="noopener">{{ post.title }}</a></li>
	{% endfor %}
</ul>