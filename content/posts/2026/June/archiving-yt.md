+++
date = '2026-06-12T11:43:37+01:00'
draft = false
title = 'Archiving YouTube'
categories = ["technology"]
+++


> "There are two types of people in the world, those that have lost data.. and those that will.."

A number of years ago I experienced the inevitable, a failed hard drive. For the most part it wasn't too much of an issue - ISOs, some music that I could re-rip from CDs, but I did lose some older media.

I now need to download some of that for an offline copy, so I needed a very quick and dirty bash script to grab a copy to store locally.

With the assistance of some AI, I've now got the following:

## The Script

Save this as youtube-download.sh

---
```
#!/usr/bin/env bash
set -euo pipefail

if [ "$#" -lt 2 ]; then
  echo "Usage: $0 <youtube-url> <download-directory>"
  exit 1
fi

URL="$1"
DEST="$2"

mkdir -p "$DEST"

yt-dlp \
  -f "bestvideo+bestaudio/best" \
  --merge-output-format mp4 \
  -P "$DEST" \
  -o "%(title)s [%(id)s].%(ext)s" \
  "$URL"
```
---
This tells yt-dlp to fetch the best separate video and audio streams when available, fall back to the best single file if needed, merge the result, and save it into the directory you pass in.

In order to actually use it, I need to make it executable:

---
```
chmod +x youtube-download.sh
```
---

Then it can be run like the following example:

---
```
./youtube-download.sh "https://www.youtube.com/watch?v=VIDEO_ID" "/Users/Downloads/YouTube"
```
---

## Prerequisites:

There may be a requirement for both yt-dlp and ffmpeg to be installed. This can be done on a Mac using the following:

---
```
brew install yt-dlp ffmpeg
```
---