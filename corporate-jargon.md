---
layout: page
title: "The Corporate Jargonator"
description: A curated collection of amazing corporate sayings, buzzword and jargon - enough to make your toes curl..
background: '/img/generic/code-image.jpg'
permalink: /corporate-jargon/
---

## Welcome to the Jargonator

The rise of big business and the corporate world has had a significant effect on modern society. 

I'm not talking about rampant end-stage capatalism or environmental destruction - I'm talking about the rise of corporate jargon. I love the creativity of these buzzwords, but cringe at their application..

This is my personal, curated collection of only the finest corporate buzzwords - I'll be adding to the list over the coming months, so please check back for more amazing buzzwords..

{% for entry in site.data.jargonator %}
<hr>
<h4>{{ entry.jargon }}</h4>
<p>{{ entry.meaning }}</p>
{% endfor %}
