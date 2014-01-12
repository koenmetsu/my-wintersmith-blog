---
title: "NuGetFight: my first OSS out in the open"
author: koenmetsu
date: 2012-06-01 12:00
template: article.jade
filename: /:year/:month/:day/:title/index.html
---

The past couple of weeks [Kevin Pelgrims](http://www.kevinpelgrims.com/blog) and I teamed up to create [NuGetFight](http://www.nugetfight.com), a website that enables you to easily compare NuGet packages based on their usage stats. 

As part of improving my coding skills, I lot of the time I spend is in reading blogs and articles. However, only reading up on technology will only take you so far. Trying out some new technologies like NoSQL or SignalR is fun as well, but usually doesn't go any further than a few small POCs. It hardly covers all the aspects of software development we "meet" in real life.

This year I decided to actually create stuff. The premise for this was simple: I wanted to use technologies that are new for me, or learn new ways to use them, everything had to be open-sourced, and probably most importantly: it had to be fun.

New technologies
===
NuGetFight was created with ASP.NET MVC 3, along with an HTML 5 canvas to create and animate the bar graphs. We decided not to use a library to create these bar graphs, but instead rolling our own. This is not something I'd recommend for real business projects (use a framework instead), but it was great fun and frustration as we were learning all about the different ways to animate the canvas with javascript. I learned a lot of new stuff there, and I'm pretty glad with the results as well.

We wanted to create some very basic and light-weight logging of the fights, for which we ended up using [MongoDB](http://www.mongodb.org/), a document-oriented NoSQL database I talked about earlier on this blog. We used [MongoLab](https://www.mongolab.com) to host a free database in the cloud. This was very lightweight like we wanted to, but we also had some minor issues with it that you would never notice without actually using it in production. In the end however, I am very pleased with how it worked out, and would definitely use this setup again.

We also used the [NuGet OData API](https://www.nuget.org/api/v2/) to query the packages, which was a breeze to use, and hardly worth mentioning here as it's as simple as consuming a common webservice. The most important thing here is that I learned how invaluable [LinqPad](http://www.linqpad.net) really is if you want to try out some queries to an OData feed, before you actually start coding them. We had some issues with the data coming through, and LinqPad was a very useful tool to verify and fix this little bug on our side.

And finally, as we are working from geographically very different locations, a [distributed version control system](https://en.wikipedia.org/wiki/Distributed_revision_control) like Mercurial seemed like a natural fit. I've known and used [Mercurial](http://mercurial.selenic.com/) and [Git](http://git-scm.com/) for a little while now, but had never used it this extensively and actually, you know, distributed. We used [BitBucket](https://bitbucket.org/) as our central repository, and it worked great in every single way. The peace of mind local checkins give you, the ease of merging, light-weight branching, ... Once you get used to DVCS you wonder how you ever coped without. If you're working on a pet project in your spare time right now, even if you're working alone on this, I can fiercely recommend learning about DVCS and using it together with a hosting like [BitBucket](https://bitbucket.org/)  or [Github](https://github.com/).

Overcoming fear of being in the open
===
We decided on BitBucket because it can host Mercurial ( which is easier [if you're new to DVCS](http://hginit.com/), in my opinion ), and because it allows for repositories to be private. Putting our code out in the open for the first time is something we were reluctant to do, and BitBucket gave us the opportunity to develop in a private repository, before [opening it up to the public](https://bitbucket.org/kevinpelgrims/nugetfight) when we were ready for it.

For me, the decision to open-source NuGetFight and our future projects was not necessarily made just to contribute to the community, or because we expected a lot of pull requests from the community. If the community does benefit from our code, all the better, but on a personal level the decision was much more about overcoming the notion that all code should be perfect before putting it out in the open. 


I see a lot of developers having great ideas, but keeping their projects and code to themselves only because "their code is not good enough". This is a shame, and I encourage you to share your pet projects regardless of how good your code is.

More fights to come
===
I had a lot of fun developing NuGetFight, and we will definitely have fun further improving the code and making NuGetFight better. We already implemented integration with [SymbolSource](http://http://www.symbolsource.org/) after a suggestion from [@TripleEmcoder](https://twitter.com/tripleemcoder), so any feedback or ideas you might have for NuGetFight are welcome. 

We've also got a couple of very exciting features coming in the next week(s), so keep in touch.
