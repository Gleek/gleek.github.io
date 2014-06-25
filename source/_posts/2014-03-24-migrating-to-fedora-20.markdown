---
layout: post
title: "Migrating to Fedora 20"
date: 2014-03-24 20:32:50 +0530
comments: true
tags: fedora fedora-17 fedora-20 upgrading pre-upgrade customizing fed-up
description: Guide to upgrade to Fedora 20 from Fedora 17
categories: [Life, Linux]
---
<a href="http://fedoraproject.org/get-fedora"><img src="http://fedoraproject.org/w/uploads/5/54/Release-2.png" alt="Fedora 20" style=" display:block;margin:auto;"></a>

I've been a Fedora Fan-boy ever-since I started using it three years ago and Fedora 17 is the only Linux Based Distro which lasted for more than a year on my laptop. But just as every good thing has to come to an end, my company with Fedora 17 had completed it's lifetime. <!-- more -->

####Why did I stick with it ?####
To be honest, I was too scared to move on to a different O.S. because of the compatibility issues which my system has with Linux. To name the few:

- Extra media/function keys don't work</li>
- Battery Applet can't detect change in battery-charging status
- Linux goes into kernel-panic if connected with Bluetooth Mobile Internet ([DUN](http://en.wikipedia.org/wiki/Bluetooth_profile#Dial-up_Networking_Profile_.28DUN.29))
- ~~Wrong Resolution detected by X ~~(Bug Resolved after an update)
- Wi-fi cannot connect to Ad-Hoc network
- Wi-fi cannot create Hotspot
- and many more minor bugs.....

The problem is that every time I install a new linux distro I have to fight with some new even more puzzling bugs, and that is some tough battle to fight. So once I finally settled myself with Fedora 17, I never dared to move to some other O.S.
###Why did I upgrade ?###
Well, all things die with time and so did Fedora 17. Updates started depleting and new packages stalled. Considering these points and applaud for Fedora 20 helped me to move.
###How ?###
Once I decided to move on to Fedora 20 , I went researching about the methods and issues people had while upgrading fedora. Most of it was concerned with efi the new 'use only Windows' policy of the hardware vendors...but that wasn't the case with me. So I moved on.
I found many ways to upgrade to f20:

- Using [Fedup](http://fedoraproject.org/wiki/FedUp) (Recommended, but sadly not available for F17 :disappointed: )
- Using [yum](http://fedoraproject.org/wiki/Upgrading_Fedora_using_yum) (Highly unstable...not recommended)
- Using [pre-upgrade](https://fedoraproject.org/wiki/How_to_use_PreUpgrade)
- Installing with boot-media

The first two options were rejected instantly because of lack of support.
**Pre-Upgrade**: looked nice, but **even a fully-updated system didn't show any new releases of Fedora** in the Pre-Upgrade Window.
Since I was left with no choice, I adapted the old-school method of formatting the partition and re-installing everything...
Since I was too desperate to try F20 I didn't think of the consequences and went on with the method.

- I backed up my home folder
- Got the name of every package installed with `rpm  -qa --qf '%{NAME}\n'`


and when on to format the partition.
###The Dumb Review###
####What's awesome?####
The best thing about Fedora 20 is the new Gnome-Shell 3.10 with much more cleaner interface. The gnome apps are awesome, and lots of bugs have been fixed.
- The applications list is sorted out and grouped in a better manner.</li>
- I don't know how but all the applications which had problem running on previous versions of Fedora, such as Wine or Conky, worked fine now.</li>



####What's not so awesome####

- My old GTK+ and Gnome-Shell themes don't work anymore. I had to tweak every old thing a bit.</li>
- The top-bar is a bit too compact for me. I would have loved some more options such as my current connectivity status, etc.</li>
- It's still a tiring task to actually edit the application list. It would be better if there could be options to add applications to the list.</li>



####What Sucks?####

- **That damn Nautilus :**Nautilus is a big setback. They have disabled the backspace key and the search is now recursive. They have also disabled the Split-View. In short they have removed everything I loved about Nautilus.

I could find only one solution to fix all the problems - Degrade to the previous version.

**Note: You can fix the backspace feature [(Ask Ubuntu)](http://askubuntu.com/questions/289535/bring-back-backspace-keyboard-shortcuts-on-nautilus-and-thunar")**

I'm sure to find some more bugs as I move Along ,and this page will be updated :stuck_out_tongue:
