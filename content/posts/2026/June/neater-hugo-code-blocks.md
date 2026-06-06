+++
date = '2026-06-06T15:46:51+01:00'
draft = false
title = 'Neater Hugo Code Blocks'
categories = ["technology"]
+++

For the most part i'm happy with the styling of the Bear Blog theme. 

I'm a big fan of contraints and by picking a well featured but simply styled blog theme it means that I can focus on the content rather than constantly messing around with the look of the blog.

I do however have a gripe with the way that code blocks are presented.

By default, theres no text wrapping, so longer blocks of code spead themselves all over the page, looking very out of place and generally ruining the look of the blog.

Changing this to include text wapping is a fairly simple affair:

## 1. Duplicate style.html

By default, the CSS for the site is pulled from style.html in the partials directory of the Bear Blog theme. You can edit this directly, but those changes would be lost if the theme updates for any reason. 

A better way is to copy the stles.html file from:

**/themes/hugo-bearblog/layouts/partials/**

Create the following folders:

**/layouts/partials**

and then paste the style.html file to that directory.

This gives us a "local" copy of the file that superceeds the one in the theme, so any changes will persist should the theme update.

## 2. Modifing style.html

Open up **/layouts/partials/style.html**

Search for, and modify the "code" block of to include the "wrap-text" arguement:

---
    code {
        font-family: monospace;
        padding: 2px;
        border-radius: 3px;
        text-wrap: wrap;
      }
---

Any code block will now we text wrapped.