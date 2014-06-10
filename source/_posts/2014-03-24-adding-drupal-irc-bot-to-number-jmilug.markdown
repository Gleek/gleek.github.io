---
layout: post
title: "Adding Drupal IRC-Bot to #jmilug"
date: 2014-03-24 22:45:47 +0530
comments: true
tags: bot community drupal irc jmilug
description: Guide to add an IRC bot to a channel
categories: [Web, Usability]
---
[![IRC](/images/irc.jpg "IRC Screen")](http://www.flickr.com/photos/kalleboo/2215471286/sizes/o/in/photostream/)

One of the main drawbacks of IRC-chat is the absence of logging. This was the main reason why our community JMI-LUG almost stopped using the channel for any discussion, as there was nothing to refer to later.
  There was a need for a kind of a bot which could save all the logs of the chats we had. Hence, I began my search for any open-source IRC bot to cater our needs.
I found [many bots](http://en.wikipedia.org/wiki/Comparison_of_Internet_Relay_Chat_bots) which could do the task. 

In my research I found a [bot](https://drupal.org/project/bot) which could be integrated with Drupal and can be installed as a simple Module. As a matter of fact it is already used to log all official Drupal Channels (you can find it [here](http://druplicon.info)). Since, the JMI-LUG website is already on Drupal it was a nice idea to use this one.
####Installing####

- Bot can be installed via update manager module of drupal or can be `git clone`d in the `/sites/all/modules/` directory.
- Installing the Net_SmartIRC libraries with `pear install Net_SmartIRC` (make sure to change the owner of the installed libraries)
- Configure the Bot Settings from the configuration Menu.
- Change the permissions from the Modules list.
- Use shell to run `drush bot-start &` from the Drupal installation directory to start the bot

Bang, you're done, have fun with your new bot. The bot can be trained using Botagotchi and adding factoids from the chat.
