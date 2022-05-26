---
layout: post
title: "Planning A Homelab"
subtitle: "Always start wuth the requirements.."
date: 2022-05-26 10:45:13 -0400
background: '/img/posts/data-center.jpg'
permalink: /planning-a-homelab/
categories: [homelab,docker]
---
Given that I've enjoyed playing around with some basic docker containers recently, i'd like to rebuild my homelab from the ground up.

As with any good project, lets start with the requirements..

## What services do I want to run?

* Some kind of virtualisation server - Likely Proxmox
* At least 1 x Linux Server (likely Ubuntu) running as a VM
* Docker (thats a given)
* Yacht (to Manage Docker)
* Plex (or possibly try JellyFin)
* PiHole (because I hate adverts)
* A couple of [MineCraft servers](/deploy-minecraft-docker/) (via Docker)
* Uptime Kuma (because it looks cool and I'd like to monitor the stack)
* Home Assistant (I'm using this on a RPi at the moment)
* Some form of BitTorrent server (for ISO's naturally)
* Heimdall (as a home page / shortcut manager)

## What can I run it on?

I do have an old Dell Optiplex that would make an ideal host, but I'm thinking about using one (or both) of the Intel NUCs I have gathering dust.

One is a 5th Gen i5 with 16GB RAM and a 240GB SSD, and the other is a 5th Gen i3 with 8GB RAM and a 240GB SSD - the i5 would naturally be the primary with the i3 as the backup.

## Anything else?

The containers I'm planning on running shouldn't really tax the hardware, even if it is a little old, with the exception of Plex (or Jellyfin) for that matter. 

This gives me a little headroom for other Linux images, Windows installs etc that I want to play around with. 

Lets get the basics done and see where we end up :)