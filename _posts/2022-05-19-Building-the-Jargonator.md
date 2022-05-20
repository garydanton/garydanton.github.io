---
layout: post
title: "Building the Jargonator"
subtitle: "Using data sources in Jekyll"
date: 2022-05-19 10:45:13 -0400
background: '/img/posts/06.jpg'
permalink: /building-the-jargonator/
---

My "Jargonator" project was built in an hour or so as a way of working out how to handle data files to populate static webpages generated in Jekyll.

I extensively referenced the official [Jekyll documentation for data files](https://jekyllrb.com/docs/datafiles/) - if my explanation doesn't make any sense, those docs would be your best starting point. 

You can visit the complete Jargonator page [here](/corporate-jargon/).

## Build your data source

This is built as a standard CSV file made of multiple fields separated by a comma, with each entry on a new line.

```
jargon,meaning
Drill down,Investigate further (see Deep Dive)
Circle back,Return to an earlier conversation
Boil the ocean,Do the impossible
```

This was then saved in as a file called jargonator.csv in folder called _data in the root of my Jekyll project.

Once this is done, you then need to insert the appropriate code in your page. In my case I wanted the "jargon" part of the CSV to be a heading, followed by the "meaning" part as a standard paragraph - and everything to be separated by a horizonal rule, to keep things neat.

## Insert the code into the page

The next step is to write and insert the code calling the data fields into your web page:

```text
  { % for entry in site.data.jargonator %}
  < hr>
  < h4>{{ entry.jargon }}</h4>
  < p>{{ entry.meaning }}</p>
  { % endfor %}
```
*ignore the first space after the { or the < in the code block above, I'm stuggling to find the correct markdown to display as code and not render as html. This is my very quick and dirty workaround*

In this instance "entry in site.data.jargonator" steps through each line in the jargonator CSV file and for each displays the entry.jargon field in a heading tag, then each associated entry.meaning field in a paragraph tag.

This then generates the following output which can then be styled using CSS.

```{% for entry in site.data.examples.jargonator_example %}
<hr>
<h4>{{ entry.jargon }}</h4>
<p>{{ entry.meaning }}</p>
{% endfor %}```

Neat eh? Its a very powerful feature that can bring a lot of functionality to Jekyll pages. 