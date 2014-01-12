---
title: Something, something, … Refactor!
author: koenmetsu
date: 2011-02-15 12:00
template: article.jade
filename: /:year/:month/:day/something-something-e2-80-a6-refactor/index.html
---

Many of us developers leave for work on a daily basis, ready to throw ourselves onto the next change request that will change the world as we know it, only to find yourself hack ‘n’ slashing through <a href="http://thedailywtf.com/">a jungle of WTF’s</a>, <a href="http://en.wikipedia.org/wiki/Copy_and_paste_programming">copy-paste inheritance</a>, <a href="http://stackoverflow.com/questions/143701/what-is-the-worst-class-variable-function-name-you-have-ever-encountered">awfully named fields</a>, and <a href="http://www.osnews.com/story/19266/WTFs_m">more WTF’s</a>.

This probably sounds like a broken record to you, and though I could go on all day presenting you with examples, I’d rather suggest an alternative: <strong>Refactoring.</strong>

Refactoring is a word mostly spoken in the domain of <a href="http://en.wikipedia.org/wiki/Test-driven_development">TDD</a>, from its well known mantra “<a href="http://www.kodefuguru.com/post/2011/01/29/Red-Green-Refactor.aspx">Red - Green - Refactor</a>”.  However, refactoring does not belong exclusively to the exotic world of TDD, which can spark fear in the minds of many developers not familiar with TDD.

Refactoring has been the topic of <a href="http://www.refactoring.com/sources.html#Books">many books</a>, and rightfully so. The <a href="http://www.refactoring.com/catalog/index.html">list of possible refactorings</a> is a long one, but many of these techniques are really quite simple.
And more importantly: it can <strong>significantly improve your code base</strong>.

Yes, refactoring can <strong>improve readability and flexibility</strong>, which in turn <strong>improves maintainability</strong>. Improved maintainability leads to <strong>less money spent</strong> on fixing bugs, which leads to <strong>happy customers</strong>, which leads to less picking on us poor developers, a more <strong>satisfying job</strong> and ultimately: <span style="text-decoration:underline;"><strong>improved health by reduced stress</strong></span>. See that? All benefits! =)
<h2>When done, refactor</h2>
So why do we write less readable, less flexible code than we possibly can?

With deadlines and project managers breathing down our neck, it is easy to conveniently forget the refactoring part and move on to the next task at hand. We hope to never see that piece of code again, or think that the code we just wrote is “pretty ok enough" to understand 6 months down the line ( <span style="text-decoration:underline;">hint: it isn’t</span> ).

So when you’re leaving the campground, be sure to <a href="http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule">leave it cleaner than you found it</a>, and <strong>clean up after yourself</strong>. Start off by asking yourself the following simple questions:

<ul>
 <li>Could my field names be any more meaningful?</li>
 <li>Are my method names truthful? ( ie: <a href="http://blogs.msdn.com/b/marcelolr/archive/2010/06/30/api-design-rule-first-don-t-lie.aspx">don’t lie</a> )</li>
 <li>Do I repeat myself unnecessarily?</li>
 <li>Does my code need any documentation? ( answer = <strong>yes </strong>)</li>
 <li>Do I still need that piece of commented code? ( answer = <strong>no </strong>)</li>
 <li>Could any other developer read this code and on sight understand what it does?</li>
</ul>

Contemplating about these things alone can be the first step towards a cleaner codebase and a happier life in code, knowing you’ve become a better developer. Next time you have to change something in that particular code file, <span style="text-decoration:underline;">you will thank yourself</span> you took 5 minutes to clean up.

So while you’re at it, why not also improve your codebase with:

<ul>
 <li>Checking if your code is <a
   href="http://en.wikipedia.org/wiki/Solid_(object-oriented_design)">SOLID</a></li>
 <li>Programming to interfaces instead of 
   implementations?  </li>
 <li>Writing meaningful tests?</li>
</ul>
<div>

There are so many other things you can do to improve your code. <a href="http://codebetter.com/">Keep reading about ways to code better</a>, and remember to refactor and clean up your code whenever you’re done with a little piece of code.
<h2>Conclusion</h2>
Even if you won’t have to maintain your code in the future ( never say never ), clean up your code when you're done with it, even if it's just for good programmer’s Karma and <a href="http://www.codinghorror.com/blog/2008/06/coding-for-violent-psychopaths.html">the next guy that might have to maintain it</a>.

Stay realistic: your code will never be perfect. But <a href="http://www.mehdi-khalili.com/bad-code">writing bad, cluttered or unreadable code willingly or knowingly</a> should never be an option, and since you have read this post, you now no longer have any excuse. ;-)

</div>
&nbsp;

