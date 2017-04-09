---
layout: post
title: "Installing Fedora on MacBook"
date: 2017-04-09 17:03:02 +0530
comments: true
tags: fedora Mac
description: Installing Fedora on Macbook
categories: Linux
---

Recently, I've been using MacBook Air along with its default OS [macOS Sierra](https://www.apple.com/in/macos/sierra/) for about a year.
I decided to switch back to [Fedora](https://getfedora.org/) once I started noticing the decreasing customizability after every update.
Also there were a lot of API level changes that somehow always ended up breaking my workflow.<!-- more -->

The following are the steps with which I got Fedora completely working on my machine.

### Prerequisites

- Get [Fedora Media Writer](https://getfedora.org/fmw/FedoraMediaWriter-osx-4.0.8.dmg) and [Fedora Workstation](https://download.fedoraproject.org/pub/fedora/linux/releases/25/Workstation/x86_64/iso/Fedora-Workstation-Live-x86_64-25-1.3.iso) and install the disk image onto a USB

Alternatively, you can use `dd` utility to do the same without the Fedora Media Writer by doing
```bash

    diskutil list # get the disk name from the output which is something like /dev/disk1
    diskutil unmountDisk /dev/disk1
    sudo dd if=/Users/umar/Downloads/Fedora-Workstation.iso of=/dev/rdisk1 bs=512k # notice the prepended r in the disk name
    diskutil unmountDisk /dev/disk1
```
- Create a partition using DiskUtility
Mac Hardrive > Partition > + >  Name= Fedora, Size = 30~50 GB

Keep in mind, since Mac will only allow a single more partition to be added, keep the partition size as high as possible if you're going to use fedora as your primary OS.

Click on Apply and Confirm to get a new partition.

### Installation

- Insert the USB and reboot the system while pressing the opt/alt key

Select the USB disk and Select Start fedora live.

The following screens should be fairly simple

- For the installation destination select the main hard-drive and select "I would like to make additional space available".

Select the Fedora Disk partition click "Delete" and then on "Reclaim space" this will automatically reclaim the space and create space for Fedora.

- Proceed with installation along with creating a user with password and root password.


### Post-Installation

- Get the Wi-Fi working by [installing the broadcom drivers](https://gist.github.com/jamespamplin/7a803fd5be61d4f93e0c5dcdea3f99ee)
  (You'll need to connect to internet via bluetooth/USB tethering, which thankfully work).

- Update fedora by running `sudo dnf update`

- Fix the camera by installing the reverse-engineered [FaceTime HD drivers](https://github.com/patjak/bcwc_pcie) by running the following

```bash

cd /usr/src
wget https://github.com/patjak/bcwc_pcie/archive/master.zip
unzip master.zip
mv bcwc_pcie-master bcwc_pcie
cd /usr/src/bcwc_pcie/firmware
make
sudo make install
cd /usr/src/bcwc_pcie/
make clean
make
sudo make install
sudo depmod
sudo modprobe facetimehd

```
Check it by running [Cheese](https://wiki.gnome.org/Apps/Cheese).


- Run the following commands to fix the keyboard bugs
```bash
xmodmap -e "keycode  94 = grave asciitilde"
xset r rate 200 38 # Increase keyboard repeat rate
```
You can optionally switch control and CapsLock and make Return act like control when long-pressed by installing [xcape](https://github.com/alols/xcape)
and running

```bash
setxkbmap -option ctrl:nocaps
xmodmap -e "remove Control = Control_R"
xmodmap -e "keycode 0x69 = Return"
xmodmap -e "keycode 0x24 = Control_R"
xmodmap -e "add Control = Control_R"
xcape -t 10000 -e "Control_R=Return"
```

- Install Gnome Tweak tool by `sudo dnf install gnome-tweak-tool`

Typing > Alt/Win behavior > Alt is Swapped with Win

- Install Gestures for trackpad by installing [libinput gestures](https://github.com/bulletmark/libinput-gestures)

- For battery optimizations install `powertop`

Create `/etc/systemd/system/powertop.service` with this content

```
[Unit]
Description=Powertop tunings

[Service]
Type=oneshot
ExecStart=/sbin/powertop --auto-tune

[Install]
WantedBy=multi-user.target
```
Followed by `sudo systemctl enable powertop.service`

- Mount the Mac Disk by `sudo mount -t "hfsplus" /dev/sda2 /media/mac`

You can get the name of the disk by the Disks program. To have write access to the mount partition

- Reboot into Mac (by holding the option/alt key)

- Running `diskutil disableJournal /Volumes/TheMacVolumeName`

- Reboot into Fedora

- Then `chown`, `chmod` all the files Recursively

Also, you can add it to the your [fstab](https://help.ubuntu.com/community/Fstab)

You can now enjoy your Fedora install and carry on to install some [other utilities on Fedora]({{ root_url }}/blog/2014/09/27/things-to-do-after-installing-fedora/).
