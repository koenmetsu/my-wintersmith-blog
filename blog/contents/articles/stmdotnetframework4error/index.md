---
title: "STM.NET and .NET Framework 4.0 beta 2 ( Error 1603: A fatal error occurred. )"
author: koenmetsu
date: 2009-11-18 12:00
template: article.jade
filename: /:year/:month/:day/:title/index.html
---

Recently I ran into some problems installing the latest Visual Studio 2010 beta 2. It gave me the very clear error message:

"Error 1603: A fatal error occurred."

Well that about says it all, right...?

After a lot of googling and frustration, it seemed that my previous installation of STM.NET caused this error.

I should have remembered that  "<em>the STM enabled version of Microsoft .NET version 4.0 and official versions of .NET
version 4.0 are mutually exclusive, and cannot be installed simultaneously on the same computer</em>".

Uninstalling STM.NET was not as easy as I thought. I assumed the almighty internet would have answers, but no dice. I spent  about a day and a half of trying almost everything : .NET Framework Cleanup tools, uninstalling anything with '.NET or 'Visual' in it's name, registry cleaning, manually removing folders from the Windows folder  ( I got desperate ).

Finally, I found the answer, thanks to an old Microsoft Support article.

Following the next steps should help you remove the STM.NET version of .NET Framework 4.0:
<a href="http://koenmetsu.files.wordpress.com/2009/11/uninstall-net-framework-4-stm.png"><img class="alignright size-medium wp-image-5" title="Uninstall NET Framework 4 STM" src="http://koenmetsu.files.wordpress.com/2009/11/uninstall-net-framework-4-stm.png?w=300" alt="Uninstall NET Framework 4 STM" width="240" height="150" /></a>
<ol>
	<li>Go to : Start &gt; Run &gt; type 'Installer', press enter</li>
	<li>Right click on the column header and add the 'Comments' column</li>
	<li>Sort alphabetically and search for 'Microsoft .NET Framework 4 Client Profile Beta 1 enabled to use Software Transactional Memory...'</li>
	<li>Right-click and uninstall!</li>
	<li>Reboot ... just in case =)</li>
</ol>
This should enable you to succesfully install the 'regular' .NET Framework 4 Beta 2 and enjoy the new Visual Studio 2010 Beta!
