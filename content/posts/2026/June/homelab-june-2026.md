+++
date = '2026-06-11T19:24:30+01:00'
draft = false
title = 'Homelab Update - June 2026'
categories = ["technology"]
+++

I've been messing about over the last 6 months with my homelab, and it’s gone through several different setups, with some far more successful than others.

The main purpose of the homelab is media processing and consumption. I'd like to start to migrate away from streaming services, so I need to self-host alternatives.

As of June 2026, my homelab currently consists of the following:

- Raspberry Pi 4B
- Lenovo ThinkCentre M720q Tiny
- Dell Optiplex 3050
- Synology NAS

## Raspberry Pi 4B

This little gem of a computer has been running [Pi-hole](https://pi-hole.net/) for years now. It’s the only device that’s always on, happily blocking ads for my whole home network.

## Lenovo ThinkCentre M720q Tiny

Before I picked up the Optiplex, the little Lenovo was my primary homelab device. It’s been rebuilt multiple times, initially using Proxmox, but I’ve recently switched to Ubuntu Server and Docker.

It’s currently running the following containers:

- Dockge (for container management)
- Uptime Kuma (for checking system uptimes)
- ARM (Automated Ripping Machine)
- Minecraft server

The ThinkCentre is an absolutely tiny computer, but this does have its drawbacks. It does run a little warm, and the fan readily spins up and can be a little whiny at higher speeds, which, when configured as a media server, is noticeable.

I’ve added an external DVD drive in order to use ARM ([Automated Ripping Machine](https://github.com/automatic-ripping-machine)) — I’ve got a stack of old DVDs and CDs, and this takes 95% of the effort out of ripping and digitising my media collection.

## Dell Optiplex 3050

This very cheap Dell Optiplex rocks a 7th Gen i5, 16GB RAM, a 240GB SSD for a boot drive, and a 4TB spinning storage drive. I also have a very old and basic Nvidia 1050 Ti installed for transcoding a few Jellyfin streams.

It’s currently used exclusively as a media server running [Jellyfin](https://jellyfin.org/), and it works well for such a cheap solution. It’s also running Ubuntu Server with the latest NVIDIA drivers.

## Synology NAS

I’ve had this Synology NAS for years, and it was my original media server solution. It’s capable of running Jellyfin, but it really does struggle with more modern file types, and transcoding is pretty much a no. Since setting up the Optiplex, it’s been demoted to a secondary file store.

## What’s next for the homelab?

I’m likely to migrate everything over from the Lenovo to the Dell. While the Lenovo is a capable machine, it can be noisy and lacks internal storage — it’s a computer built on compromise.

I’d also like to add a Samba server to the Optiplex, as at the moment media transfer is done via rsync (this works fine, but I’d like a simple GUI-accessible method as well).

I’m also looking to expand the media capabilities of the setup, adding in a podcast and audiobook server, ebook server, and anything else I fancy playing around with.

I may end up repurposing the Lenovo for more of a testing setup, reinstalling Proxmox — but we’ll see.

That’s the beauty of a homelab: you can chop and change it as much as you like.