---
layout: post
title: "GSOC Midterms: Half Over is Half Left"
date: 2014-06-29 16:30:07 +0530
comments: true
tags: gsoc drupal fluxkraft fluxpocket
description: An account of the journey in GSOC till the midterms
categories: [Web, Life]
---
<div align="center">
<img src="/images/gsoc-midterm.png"/>
</div>
<br>
GSOC Midterms ended few days back and it's been fun so far. In my previous post I briefly touched upon my project, **[fluxpocket](https://www.github.com/gleek/fluxpocket)** , which is an extended service for **[fluxservices](http://www.drupal.org/project/fluxservice)**, which is based upon **[fluxkraft](http://www.fluxkraft.com)**, which runs on **[rules](http://www.drupal.org/project/rules)**, which is based on **[Drupal](http://www.drupal.org)**!!
<!-- more -->
<div align="center">
<img src="http://drunomics.com/files/what_the_flux_560.png" width="300"/>
</div><br>
Well, it gets a bit confusing sometimes. But for making things easier, [consider these ifttt services](https://ifttt.com/recipes?channel=pocket#popular), \(take a minute for that\), now imagine these running on your own server or website and all the keys to your valuable data secured - and most importantly - under your control!

###What Works so far ###
**The Actions**. You can perform almost all the actions supported by Pocket through the API. Thus some examples of what you can do so far are:

- Posting your Posts simultaneously to Drupal and Pocket
- Getting your new Feeds directly in Pocket
- Posting links to favorite tweets to Pocket
....list goes on, but you get the idea :wink:

###What's left###
**The Events**. The events or triggers are currently under-development and will be under my focus for most of the left-over period. The Events are the portion which react to the changes in the pocket, such as addition of new URL. It will be done by polling the pocket server for any changes in the pocket list after specified interval.

**Documentation**. The fluxservices are not yet properly documented. This will be my priority after I finish up with the Events.

###How's everything else?###
I have done some changes on how I manage things regarding the project , for instance, I now use [github milestones and issues](https://github.com/Gleek/fluxpocket/issues) to track my progress instead of completely depending on titanpad for that.

I've also stopped pushing my code to my [drupal sandbox](https://www.drupal.org/node/2282655) and I only update my [github repository](https://www.github.com/fluxpocket) now. I'll transfer it to drupal when the project's complete.

Other than that I've started to track my time using [hamster](https://github.com/projecthamster/hamster) which tells me that I spend more time researching than actual coding. It also tells me that T.V. is a real time killer :grimacing:.
(P.S. I don't track the sleeping hours...the long ones)

![time overview](/images/time_overview.png)

Other than that I might have misconfigured my mind's clock cycle. I am usually sleeping when the 'normal' humans work and work when they sleep.. and it's really hard to get rid of this schedule.

I wish to write more but [hamster](https://github.com/projecthamster/hamster) tells  me that I've spend far more time on this than originally anticipated. So I'm gonna switch back to coding and hope everything works out in the end.
