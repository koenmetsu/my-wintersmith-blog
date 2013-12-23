---
title: Getting started with command-line distributed version control
author: koenmetsu
date: 2012-07-29 12:00
template: article.jade
---

Getting started with command-line distributed version control

For those of us coming from version control systems like Team Foundation Server, Subversion or similar systems with a graphical user interface, command-line version control systems might come off as arcane, unintuitive and not very user-friendly. 

If you're new to distributed version control systems, I'd recommend you to order the free book (even the printed version is free!) by Eric Sink, [Version Control by Example](http://www.ericsink.com/vcbe/). It has a great workflow comparison of Subversion, Mercurial (Hg) and Git and gives you some insights on why you should use a distributed version control system.	

##Why you should learn a command line DVCS
Next to the advantages of a distributed vcs, using a command-line dvcs is:

- blazingly fast
- very user friendly ( especially Hg )
- incredibly powerful (especially Git)
- amazingly flexible (especially Git)

The problem with graphical shells over a more command-line version control system is that as a new user it's harder to understand the version control system underneath by trying to shield the user from it with "easier" jargon and automatically performing steps for the user ( without the user realizing). 

On the work floor this added jargon can cause confusion amongst developers using different graphical shells, when in essence they're using the same version control system. Using Git or Hg via the command line gives you an experience closer to the inner workings, and will enable you to use the full power of those systems.

##Starting with Mercurial

If you're just starting out with a distributed version control system, I'd recommend using command-line [Mercurial](http://mercurial.selenic.com/) for it's user-friendliness and easier learning curve. [Joel Spolsky](http://www.joelonsoftware.com) has an wonderful tutorial on Mercurial called [Hg Init](http://hginit.com/). You should totally follow it if you're interested in starting out with Hg or any dvcs.

If you're still a bit uneasy about going full command-line, try using the command-line together with [TortoiseHg](http://tortoisehg.bitbucket.org/) (in my opinion the most mature and user friendly free GUI for Mercurial). This way you can actually see your command-line changes appear simultaneously in the [TortoiseHg Workbench](http://tortoisehg.bitbucket.org/manual/2.4/workbench.html). The Workbench also puts the commands you made in the GUI in the output log, so you can see which command you have to use the next time you want to merge.

Having a GUI as a visual guideline and being able to switch easily between GUI and command-line ( for the more complicated commits ) helped me a lot during my initial dvcs learning.

##Moving to Git
Once you've got the taste of working with the command-line via Hg, you should definitely try out Git. It's local branching model is more light-weight and intuitive, and doing complicated commits from the command line is much easier. 

With Git's staging model, you can select files individually and even select separate lines of a file for a commit, which means you can now properly commit the lines of code you changed for story/ticket XYZ, and keep your commits smaller and cleaner.

On top of that, Git feels like it was made purely for command line usage. Need an example? Take a look at this graph Git can generates.

I've been using Git at home for about half a year now and 2 months with my employer, and not a single time have I felt the need for GUI.

Honestly, the first few weeks ( especially with Git ) you're going to do a lot of lookup work. Git still suffers from a major [curse of knowledge](https://en.wikipedia.org/wiki/Curse_of_knowledge), especially for us Windows users, so I'm trying to add my bit to help you on your way ;-)

If I've got your attention, hold on to the next post, in which I'll explain how to set up Hg and Git with the least possible friction for us Windows users.

##Other References to get you started

[Git for beginners: The definitive practical guide](http://stackoverflow.com/q/315911/367388)

[Pro Git](http://git-scm.com/book), which you can download for free in PDF, mobi or ePub format.

For a good comparison of the learning curves of Git and Hg, take a look at [this answer on stackoverflow](http://stackoverflow.com/a/892688/367388), it explains why [Git is MacGyver and Mercurial is James Bond](http://stackoverflow.com/a/35845/367388)




















