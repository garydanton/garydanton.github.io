---
layout: post
title: "Deploy a Minecraft server with Docker"
subtitle: "more gameplay, less config"
date: 2022-05-22 10:45:13 -0400
background: '/img/posts/minecraft-header.jpg'
permalink: /deploy-minecraft-docker/
categories: [docker]
---

Here are some project notes/basic instructions etc, to spin up a very beginner friendly Minecraft server using Docker. 

This may spin up into a proper "how-to" once i've perfected the process.

**Docker Source:**

Source [itzg/docker-minecraft-server](https://github.com/itzg/docker-minecraft-server) on Github.

**docker-compose.yml contents:**

``` docker
version: "3"

services:
  mc:
    image: itzg/minecraft-server
    ports:
      - 25565:25565
    environment:
      EULA: "TRUE"
    tty: true
    stdin_open: true
```
**Post deploy config:**

Jump into the CLI and within the server.properties file edit the following:

```
gamemode=survival
spawn-monsters=false
difficulty=peaceful
```

The container will need a restart after modifing server.properties

**Things still to do:**

1. Make volumes persistant
2. Migrate to a dedicated docker host (rathen that Docker desktop on my main machine)