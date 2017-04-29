---
layout: post
title: "Editing remote code with Emacs"
date: 2017-04-11 22:56:54 +0530
comments: true
tags: emacs ssh tramp
description: Editing remote code with Emacs
categories: Emacs
---

Lately, I've been working on a code-base situated remotely on a server accessible over `ssh`.
The network latency and size of the code repository prompted me to reconsider the method
to edit such files. I discovered a few options I could use and finally settled with one of them.
<!-- more -->

### Option I : Running Emacs remotely.
This was the option I initially started with. Since most of the people who worked around me
used `vim`, remotely, this option came naturally to me.
Since, the remote machine was a Linux system, I [built Emacs](https://www.emacswiki.org/emacs/BuildingEmacs)
on the server and started using it.

Since most of my keyboard shortcuts, in Emacs, are some fancy combinations of <kbd>Ctrl</kbd>, <kbd>Meta</kbd> and character keys,
the terminal software I used, ate most of such shortcuts.
I tried resetting the terminal keybindings and changed some complex keybindings but in the end, I had to give up on that.

Changing my keybindings to make them a little saner for my terminal emulator, did not seem like an option.
Since, rewiring my brain to create new muscle memory built over 2 years was my last option.

### Option II: Using Tramp
Emacs has an inbuilt option to connect to remote hosts (via several protocols) called [Tramp](https://www.gnu.org/software/tramp/).
Initially it felt (a lot) easier than the 'running emacs remotely' option, but slowly
the problems with tramp started to appear.

Tramp was a bit sluggish when opening and saving files. There were some optimizations that could be done
with tramp settings

```scheme
(setq tramp-auto-save-directory "~/tmp/tramp/")
(setq tramp-chunksize 2000)
```
and some ssh settings.
```
Host *
      ControlMaster auto
      ControlPath ~/tmp/.ssh-control-%r-%h-%p

```
Even though, these did improve the performance by a large factor, it's performance on large files and slow network
connections, was still a little below usable.

Apart from this, I had problems running a few Emacs packages such as [flycheck](http://www.flycheck.org/).

### Option III: Mounting Remote file system locally
One of the options I found was mounting a remote file system locally via [sshfs](https://github.com/libfuse/sshfs).
It did have a few problems with connection stability, but it worked fine overall.

I solved a few problems with some optimizations via command-line parameters. The final command looked somewhat like this.

```bash
sshfs remotehost:/remote/directory/ ~/local/directory -oauto_cache,reconnect,Ciphers=arcfour,Compression=no
```
This increased the overall speed and removed sluggishness while editing.

The problem with sshfs is it's speed. Any operation requiring a disk scan was unbearably slow.
So I couldn't run commands like `locate`, `grep`, and [`magit`](https://magit.vc/) via Emacs.

[Projectile](https://github.com/bbatsov/projectile) was usable after `(setq projectile-enable-caching t)` though.

I found a [small utility](https://github.com/ericpruitt/sshfsexec) which addressed this problem.
It works by executing all commands which ran inside a directory mounted on sshfs on the remote host directly.
So, heavy disk operations become very fast as the remote server is doing all the heavy lifting.

To run any command such as `git` directly on remote all I had to do was

```bash
wget https://github.com/ericpruitt/sshfsexec/archive/master.zip
unzip master.zip
mv sshfsexec-master sshfsexec
cd sshfsexec
mkdir -p ~/bin/sshfsexec
cp sshfsexec.py ~/bin/sshfsexec
chmod +x ~/bin/sshfsexec/sshfsexec.py
export PATH="$HOME/bin/sshfsexec:$PATH"
cd ~/bin/sshfsexec
ln -s sshfsexec.py git
hash -r
```
You can check this by running `git --version` from inside and outside the sshfs mount.

The combination of `sshfs` and `sshfsexec` solved almost all the problems I faced with earlier setups.
It was almost always faster than tramp when opening and saving of files, and almost as fast as tramp when doing
disk operations such as opening Magit.

The only problem here was the availability of code when offline. And even though this method was fast, it was
not as fast as a project opened locally. These problems bring us to the fourth option.

### Option IV: Keeping local copy in sync
This is the approach that some of the IDE's take. The code is mirrored locally and the remote code is kept in sync
with the local copy.

There are two parts to this. Firstly, there should be a syncing utility which does the job of transferring the
changes of the file to the remote copy. The second part of it is the file change notifier which will alert the syncing
utility to start syncing.

Initially, I started with running `rsync` in the `after-save-hook` hook of emacs. It worked kind of fine, but the problem was
with the changes made outside the scope of Emacs, such as changing of a git branch. It also restricted me from making
any changes on the remote code directly since there was no mechanism to automatically download the remote copy changes
to the local copy.

On looking a bit further, I came across [Unison](https://www.cis.upenn.edu/~bcpierce/unison/). It supported two way syncing along
with file watch facility. It is required that same version Unison is installed on both local and remote machines.
Following are the steps that will setup Unison.

```bash
sudo dnf install ocaml ocaml-camlp4-devel
sudo dnf install ftp://195.220.108.108/linux/fedora-secondary/releases/24/Everything/ppc64le/os/Packages/p/python-inotify-0.9.6-4.fc24.noarch.rpm
wget https://github.com/bcpierce00/unison/archive/2.48.4.tar.gz
tar -zxvf 2.48.4.tar.gz
cd unison-2.48.4
make NATIVE=true UISTYLE=text
sudo cp src/unison-fsmonitor /usr/local/bin
sudo cp src/unison /usr/local/bin
hash -r
```
Repeat these same steps on the server.
It is preferable to remove `.git` folder from syncing. This can be done by creating/editing a `~/.unison/default.prf`
and adding

```
# Unison preferences file
ignore = Path {.git}
```
You should also remove other build/libraries directories that you won't be editing. This will decrease
the amount of files it has (and memory it takes in the process) to look for changes.

You can now start the sync by
```bash
unison default ~/local/copy ssh://server//remote/copy/path/ -repeat watch -times  -logfile /tmp/unison.log
```
This will keep on looking for changes in the local copy and sync the remote every time there's one.

In the case when a sync is required from the remote to local

```bash
unison -batch -times ~/local/copy ssh://server//remote/copy/path/ -logfile /tmp/unison.log
```
can be used.

In case of errors such as `Errno=No space left on device (ENOSPC)`, the inotify memory can be increased
by setting `sudo sysctl fs.inotify.max_user_watches=20480`. This memory uses
[kernel memory space](https://en.wikibooks.org/wiki/The_Linux_Kernel/Memory#Process_Memory_Layout)
and is not swappable. Therefore, this shouldn't be increased too much if you don't have sufficient RAM.


I initially used `sshfs` method for a long time along with `tramp` for most of my work,
but recently have switched to maintaining a local copy of the codebase.

### Concluding

The choice of the method completely depends on what the purpose of editing is.

For a quick change in a server I always prefer `tramp`. In the case when I'm doing some sysadmin work,
I prefer installing Emacs on the server and using `emacsclient` to open and edit files quickly.
When working on code, unless it's not fairly large repository, I prefer `sshfs`.
Since the current scenario requires me to work on a large codebase where sshfs (kind of) breaks
I keep everything copied locally and in sync with the server.
