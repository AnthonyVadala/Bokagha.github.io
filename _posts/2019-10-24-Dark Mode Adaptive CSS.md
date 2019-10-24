---
title: Adaptive CSS Dark Mode
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

## Introduction
If you have been using the internet in the past year or so, you may have noticed many websites and even desktop and mobile operating systems now have a toggle or even automatic dark modes. In the past this required some creative use of JavaScript or other means to automatically switch the color scheme or require input from the user to toggle between these modes. 

With the new `prefers-color-scheme` CSS media feature, the browser itself can detect the user's browser and operating system preferences and automatically toggle between different color schemes depending on the preference (light mode or dark mode).

<!--more-->

## How to Use
The way I prefer to use `prefers-color-scheme` is to write the CSS for a website for what the user will see by default first. This does not require `prefers-color-scheme`. Once written, at **THE END** of the `.css` file I use either of the following:

**Dark Mode**
```
@media (prefers-color-scheme: dark) {
  ...
  CSS For Dark Mode Here
  ...
}
```

**Light Mode**
```
@media (prefers-color-scheme: light) {
  ...
  CSS Light Mode Here
  ...
}
```

The one you use depends on the color scheme of the original CSS, if the default is written for dark mode, use `@media (prefers-color-scheme: light)` at the end of the file and vice versa.

Since CSS is executed in the order it is written, the website will load all the original CSS for layout and default color scheme, then depending on user preference either stay on the default color scheme or change to the alternative using `prefers-color-scheme`.

### Live Example
In this example the default color scheme is written for dark mode, which is white text with a black background. If the operating system or browser is using a light theme/mode it will appear as black text with a white background.

<script async src="//jsfiddle.net/AnthonyVadala/2em8d69f/embed/html,css,result/"></script>


## Browser Support

| Browser           | Version       |
| :-------------    | -------------:|
| Google Chrome     | 76.0          |
| Firefox           | 67.0          |
| Internet Explorer | N/A           |
| Safari            | 12.1          |
| Opera             | N/A           |