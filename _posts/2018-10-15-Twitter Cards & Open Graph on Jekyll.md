---
title: Twitter Cards & Open Graph on Jekyll
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

## Getting Started
{% raw %}
In Jekyll, there are two types of variables:
- `{{ site.VARIABLENAME }}` for the entire Site located in `_config.yml` ([mine](https://github.com/AnthonyVadala/AnthonyVadala.github.io/blob/master/_config.yml))
- `{{ page.VARIABLENAME }}` for a specific Page located in the front matter block (see [YAML](https://jekyllrb.com/docs/front-matter/))
{% endraw %}

{% raw %}
The Jekyll variables we will be using are:
`{{ site.url }}`
`{{ site.description }}`
`{{ site.photo_embed }}`
`{{ site.twitter_username }}`
`{{ page.url }}`
`{{ page.title }}`
`{{ page.excerpt }}` 
{% endraw %}

In your `_config.yml` make sure to define "url", "description", "photo_embed", and "twitter_username". For example, this is how mine are defined:
```
...
url: "https://anthonyvadala.me" # The base hostname & protocol for the site
...
photo_embed: /images/profile_picture.jpg # Sets picture for Twitter Card/Open Graph
description: Hello, I'm Anthony Vadala! I am an aspiring network specialist and hobbyist web designer.
...
twitter_username: Anthony_Vadala
...
```

<!--more-->

For each individual post set the front matter block. For this post mine looks like this:
```
---
title: Twitter Cards & Open Graph on Jekyll
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---
```

## Twitter Cards documentation
Looking at the [Twitter Cards documentation](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards) there are several card types available; since I’m not doing any video or linking to apps, I’m looking at using two card types:
- Summary Card
- Summary Card with Large Image

Looking at both types’ properties, the required properties are the same ("card", "title", "description").

### Twitter Cards properties
Here is the metadata we will be setting for Twitter:
- `twitter:card` - Used to define the type of card Twitter will display. We will be using "summary".
- `twitter:title` - The post title.
- `twitter:url` - The link to the post/page.
- `twitter:description` - The text that will be displayed below the title.
- `twitter:site` - Your Twitter handle. I am referencing mine using `site.twitter_username` to reduce hard-coded values.
- `twitter:image` - The image shown. I am using my profile picture using `site.photo_embed`.

### Twitter Code
{% raw %}
```
<meta property="twitter:card" content="summary">
<meta name="twitter:title" content="{{ page.title }}">
<meta name="twitter:url" content="{{ site.url }}{{ page.url }}">
<meta name="twitter:description" content="{% if page.excerpt %}{{ page.excerpt | strip_html | strip_newlines | truncate: 160 }}{% else %}{{ site.description }}{% endif %}">
<meta property="twitter:site" content="{{ site.twitter_username }}">
<meta property="twitter:image" content="{{ site.url }}{{ site.photo_embed }}">
```
{% endraw %}


## Open Graph
According to the [official Open Graph protocol documentation](http://ogp.me/), the basic required properties to use Open Graph are: "type", "title", "image", and "url".

Unlike Twitter Cards, the Open Graph protocol is supported by many major websites such as: Facebook, Pinterest, Linkedin, Google Plus (RIP) and even Twitter uses it as a [fall back option](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started#opengraph)!

### Open Graph properties
Here is the metadata we will be setting for Open Graph:
- `og:type` - Used to define the type of object that will display. We will be using "article".
- `og:title` - The title that will be displayed.
- `og:url` - The link to the post/page.
- `og:description` - The text that will be displayed below the title.
- `og:image` - The image shown. I am using my profile picture using `site.photo_embed`.

### Open Graph Code
{% raw %}
```
<meta property="og:type" content="article">
<meta property="og:title" content="{{ page.title }}">
<meta property="og:url" content="{{ site.url }}{{ page.url }}">
<meta property="og:description" content="{% if page.excerpt %}{{ page.excerpt | strip_html | strip_newlines | truncate: 160 }}{% else %}{{ site.description }}{% endif %}">
<meta property="og:image" content="{{ site.url }}{{ site.photo_embed }}">
```
{% endraw %}


## Putting it all together
For both `twitter:description` and `og:description`, I did a simple if else statement. If the page is a post, it will display an excerpt from the post, striping all HTML, newlines and truncates down it to 160 characters. Else it will display the website description from `_config.yml`

{% raw %}
```
{% if page.excerpt %}
	{{ page.excerpt | strip_html | strip_newlines | truncate: 160 }}
{% else %}
	{{ site.description }}
{% endif %}
```
{% endraw %}

### Complete Code
{% raw %}
```
<!-- Twitter Card -->
<meta property="twitter:card" content="summary">
<meta name="twitter:title" content="{{ page.title }}">
<meta name="twitter:url" content="{{ site.url }}{{ page.url }}">
<meta name="twitter:description" content="{% if page.excerpt %}{{ page.excerpt | strip_html | strip_newlines | truncate: 160 }}{% else %}{{ site.description }}{% endif %}">
<meta property="twitter:site" content="{{ site.twitter_username }}">
<meta property="twitter:image" content="{{ site.url }}{{ site.photo_embed }}">

<!-- Open Graph -->
<meta property="og:type" content="article">
<meta property="og:title" content="{{ page.title }}">
<meta property="og:url" content="{{ site.url }}{{ page.url }}">
<meta property="og:description" content="{% if page.excerpt %}{{ page.excerpt | strip_html | strip_newlines | truncate: 160 }}{% else %}{{ site.description }}{% endif %}">
<meta property="og:image" content="{{ site.url }}{{ site.photo_embed }}">
```
{% endraw %}

If you want to make sure your Twitter Card and Open Graph display correctly without posting and deleting, [check here for Twitter](https://cards-dev.twitter.com/validator) and [check here for Open Graph](https://developers.facebook.com/tools/debug/)