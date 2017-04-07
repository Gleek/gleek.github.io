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
<img src="https://lh3.googleusercontent.com/O2hQSeV_aZFFQH0PQgh-AV5c9b3Gvzx8U3_O2OLidJXUOCnWGPLN6DyE7KdOXXWG1KZuSGer-0sDzHXoHjv2bGtPnXtE4jVoygB7IhFoharxvP-GGul4UAe68sL7Jp8O0y7PG9VneRwmhFOuIFFeXAVy4fpBbJ-DDV4ymv-VwnQFh31BEMokAHwDb2E2jB3R4PHWKN-GptRNHWG8SGbndLXREoi-lyRUo9DSMEAeiUyrCwhc4-UFU4hvE8JksEs8tXSL-rQ6dgO9Qjw7u1jYidXRX8kRKaj1t0RV0R4PjvJhkn6-u_1ODqWfIMGfx_MQ_uCS1FQv503oAC1BArzbRwEjLX0sp7RhKf0-EeWuna3UDLlbanOJd5alAFbj0Z2HKRmD58rStwQIvLheLpjCGmKdeXEo3xB5fHHtx8zJLksjU2cCxFgAC71tXiUeeLZ2WYWups5Q7U72B1mXzGqXUQFH1E-GtfXaD1tZuHJ5I-n13A-lKvPCEK5hWYF8ImRAa3Kg2vv3tVnvUIPWcMcuoQO1RJDZik5YImF8F7SU_FCHavtaEJz5AGaQYn3r8DVYHM2WePN_htsPV7Gt-KNPfd9wMbVHY5keT_iTRQ0rYPhhKPojx2Rq7mkGPtq_SVdOScX5quCjjRzaFzx836GLqeyhim7cn9RB9KHvQu_b8g=w600-h160-no"/>
</div>
<br>
GSOC Midterms ended few days back and it's been fun so far. In my previous post I briefly touched upon my project, **[fluxpocket](https://www.github.com/gleek/fluxpocket)** , which is an extended service for **[fluxservices](http://www.drupal.org/project/fluxservice)**, which is based upon **[fluxkraft](http://www.fluxkraft.com)**, which runs on **[rules](http://www.drupal.org/project/rules)**, which is based on **[Drupal](http://www.drupal.org)**!!
<!-- more -->
<div align="center">
<img src="https://lh3.googleusercontent.com/ogTFYEpIzoDLq1yNZWVxpd0WCcoAclC8x5bCqGrO1n7B8TPirtTKVwQ3Xc0ccvLa8bOT7WRV7aFlT-ut1ldluZQw7Zdc-I8SMFSemoMZGAbHUheeLxQPQElr5hz0DtPpqMqNcE22ZFT4REP9BGHHbXospKBsZGo6F-h8D_t6zOMpHWsa_jt-A74huWTOied0-YLTK-F20Byl-pBdjefga60uDP3BiN0SVBEPkovWigv8-GLAiGw6v_zxtmqUXq3bYc8pKxiAqTu8r0RCKBO5OfUE8yqLfFpb9Qm_dX5y6pyIofEw__du1ORg2D7HxBjfNFU-6VXJkE_JGSt-SHF9s0vAK15_nLJIDFAM92aLTjupzmhgp8z-tcPMNPjRyY3KeYyfdUsMEnXFNd2KXGnejvJn80B3E3_3mOgMHYa-zfcdNo7tVg38935IgFwrZDjZ6HqD98_f-ra2wpr8LzxRH7lF0ObWWM-67aGKkdK7JC2zmndQqu265gLyY8CgqWorGr1SdN9KeFANnJ84ZQoZt_SeMpxcAjojFgsnbS7O2hhKbAIiIWI7ITeospKVJu-0E-GLNZee9eIEkiY0W6E-e0fWC-pX-E5AA2TuBITAC99YiGhvRUII2xEPq4JzBPG_6jkCZuM3IUAF31SQ3R-UsYv4myJLoeQK1Z3ygG9UWA=s300" width="300"/>
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

![time overview](https://lh3.googleusercontent.com/HOlEm2-_EvezvAO4CEUKdBGT8bh5O2ZMcY4ukToz_mt5XDYn2jLQIRqMLQKOnAzzEGPUpxbrPpT2PpcO2iQzwLIneSzggaxw41d2q6io84TzE53Hhc8m-4fqW1bFzH2FB3cWqpkx2eZZp9NC80kDw1Yy37zv4--fzCc9TTD8xCcOb2iVLWJtovj_uRcbYcjKUPFdBw8c3e-iiLjQ-henqDk2HXDRbOlwlo22w0XAwqfW2S5s1zrT4GIgFxjEZmXoguQxV5dYw7sTb3hBAgdJ9KVhduYi3LvMaOuLHnBwzfwYfRKFCmv_k6DzevvLA9goDE0WDEdWpXbrSzSbJXhQaHNgpyomiPEpDgrOqu0yadVF-NuKbn-raEtT0DWaes53CxiDUKIHyPa_hqfddsNq8kNSG0bzC2Wr1HqU1d-81sjwjYm4-go1cN2vWh_rOlKmeTNP1PjRlMxsX1UccRk5qH0Wkn7A7i--O46wlH0yyOocjXDo1ooQUTLLbNShM6xMymrB_vA-o4EBUXEZRKhw0YLgz19lZXQ8pGldbcwVPBZvTf9W_IXP2Oo7NThCUeT-qRM-2MZD9tslPZF2pf-A9ctdQkJVc1gvhHiUHaY2e567_ryW-O1L=w1286-h422-no)

Other than that I might have misconfigured my mind's clock cycle. I am usually sleeping when the 'normal' humans work and work when they sleep.. and it's really hard to get rid of this schedule.

I wish to write more but [hamster](https://github.com/projecthamster/hamster) tells  me that I've spend far more time on this than originally anticipated. So I'm gonna switch back to coding and hope everything works out in the end.
