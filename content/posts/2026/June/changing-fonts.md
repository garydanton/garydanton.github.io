+++
date = '2026-06-06T17:53:38+01:00'
draft = false
title = 'Changing Fonts in Hugo'
categories = ["technology"]
+++

Another tweak I've made to the base Hugo Bear Blog theme is to swap out the default font (Verdana - i've never much cared for it) with some alternatives, in my case Ubuntu for headers and Lucidia Console for body text.

It's a very quick change and just involves editing the style.html file created we [editing the code-block defaults](/posts/2026/june/neater-hugo-code-blocks/)

Right at the top of the style.html file you need to edit the following:

___
```
:root {
    --width: 720px;
    --font-main: Verdana, sans-serif;
    --font-secondary: Verdana, sans-serif;
```
___
to:
___
```
:root {
    --width: 720px;
    --font-main: Ubuntu, sans-serif;
    --font-secondary: "Lucida Console", monospace;
```
___

Save, upload and you are good to go.