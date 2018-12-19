---
title: Full-screen iframe with a Height of 100%
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

## Introduction
Sometimes I write small PHP web applications that are used on an internal web portal. The problem with the web portal is that it does not support inline PHP, but it does support inline JS and HTML. Using a bit of JS and a HTML iframe I display these web applications and make them appear to be a part of the web portal itself!

**Note: This will only work on if the URL in the iframe matches the same domain as the host page it is embedded on.**

## Getting 100% iframe Height
The big part of having the iframe integrate seamlessly into the portal is to have the height of it match the height PHP web application, that way I don't need to scroll inside the iframe to view everything.

To calculate the height the iframe should be, I use a bit of JS with a function called calcHeight. This function will calculate the height in pixels the iframe needs to be.

JS
```
function calcHeight(iframeElement) {
  var the_height = iframeElement.contentWindow.document.body.scrollHeight;
  iframeElement.height = the_height;
}
```

In order to call the function calcHeight, I need to add an inline event. This event will occur every time something is loaded in the iframe and looks like this: `onLoad="calcHeight(this);"` inside the iframe.

I also remove the ability to scroll, since the iframe will be full height anyways using `scrolling="no"`.

HTML
```
<iframe src="https://YOURDOMAIN" onLoad="calcHeight(this); 
frameborder="0" scrolling="no" id="the_iframe" width="100%">
  <p>Your browser does not support iframes.</p>
</iframe>
```

**Note: Replace `https://YOURDOMAIN` with the URL you want to be iframed.**
<!--more-->

## (Optional) Scroll iframe and Page to Top
I like to have both the content inside the iframe and the host page to be scrolled to the top every time something is loaded inside the iframe. I do this by having this additional part to the onLoad event: `window.parent.parent.scrollTo(0,0);`

## Complete Code

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <script>
      function calcHeight(iframeElement) {
        var the_height = iframeElement.contentWindow.document.body.scrollHeight;
        iframeElement.height = the_height;
      }
    </script>
  </head>
  <body>
    <iframe src="https://anthonyvadala.me/" onLoad="calcHeight(this); window.parent.parent.scrollTo(0,0);" frameborder="0" scrolling="no" id="the_iframe" width="100%">
        <p>Your browser does not support iframes.</p>
    </iframe>
  </body>
</html>
```

## Live Example

<script>
function calcHeight(iframeElement) {
  var the_height = iframeElement.contentWindow.document.body.scrollHeight;
  iframeElement.height = the_height;
}</script>

<iframe src="https://anthonyvadala.me/" onLoad="calcHeight(this); window.parent.parent.scrollTo(0,0);" frameborder="0" scrolling="no" id="the_iframe" width="100%">
  <p>Your browser does not support iframes.</p>
</iframe>