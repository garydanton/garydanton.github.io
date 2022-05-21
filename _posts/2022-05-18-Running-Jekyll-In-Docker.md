---
layout: post
title: "Running Jekyll in Docker"
subtitle: "or 'How to avoid wasting a couple of hours on an internet deep-dive'"
date: 2022-05-18 10:45:13 -0400
background: '/img/generic/code-image.jpg'
permalink: /running-jekyll-in-docker/
categories: [docker,jekyll]
---

Since I've been playing around with Jekyll I've spent hours messing around on both Mac and Windows trying to get Ruby installed so I can run Jekyll natively from within the terminal in VSCode - ultimately with the aim of running a basic web server on my laptop..

## Enter Docker..

Rather than mess around with installing homebrew, Ruby and any number of dependencies, I found the following repo on github -- with a prebuilt Jekyll server with all the added extras already installed and pre-configured.. Go Internet!

The instructions are very simple and straightforward:

1. Install Docker Desktop from [The official Docker website](https://www.docker.com/products/docker-desktop/).
2. Create a docker-compose.yml in the root of your Jekyll site and copy the following code into it..
3. Launch the terminal and run docker-compose up
4. Point your browser to [http://localhost:4000](http://localhost:4000) and check out your website

**docker-compose.yml contents:**

``` docker
services:
  jekyll:
    image: bretfisher/jekyll-serve
    volumes:
      - .:/site
    ports:
      - '4000:4000'
```
The docker image is built to scan and auto update files each time they are saved, allowing you to speed up your workflow.

The usual caveats apply, so if you edit your _config.yml file then you'll need to exit the container with a CTRL-C and re-run docker-compose up to reload.

---
**Credits:**

1. Jekyll Docker Server by BretFisher on [Github](https://github.com/BretFisher/jekyll-serve)
2. Header image by [Luis Gomes](https://www.pexels.com/@luis-gomes-166706/) on [Pexels](https://www.pexels.com/photo/close-up-photo-of-programming-of-codes-546819/)
