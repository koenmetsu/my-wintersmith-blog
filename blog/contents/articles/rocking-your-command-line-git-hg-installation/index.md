---
title: "Rocking your command line: Git & Hg installation "
author: koenmetsu
date: 2012-09-10 12:00
template: article.jade
---

// in my previous post, ... blabla

If you're starting out with the command line of Git or Mercurial, this post can help you make things more comfortable for you ( and serve as a reference for my future repaves ).

#Installation

##Hg Installation
link: [http://mercurial.selenic.com]( http://mercurial.selenic.com/) (comes with TortoiseHg)

Just follow the installation ( next next next ). Done!

##Git Installation
link: [http://git-scm.com/](http://git-scm.com/) 

The only thing I suggest you modify during the installation is the PATH. Selecting this option will enable you to run git from your regular windows cmd. Everything else is next next next.

![Git Setup](http://koenmetsu.com/get/images/commandlinedvcs/Git%20Setup.png)

###TortoiseGit
link: [https://code.google.com/p/tortoisegit/](https://code.google.com/p/tortoisegit/)
I'm not using TortoiseGit as my main way for working with Git, but it has a couple of nice additions which can prove helpful. It has a good merge tool, a visual shell and a context menu ( which I don't really use, but hey ).

I choose TortoisePlink as the SSH client, as I'll be using it later to make Git remember my password automatically whether or not you're using Git Bash.

![](http://koenmetsu.com/get/images/commandlinedvcs/TortoiseGit%20TortoisePlink.png)

#Setting up SSH for Git
The guys from Confluence have a great guide on [how to set up SSH for Git](https://confluence.atlassian.com/display/BITBUCKET/Set+up+SSH+for+Git). You can skip step 5 if you like, I'll show you another way of getting the same results later in this post.

If you're going to work with github, don't forget to add a key for github as well ( as in step 4 ). You can do this by editing the config file in the .ssh folder in your home dir (~).

![](http://koenmetsu.com/get/images/commandlinedvcs/SSH%20folder.png)

You should something like this now:

> Host bitbucket.org<br />
> User koenmetsu<br />
> IdentityFile ~/.ssh/id_rsa
> 
> Host github.com<br />
> User koenmetsu<br />
> IdentityFile ~/.ssh/id_rsa

Be sure to add your key online as well in your GitHub profile settings.
Now you have one key that works with both Bitbucket and Github!

When you start your Git Bash now, you should be asked for your password.

![](http://koenmetsu.com/get/images/commandlinedvcs/Git%20Bash%20password.png)

##Remembering your password
Git asks you for your password every time you want to pull or push something from your GitHub/BitBucket remotes, something that can be quite annoying.

To overcome this annoyance:<br />

1.  [make Git remember your password under Windows](http://stackoverflow.com/questions/370030/why-git-cant-remember-my-passphrase-under-windows)
2.  [automatically add the keys at Windows startup](http://blog.shvetsov.com/2010/03/making-pageant-automatically-load-keys.html)

If you've got both TortoiseGit and TortoiseHg installed, be sure to use the pageant and tortoiseplink executables from one of the installations. Mixing them up will cause the above solution to not work.

#Setting up SSH for Mercurial
Again, the guys from Confluence did a great job here, just follow their guide for [setting up SSH for Mercurial](https://confluence.atlassian.com/display/BITBUCKET/Set+up+SSH+for+Mercurial). Except, you can now reuse the private key we generated in the "Remembering your password" section above, so you don't have to generate a new one like the guide says. Isn't that great? Less key management, more fun!

All done, now you can use the command line for Mercurial and Git without the hassle of remembering passwords.

#Making Git Bash more Windows friendly
Git Bash is a great tool which has quite a few perks if you're using Git. Most importantly, it has completion on the git commands and stuff like your branches. This will save you a lot of frustration trying to find out what name you gave that one feature branch. It also shows you which branch you're currently working on ( see screenshot above ). 

Git Bash might seem a bit odd if you're used to working with the Windows command line, but there are a few tricks to make it behave more Windows-friendly.

##Tab completion
For cmd-like tab completion and a case-insensitive tab completion:

Create a new file .inputrc in your home folder 
>           "\C-i": menu-complete
>           set completion-ignore-case on
> 

(source [http://superuser.com/a/222393/132009](http://superuser.com/a/222393/132009) )

To create a file in Windows that starts with a dot, name it ".filename.", the last dot will disappear

##Your own text editor instead of Vim
Vim is an awesomely powerful tool, but if you're not feeling ready for Vim just yet, just copy this command in the command line.
> git config --global core.editor "'c:/Program Files (x86)/Notepad++/notepad++. exe' -multiInst -notabbar -nosession -noPlugin "

(source: [http://stackoverflow.com/a/773973/367388](http://stackoverflow.com/a/773973/367388) )

Of course you change the path to Notepad++, or use any text editor you like. 

##A more visual merge tool
Not to claim this is the best one ( I haven't done a comparison yet ), but TortoiseMerge might feel more comfortable than vimdiff if you're not used to vim.

On my pc, TortoiseMerge was automatically set as the default mergetool after installing TortoiseGit. You can set it manually as well by putting this in the git config.

> [merge]<br />
> tool = tortoise
> 
> [mergetool "tortoise"]<br />
> cmd = "TortoiseMerge.exe" -base:"$BASE" -theirs:"$REMOTE" -mine:"$LOCAL" -merged:"$MERGED"


(source: [Getting Git to use TortoiseMerge](http://programmersunlimited.wordpress.com/2010/07/01/getting-git-to-use-tortoisemerge/))
