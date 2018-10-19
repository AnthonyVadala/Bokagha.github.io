---
title: Sticky Footer Using Flexbox
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

## The Power of CSS

I am sure all web developers have run into this problem at some point or another, wanting a footer to ***ALWAYS*** be at the bottom of the page. I certainly did while designing this blog. Luckily, I came across [Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout). 

Using Flexbox, footer positioning can be handled by only a few lines of CSS by using the [`flex`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex) and [`flex-shrink`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink) properties.

<!--more-->

<script async src="//jsfiddle.net/AnthonyVadala/ufkht0jn/embed/html,css,result/"></script>

## Browser Support

| Browser           | Version       |
| :-------------    | -------------:|
| Google Chrome     | 29.0          |
| Firefox           | 22.0          |
| Internet Explorer | 11.0          |
| Safari            | 10.0          |
| Opera             | 48.0          |