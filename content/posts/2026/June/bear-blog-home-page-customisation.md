+++
date = '2026-06-06T15:08:17+01:00'
draft = false
title = 'Bear Blog Home Page Customisation'
categories = ["technology"]
+++

# Bear Blog Home Page Customisation

I want to be able to add some customision to the stadard Hugo Bear Blog home page, specifically adding in some header text and a break down of blog posts made in certain categories.

To add in this type of customisation, we need to 

## Adding header text to the home page

In order to add in some header text to the home page, we need to create a _index.md file in the root of the content directory, within this file you can add in the text you want, along with any approprite front matter, for example:

---
```
+++
title = "Home"
+++

Welcome to my site.
```

This will then render at the top of the home page.

## Adding posts per category

In the example below, the fuction looks for the first 5 posts with the "technology" category in the "posts" folder, then applies some formatting before displaying the date and then the link to the post.

---

    {{ define "main" }}
      {{ .Content }}

      <h3>Technology</h3>
      <ul class="blog-posts">
        {{ range first 5 (where (where site.RegularPages "Section" "posts") "Params.categories" "intersect" (slice "technology")) }}
        <li>
            <span>
              <i>
                <time datetime="{{ .Date.Format "2006-01-02" }}">{{ .Date.Format "02 Jan 2006" }}</time>
              </i>
            </span>
            <a href="{{ .RelPermalink }}">{{ .Title }}</a>
          </li>
        {{ end }}
      </ul>
      </ul>

    {{ end }}
---

Multiple categories can be added in the same way by stacking these in the required order.

To implement this, create an index.html file in the layouts/ folder, when saved it should render as required.

