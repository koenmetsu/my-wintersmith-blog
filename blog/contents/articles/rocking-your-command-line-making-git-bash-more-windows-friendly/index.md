---
title: "Rocking your command line: Making Git bash more Windows-friendly"
author: koenmetsu
date: 2012-10-04 12:00
template: article.jade
---

#Making Git Bash more Windows friendly
![Git Bash in ConEmu](http://koenmetsu.com/get/images/commandlinedvcs/Git%20Bash.png)
Git Bash is a great tool which has quite a few perks if you're using Git. For one, it has completion on the git commands and stuff like your branches. This saves you the effort of looking up the exact name of a branch every time you want to switch branches. Git Bash also shows you which branch you're currently working on , preventing you from working on the wrong branch unnoticed ( as some of my colleagues not working in Git Bash have encountered ).

However, Git Bash might seem a bit odd if you're used to working with the Windows command line, but there are a few tricks to make it behave more friendly to those used to cmd.exe.

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
Not to claim this is the best one ( I haven't done a full comparison yet ), but TortoiseMerge might feel more comfortable than vimdiff if you're not used to vim.

On my pc TortoiseMerge was automatically set as the default mergetool after [my usual git installation](http://koenmetsu.com/rocking-your-command-line-git-hg-installation) which includes installing TortoiseGit. You can set it manually as well by putting this in the git config.

> [merge]<br />
> tool = tortoise
> 
> [mergetool "tortoise"]<br />
> cmd = "TortoiseMerge.exe" -base:"$BASE" -theirs:"$REMOTE" -mine:"$LOCAL" -merged:"$MERGED"


(source: [Getting Git to use TortoiseMerge](http://programmersunlimited.wordpress.com/2010/07/01/getting-git-to-use-tortoisemerge/))

##Aliases
Setting the right aliases in git can save you a lot of time typing out all the right commands and switches, as well as give your mind a rest trying to remember all of those switches.

I've compiled a small list of aliases I've encountered, some of which I use very frequently.

####Hosting a git repo
`serve = !git daemon --reuseaddr --verbose --base-path=. --export-all`

####Showing the last 10 commits
`last = log --pretty=format:"%C(yellow)%h%x09%Creset%an%x09%x09%s" --decorate -10`

####A graph view of your history with branches
`graph = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' --abbrev-commit --all`

####Another graph, with more detail ( and other colors )	
`graph2 = log --graph --all --format=format:'%C(bold yellow)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(bold white)- %an%C(reset)' --abbrev-commit`

####Initialize a repo
`this = !git init && git add . && git commit -m \"initial commit\"`

####Show a list of aliases, sorted
`alias = !git config --list | grep 'alias\\.' | sed 's/alias\\.\\([^=]*\\)=\\(.*\\)/\\1\\t=> \\2/' | sort`


There are many resources online that describe different tactics on aliases, from only using them for the more "complicated" commands ( showing a git graph with dates & author names ) to replacing practically every simple command ( "git st" instead of "git status" ). I usually only use aliases for the commands with lots of switches, since Git Bash will autocomplete simple commands anyways.

(sources, among others: [http://blog.blindgaenger.net/advanced_git_aliases.html](http://blog.blindgaenger.net/advanced_git_aliases.html), [http://gitready.com/intermediate/2009/02/06/helpful-command-aliases.html](http://gitready.com/intermediate/2009/02/06/helpful-command-aliases.html) )
