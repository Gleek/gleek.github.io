---
layout: post
title: "Things to do after installing Fedora"
date: 2014-09-27 18:34:37 +0530
comments: true
tags: linux fedora fedy gnome firefox extensions tweak
description: Installing proprietary packages quickly after installing fedora 20
categories: Linux
---
 <img style=" display:block;margin:auto;height:240px" src="http://sd.keepcalm-o-matic.co.uk/i/keep-calm-and-yum-install.png"   alt="Keep Calm and yum install" /><br>
Getting the right packages after a fresh install is a headache. That is exactly what I had when I had to do a fresh installation of my Fedora after I accidentally corrupted my entire disk :frowning:.

I didn't want to spend days installing the packages this time. This time I wanted to do it smart and quick.

The problem here was that I couldn't just `yum install` everything, that's because Fedora community adheres to free software principles and doesn’t offer non-free codecs and drivers from it’s repositories. But there are 3rd party repositories which allow Fedora users to get non-free components.
<!--more-->

Here is a list of few things you should do after a fresh install of Fedora 20:
<a name="fedy"></a>
###Installing Fedy

 >Fedy lets you install multimedia codecs and additional software that Fedora doesn't want to ship, like mp3 support, Adobe Flash, Oracle Java etc., and much more with just a few clicks.

Install it via
```bash
su -c "curl https://satya164.github.io/fedy/fedy-installer -o fedy-installer && chmod +x fedy-installer && ./fedy-installer"
```
You can download any of the packages from this point onwards but I feel some of them are essential:

- Tweaks and Task
  - Install Adobe Flash
  - Set SELinux to permissive mode
  - Configure sudo for current user
  - Install multimedia codecs
  - Configure RPM Fusion repositories
- Additional Software
  - Google Talk Plugin

<a name="template"></a>

###Creating a Template File
Template file is a file in the `Templates` folder of the home directory. Files added here will appear in the *New Documents Menu*.
Do it via typing this in the terminal

```bash
touch ~/Templates/Empty\ File
```

You can add other types of files in the templates folder and add some default content to it.

For example you can add a `new.c` file there and write various header files, you usually use, in it.
This would **save the hassle of writing it yourself everytime you create a new 'c' file.

<a name="yumex"></a>
###Installing Yumex
I personally don't like the new Software manager in Fedora. It has nice UI but often takes a lot of time in loading packages and installing them.
Yumex (Yum Extender) on the other hand is a graphical package management tool** which utilizes the power of yum and makes it a bit 'user-friendly'.
I also feel it's much more easy to use and is a bit more transparent in it's functionality than the former manager

```bash
sudo yum install yumex
```

You might update your full system after this, as yumex will prompt you for that on it's start.

From this point onward you can simply search for a package inside yumex, instead of googling the exact package name to be used with `yum install`.
<a name="gnometweak"></a>
###Gnome-Tweak Tool
This is one of my favorite tools for Gnome Shell. This helps to customize Gnome 3 very easily. It also provides an easy way to install extensions and enable themes
Few of the extensions that I've are:

- [User Themes](https://extensions.gnome.org/extension/19/user-themes/) - Load Shell Themes from user directory
- [Media Player Indicator](https://extensions.gnome.org/extension/55/media-player-indicator/) - Control Media Players from the Top Bar 
- [Impatience](https://extensions.gnome.org/extension/277/impatience/)- Speed up the animation speed of Gnome-Shell
- [Drop Down Terminal](https://extensions.gnome.org/extension/442/drop-down-terminal/) - A Handy utility to quickly jump to terminal and mininmize it with just a single button
- [Dash To Dock](https://extensions.gnome.org/extension/307/dash-to-dock/) - Makes the dash bar act as a dock
- [Shell Shape](https://extensions.gnome.org/extension/294/shellshape/) - A tilling window extension
- [Show Desktop From Overview](https://extensions.gnome.org/extension/496/show-desktop-from-overview/) - Show desktop on clicking on empty space in overview
- [Calculator](https://extensions.gnome.org/extension/111/calculator/) - A simple calculator in search overview
- [Flash FullScreen Fix](https://extensions.gnome.org/extension/851/flash-fullscreen-fix/) - Fixes the bug encountered while making flash videos full screen

You can find more extensions on the [official page](https://extensions.gnome.org/).

Some of my other settings include enabling *Icons on Desktop* and reducing the *Scaling Factor* to 0.9. I also use [Droid Sans](http://www.fontsquirrel.com/fonts/droid-sans), [Roboto](http://www.fontsquirrel.com/fonts/roboto) and [Consolas](http://www.microsoft.com/typography/fonts/font.aspx?FMID=1924) as my primary fonts.

There is another tool called `dconf editor` which is basically a GUI version of the `gsettings` tool.
It also provides some customizations of gnome shell and other applications.

<a name="bleachbit"></a>
###Installing Bleach Bit and Ailurus
After a while a system starts getting cluttered via junk files and caches. Bleach Bit does the task of remove this clutter and useless files easily with a single click of a button. It can be Installed with

```
sudo yum install bleachbit
```

Ailurus is a tool to install new Softwares and provide clean-up of caches. It also helps to tweak firefox and RPM Recovery. It can be installed via

```
sudo yum install ailurus
```
<a name="firefoxext"></a>
###Getting Firefox Extensions
There are some extensions which are vital for a firefox user. Some of them are:

- [Adblock Plus](https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/) - Blocks annoying advertisements
- [Ghostery](https://addons.mozilla.org/en-US/firefox/addon/ghostery/) - Blocks various tracking applications, widgets and social media buttons which might track you
- [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/) - An awesome extension to run custom user scripts for various tasks
- [HTitle](https://addons.mozilla.org/en-US/firefox/addon/htitle/)- Removes the useless title bar, thus increasing screen space.
- [Omnibar](https://addons.mozilla.org/en-US/firefox/addon/omnibar/) and [OmnibarPlus](https://addons.mozilla.org/en-US/firefox/addon/omnibar-plus/) - Unites the Address Bar and search bar to provide a single Bar for search as well for opening websites
- [The Addon Bar](https://addons.mozilla.org/en-US/firefox/addon/the-addon-bar/)  - A toolbar which bring back the Addon Bar, listing all the addons for easy access.
- [DownloadThemAll](https://addons.mozilla.org/en-US/firefox/addon/downthemall/) - A download accelarator inside firefox.
- [Vimperator](https://addons.mozilla.org/en-US/firefox/addon/vimperator/) or [Pentadactyl](https://addons.mozilla.org/en-US/firefox/addon/pentadactyl/) - Completely transforms firefox to behave similarly to Vim Editor. This makes working completely mouseless and also gives a clean UI. If you are a **Emacs** users you might find these [.vimperatorrc](https://gist.githubusercontent.com/avendael/7028513/raw/40abf0e8bfb7d4fc72bd224f8c6c4694a1e33456/.vimperatorrc) or the [.pentadactylrc](http://www.jnanam.net/pentadactylemacs/.pentadactylrc) files useful.

These settings will provide a system which is good enough for daily use. You might want to install some other applications depending on your use. Some of the other applications include [GIMP](http://www.gimp.org/), [Emacs](http://www.gnu.org/software/emacs/), [VLC Media Player](http://www.videolan.org/vlc/index.html), [Virtual Box](https://www.virtualbox.org/), [GParted](http://gparted.org/), [Wine](https://www.winehq.org/), [DosBox](http://www.dosbox.com/), etc. to name a few. You can find all the packages by searching for them in [yumex](#yumex)
