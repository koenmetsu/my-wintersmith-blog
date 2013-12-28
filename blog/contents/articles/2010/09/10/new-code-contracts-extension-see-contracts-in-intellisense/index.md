---
title: "New Code Contracts Extension: See Contracts in Intellisense" 
author: koenmetsu
date: 2013-09-10 12:00
template: article.jade
---

<span style="font-family:Times New Roman;font-size:12pt;">Code Contracts just got a whole lot better with a brand new extension for Visual Studio 2010!
</span>

<span style="font-family:Times New Roman;font-size:12pt;">This new extension brings a couple of cool new features that help you while developing with Code Contracts.
</span>
<h2>See contracts as you type</h2>

<span style="font-family:Times New Roman;font-size:12pt;">Just start typing a method with contracts, and they will be listed right beneath the description of the method.
</span>

<img src="http://koenmetsu.files.wordpress.com/2010/09/091010_1709_newcodecont1.png" alt="" />

The great thing about this is that it works for methods in the BCL as well as your own methods.

<img src="http://koenmetsu.files.wordpress.com/2010/09/091010_1709_newcodecont2.png" alt="" />
<h2>See inherited contracts</h2>

Contracts that are inherited show up above your methods. It's a helpful visual reminder of the contracts that are defined on the interface or class you're inheriting from.

This way you can easily add preconditions and postconditions without having to look back and forth to see which contracts are already defined.

<img src="http://koenmetsu.files.wordpress.com/2010/09/091010_1709_newcodecont3.png" alt="" />

And it doesn't actually add text to your code file, it's just an adornment which you can easily click away too.

<img src="http://koenmetsu.files.wordpress.com/2010/09/091010_1709_newcodecont4.png" alt="" />
<h2>See contracts for external assemblies</h2>

Another helpful addition is being able to see contracts of external assemblies. The contracts are visible in the metadata file you see when you 'go to definition' of a member of a class of which you don't have the source.

<img src="http://koenmetsu.files.wordpress.com/2010/09/091010_1709_newcodecont5.png" alt="" />

This can also be disabled by a simple click of a button labeled "Hide all contracts" ( See, it's all obvious ).
<h2>Conclusion</h2>

Before this extension, visibility of the contracts was one of my major concerns with Code Contracts. Not being able to see contracts as you type made you rely on the static checker to see what contracts were defined on your code. This extension is a great improvement and incentive to using Code Contracts. It's only just released, but I'm loving it already!

Great! So how  can you have a piece of this?

It's easy!
<ol>
	<li>Install the latest version of <a href="http://research.microsoft.com/en-us/projects/contracts/">Code Contracts</a></li>
	<li>Install the <a href="http://visualstudiogallery.msdn.microsoft.com/en-us/85f0aa38-a8a8-4811-8b86-e7f0b8d8c71b">Code Contracts Editor Extension</a> for Visual Studio 2010.</li>
	<li>Enable Code Contracts and choose 'Build' for 'Contract Reference assembly' in the Code Contracts properties pane.</li>
	<li>Build your code</li>
</ol>
And you're ready to see your contracts showing up as you type! Have fun =)
