---
layout: post
title: "From WordPress to Octopress"
date: 2014-04-18 20:07:03 +0530
comments: true
tags: blog, platform, wordpress, octopress
description: Why I moved from WordPress hosted blog to Octopress
categories: [Life, Usability]
---
*This post is about choosing Octopress over **WordPress hosted** blog, it does not talk about WordPress as a framework.*

It has been a very few days I started this blog. Now I feel a bit of a weird pride in announcing that this may be the last post on the wordpress, it's now hosted on github - [http://gleek.github.io](http://gleek.github.io/) , and powered by Octopress.

###Why I chose WordPress?###
When I first thought about blogging, the first thing that came to my mind was choosing the right framework for it. Three of them came to my mind, namely Drupal, Wordpress and Octopress. Since I didn't have any reliable hosting at that time and had previous experience with WordPress, I decided to go with blog hosted on Wordpress.com.

###The problems###
What I didn't realize at that time was that **installing and using wordpress, on an owned server, was a lot different that hosting a blog on Wordpress.com.**

The main problem is that **I have no desire to empty my pockets on a blog, but still demand full control over it.**

WordPress sets up a free blog with a theme, but I had to pay even for the slightest tweak. So most of my problems which weren't expected initially were:

- There are a lot of themes which were usable for free, but tweaking the themes is not tolerated without costing you some bucks.
- I couldn't control the back-end of the blog. (I expected that, actually :grin: )
- You can't write JavaScript
- You can't write your CSS without paying a little something. I had to write some inline CSS to make something a little prettier.
- WordPress puts its advertisements at the end of every blog post.
- Custom WordPress plugins cannot be used in the blog.

###Switching to Octopress###
Disappointed by WordPress, hosting my blog on Github or Heroku with Octopress seemed to be the only option. Since I keep almost all my projects on github, I chose the same for the blog. There were some initial problems while setting up the blog. But [issue queue](https://github.com/imathis/octopress/issues) helped me in solving them.

 **Pros**

- I get the content control over my website. Above mentioned problems in wordpress site such as no JS/CSS support is now solved.
- It's not necessary to be online while you write the blog
- Git is used to manage the blog which makes it easy to manage.
- Static pages makes it incredibly fast.
- Posts are written in Markdown

**Cons**

- Initial installation and setup is a bit time-taking.
- Your blog is restricted to your local machine. To use a different machine to blog, you'll have to clone entire blog on it.(Which also eliminates using mobiles for blogging)
- For large websites generating the pages can take some time, though using `rake isolate[path/to/post.markdown]` and `rake integrate` may solve the problem if you are working on a single post. Find more on [Pavan's blog](http://blog.pixelingene.com/2011/09/tips-for-speeding-up-octopress-site-generation/)

You can take a look at performance aspect of Octopress on [Praveen's Blog](http://decodize.com/html/moving-from-wordpress-to-octopress/).

###Summary###
Choosing a framework for a Blog is a matter of choice. As far as I am concerned I'm satisfied with the results Octopress is giving me. I might remind you that this post was on my experience in blogging at [WordPress](http://noobpanic.wordpress.com) and on [Octopress](http://gleek.github.io).
