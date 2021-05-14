---
layout: profile
title: Anthony Vadala - About
permalink: /
---

<!-- Profile Header -->
<div id="background">
	<div id="circular"></div>
</div>

<!-- Short Intro -->
{% if site.header_text %}
<div id="title">{{ site.header_text }}</div>
{% endif %} {% if site.description_text %}
<div id="sub-title">{{ site.description_text }}</div>
{% endif %}

<!-- Social Media Links -->
<ul class="buttonList">
	{% if site.twitter_username %}
	<li class="button twitter">
		<a href="https://twitter.com/{{ site.twitter_username }}" rel="noopener" accesskey="t" data-instant>
			<span class="fab fa-twitter"></span> Twitter</a>
	</li>
	{% endif %} {% if site.linkedin_username %}
	<li class="button linkedin">
		<a href="https://www.linkedin.com/in/{{ site.linkedin_username }}" rel="noopener" accesskey="l" data-instant>
			<span class="fab fa-linkedin-in"></span> LinkedIn</a>
	</li>
	{% endif %}{% if site.github_username %}
	<li class="button github ">
		<a href="https://github.com/{{ site.github_username }}" rel="noopener" accesskey="g" data-instant>
			<span class="fab fa-github"></span> GitHub</a>
	</li>
	{% endif %} {% if site.gitlab_username %}
	<li class="button gitlab ">
		<a href="https://gitlab.com/{{ site.gitlab_username }}" rel="noopener" accesskey="i" data-instant>
			<span class="fab fa-gitlab"></span> GitLab</a>
	</li>
	{% endif %} {% if site.keybase_username %}
	<li class="button keybase">
		<a href="https://keybase.io/{{ site.keybase_username }}" rel="noopener" accesskey="k">
			<span class="fab fa-keybase"></span> Keybase</a>
	</li>
	{% endif %}
</ul>

<!-- Project Container -->
<div class="projectContainer">

	<!-- Projects Section -->
	<div class="section-header">
		<span class="fas fa-code"></span> Projects
	</div>
	<div class="img-wrapper">
		<a href="https://www.adamscable.com/" rel="noopener" target="_blank">
			<figure>
				<img src="/images/projects/adams_cable_service.png" alt="Picture of Adams Cable Service Website" />
				<figcaption>Adams Cable Service</figcaption>
			</figure>
		</a>
		<a href="https://forestcitynews.com" rel="noopener" target="_blank">
			<figure>
				<img src="/images/projects/forest_city_news.png" alt="Picture of The Forest City News Website"/>
				<figcaption>The Forest City News</figcaption>
			</figure>
		</a>
	</div>
	<div class="img-wrapper">
		<a href="https://manelinehairdesign.com" rel="noopener" target="_blank">
			<figure>
				<img src="/images/projects/mane_line_hair_design.png" alt="Picture of Mane Line Hair Design Website"/>
				<figcaption>Mane Line Hair Design</figcaption>
			</figure>
		</a>
		<a href="https://foundryvtt.wiki" rel="noopener" target="_blank">
			<figure>
				<img src="/images/projects/foundry_vtt_wiki.png" alt="Picture of Foundry VTT Community Wiki"/>
				<figcaption>Foundry VTT Community Wiki</figcaption>
			</figure>
		</a>
	</div>

</div>
