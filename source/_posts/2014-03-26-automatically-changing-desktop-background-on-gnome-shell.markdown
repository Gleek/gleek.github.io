---
layout: post
title: "Automatically Changing desktop background on gnome-shell"
date: 2014-03-26 17:53:27 +0530
comments: true
tags: automatic background shell-script command cron fedora gnome-shell linux opensuse ubuntu wallpaper
description: Guide and Shell Script to automatically change desktop background
categories: Linux
---
*Click [here](https://github.com/Gleek/gnome_wall_changer/archive/master.zip "gnome_wall_change.zip(Github)") to download the scripts directly, or view them on [Github](https://github.com/Gleek/gnome_wall_changer)*
<img src="https://lh3.googleusercontent.com/NGCDBc6q7d4KsJ5OQft2nhe0RnglzsBVbgOGZpdEMunjopdwxg5CmzMbgYA-7GpkHX3P5xVFOOR2k300r3smFScPSX-xWsaBOmHuJL5r24OstQDIuqFbsUZ0pxwjcCoV0jQvD2azdKkCWwX7IB4wB78M8_xlW6wb4fLTn26uHzSHltTAtuapfJE5pMvzuPAMb5Af0A2I8bn-6KvjoVazUT_qMhBFcIqBLT_OjSKK8f04sDbVarExlNA5cvxwujLgNLFKrLneYNkXBV72g_8AiY3Sj20vEOG-Nqbt4FY0sxBavgWuE62bfngKaWpcIuEdlgJDzXVb0hLsO_XHulyWKZqsEnZmPTpeZTXbgwXOW831bU7FU9zWamsCxDAyQJP9361V-xqMIut-5jnT2g86ESIks1xVZxkO83RClmKiwmM3b1rq9hZuMR9DVuVFjDBdQcvVBIEWyKPAIi39-26AkblTir_AXZcEeAju_dNamBiyQuZ6-Pf_wykzTNZlXt1aR8LzoIYABCc5CrZxrft4rnj2U7M3_v4-SVmzq3bqqV5OKIONgZkMHpAZxTnGEzToNThcyxZt1Q_lr050p-a8opmObnudB6UElg2x_MdrztotI6Dpsjs6TiHIdLWfur4Zh92uvsedkmV1zY5TKazLMTttGY2yMkVY3YpVAy64gQ=s370" style=" display:block;margin:auto;" width="370"/>

One of the main attractions about a system is the desktop background. We tend to choose our background which identifies our interests , are aesthetically pleasing or remind us of our good times.

But the thing with consistency is that it gets boring with time. Wallpapers we once loved, becomes a burden and we find it hard to come back to that wallpaper after getting it on 24×7.
<!-- more -->
This is the problem I had. I cancelled out each wallpaper from my list of all wallpapers I had, after I completely sucked out the goodness of a wallpaper with my eyes.

I came up with the idea of automatically changing the wallpaper randomly via some sort of shell script. It's implementation used <code>gsettings</code> to change the desktop wallpaper. It was supposed to run automatically as a cron-job but I couldn't make the cron work. The current implementation uses <code>sleep</code> to get the delay

So a simple wall paper changing script looked like:

```bash

#!/bin/bash
image_path=$1
#Setting up a path for local storage

if [ ! -d "$image_path" ]; then
  echo "Path doesn't exist (Pass absolute path as parameter)" 1>&2
  exit
fi
local_dir="/home/$(whoami)/.local/wall_change"
#creating local directory
mkdir -p $local_dir
#getting name of the picture
pic=$(find $image_path -regextype posix-extended -regex "(.*\.jpg)|(.*\.png)"|shuf -n1)
echo $pic

#Storing image in local_dir
filename=$(basename "$pic")
extension=".${filename##*.}"
local_wallpaper=$local_dir/mywallpaper$extension
#setting the wallpaper
cp "$pic" $local_wallpaper
#echo $local_wallpaper
#Adding bogus wallpaper (don't know if this is a gsettings bug or i'm doing some basic flaw)
gsettings set org.gnome.desktop.background picture-uri file:/$local_wallpaper
#try increasing the sleep if wallpaper doesn't change
sleep 1;
gsettings set org.gnome.desktop.background picture-uri file://$local_wallpaper

```

**You can find the rest of the files on [Github](https://github.com/Gleek/gnome_wall_changer/)**

Have fun with your wallpapers :wink:
