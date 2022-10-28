---
layout: post
title: "Build A Wordpress Test Site In 90 Seconds"
subtitle: "A no-faff setup with docker-compose"
date: 2022-10-27 10:45:13 -0400
background: 'img/posts/wordpress-development.jpg'
permalink: /wordpress-docker-compose/
categories: [docker]
---

I've built a number of websites over the years for projects, both paid and personal and nearly all of them have been developed on the Wordpress platform.

In order to build these sites, i'm often working on them well before a domain name or hosting package has been arranged, especially if its just at a "wireframe" or "proof of concept" stage and you need to show something to a client.. 

I'n order to keep a development environement running for this purpose, i've tried many things over the years, including:

* Maintained a test / dev worpress install on a webhost
* Used (and hated) MAMP to host a dev site locally
* Built VM's specifically to host worpress

These all take time and effort, but every now and then I want to be able to spin a wordpress site up to test a theme, a plug in or simply and idea, but without the faff of building something first.

## Enter Docker

Over on [Docker Hub](https://hub.docker.com/_/wordpress) there's a [Wordpress](https://wordpress.com/) container that's pretty much ready to go - simply load the following into docker-compose and it'll download and spin up in about 90 seconds (depending on your network connection)

## Config

I've spun up a couple of sites using the details below (simple DB names and passwords are a *serious* no-no in production, but fine for my testing) and they've all worked well, just change the ports to something different for each extra site you want to run otherwise they'll run into issues.

**docker-compose.yml contents:**

``` docker
version: '3.1'

services:

  wordpress:
    image: wordpress
    restart: always
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: exampleuser
      WORDPRESS_DB_PASSWORD: examplepass
      WORDPRESS_DB_NAME: exampledb
    volumes:
      - wordpress:/var/www/html

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_DATABASE: exampledb
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
      MYSQL_RANDOM_ROOT_PASSWORD: '1'
    volumes:
      - db:/var/lib/mysql

volumes:
  wordpress:
  db:
```
Run this using docker-compose up and you are good to go.

Just navigate to http://localhost:8000 (or whatever your port is) and you can get yourself setup in minutes.