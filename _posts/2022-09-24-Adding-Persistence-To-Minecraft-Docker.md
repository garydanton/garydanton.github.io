---
layout: post
title: "Adding Persistence to a MineCraft Docker Container"
subtitle: "Backups.. here we come.."
date: 2022-09-24 10:45:13 -0400
background: '/img/posts/minecraft-header-2.jpg'
permalink: /minecraft-docker-persistence/
categories: [docker]
---

As mentioned in my earlier post - [Deploy a Minecraft server with Docker](/deploy-minecraft-docker/), I'd originally not created it with persistence in mind, this was fine until my intall of docker desktop developed an issue and I needed to nuke it - say goodbye MineCraft server.. 

At this point I revisted adding a persistent volume for the Minecraft Data folder to avoid issues like this in the future and make sure that all future servers can be backed up easily.

**Docker Source:**

As before, my source is still [itzg/docker-minecraft-server](https://github.com/itzg/docker-minecraft-server) on Github. However my docker-compose.yaml has been updated to include:

``` docker
    volumes:
      - ./minecraft-data:/data
```
Resulting in the following new docker compose file..

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
    restart: unless-stopped
    volumes:
      - ./minecraft-data:/data
```
**Post deploy config:**

Below is my standard, default server.properties file. To use, create the file in /minecraft-data on your local filesystem before you run "docker-compose up"

Note:

See entries for "level-seed" and "motd" - replace the values listed below with your own.

```
#Minecraft server properties
#Thu Aug 25 21:12:22 UTC 2022
enable-jmx-monitoring=false
level-seed=*Insert your seed here, or leave blank for a random one*
rcon.port=25575
enable-command-block=true
gamemode=survival
enable-query=false
generator-settings={}
enforce-secure-profile=false
level-name=MinecraftServer
motd=*Insert your MOTD here*
query.port=25565
texture-pack=
pvp=true
generate-structures=true
max-chained-neighbor-updates=1000000
difficulty=peaceful
network-compression-threshold=256
max-tick-time=60000
require-resource-pack=false
max-players=10
use-native-transport=true
online-mode=true
enable-status=true
allow-flight=false
broadcast-rcon-to-ops=true
view-distance=10
max-build-height=256
server-ip=
resource-pack-prompt=
allow-nether=true
server-port=25565
enable-rcon=true
sync-chunk-writes=true
op-permission-level=4
prevent-proxy-connections=false
hide-online-players=false
resource-pack=
entity-broadcast-range-percentage=100
simulation-distance=10
player-idle-timeout=0
rcon.password=minecraft
force-gamemode=false
rate-limit=0
hardcore=false
white-list=false
broadcast-console-to-ops=true
spawn-npcs=true
previews-chat=false
spawn-animals=true
snooper-enabled=true
function-permission-level=4
level-type=default
text-filtering-config=
spawn-monsters=false
enforce-whitelist=false
resource-pack-sha1=
spawn-protection=16
max-world-size=29999984

```

**Things still to do:**

1. Migrate to a dedicated docker host (rather that Docker desktop on my main machine)