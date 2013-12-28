---
title: Moving from WordPress to FunnelWeb
author: koenmetsu
date: 2013-03-01 12:00
template: article.jade
---

The problem
===
Begin this year, I decided to pick up blogging again. I had some good ideas to blog about (most of which I probably forgot already), but one thing kept me from doing so: <b>WordPress</b>. 

I think WordPress has a great platform, but I've never found the actual blogging to feel natural. This is mostly due to the online editor which is just really, really awful to work with. 

The biggest dealbreaker for me? The lack of control.

Moving away from WordPress was a real pain at times. The plan involved using BlogML and Disqus to make the move an easy one, however nothing worked out of the box. 
If you're interested in reading the full story on moving away from WordPress, I suggest you read [this post](http://kevinpelgrims.com/blog/2012/02/27/upgrading-my-blog-from-wordpress-to-funnelweb) by [Kevin Pelgrims](http://www.kevinpelgrims.com). He kept a nice log of everything that did and didn't go according to plan  :)

#Looking at alternatives

Looking at alternative blog engines, I met [OctoPress](http://octopress.org/), a static site generator which looked really promising (all the cool Ruby kids use this today). I kept holding on to the idea of [baking vs frying](http://www.aaronsw.com/weblog/000404) my site because I liked [the philosophy](http://inessential.com/2011/03/16/a_plea_for_baked_weblogs) of not having to go to your database for every page view (even if that number is not very high).

However, OctoPress missed the ability to publish from anywhere (ie: online) and had a steep enough learning curve to keep me away from it. I was very excited about [Code52](http://code52.org)'s .NET open-source alternative called [Pretzel](http://code52.org/pretzel.html), but this too missed the ease of use I was looking for.

# Enter FunnelWeb: Full Control meets Ease of Use

When I met [FunnelWeb](http://funnelweblog.com), I found what I was looking for:

- Easy editing with [MarkDown](http://daringfireball.net/projects/markdown/syntax#list), which you can easily edit with [MarkPad](http://code52.org/DownmarkerWPF/)
- Good looking source code in posts with [Prettify](http://code.google.com/p/google-code-prettify/)
- Support for themes, and a good number of nice and clean [themes](http://www.funnelweblog.com/theme/gallery) available
- [FunnelWeb's source code](http://hg.funnelweblog.com) (in .NET) looks really good, so I can change anything I want 

In short: lots of control and still easy to use.

#The result
I'm really liking my new blog! Discussions and analytics have been outsourced to Disqus and Google Analytics, and the fact that FunnelWeb has a BlogML export means I can move away from it anytime I want. This post was written using [MarkPad](http://code52.org/DownmarkerWPF/), which is a breeze to use and gives me the content without having to mess around in some badly-generated HTML.

It's exactly this feeling I was after: being enabled by my tools, instead of being hindered by it. I look forward to using FunnelWeb for my further blogging, as well as contributing to it =)
