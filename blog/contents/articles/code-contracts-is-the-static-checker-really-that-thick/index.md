---
title: "Code Contracts: Is the static checker really that thick?"
author: koenmetsu
date: 2010-06-30 12:00
template: article.jade
filename: /:year/:month/:day/:title/index.html
---

When you start working with Code Contracts, you often get the feeling that you have to add contracts everywhere for everything. When you enable the static checker on an existing project, you might get <strong>a lot</strong> of warnings.

<a href="http://koenmetsu.files.wordpress.com/2010/06/code_contracts_warnings2.png"><img class="size-full wp-image-105" title="Static Checker Warnings" src="http://koenmetsu.files.wordpress.com/2010/06/code_contracts_warnings2.png" alt="A lot of these" width="600" height="145" /></a>

Something that troubles starting users is the fact that you have to add a lot of contracts 'twice or more'. I've recently seen this issue appear on <a href="http://stackoverflow.com/questions/3141025/net-4-code-contracts-do-i-need-to-include-the-same-contracts-twice/3141176#3141176">stackoverflow</a> as well. You can check out the specific code sample there, but I'll lay it out for you here as well.  Suppose you have a public method calling a private method, both of which accept an input parameter of type string.

    public void ValidateString(string givenString)
    {
        Contract.Requires(!string.IsNullOrEmpty(givenString));
    
        var isValid = SomeValidatingMechanism( givenString );
    }
    
    private bool SomeValidatingMechanism( string toValidate )
    {
        return toValidate.Contains(&quot;someImportantValue&quot;);
    }

I've immediately added a precondition to the ValidateString method, to make sure the caller never wrongfully provides me with an empty string and make my application crash to death.  </br></br>Now when you let the static checker loose ( and you've set it to check for possible nullreference occurrences), it will whine about my private method calling Contains on a possible null value. What's that all about? I added a precondition to the public method, so the toValidate string can't be empty, right?
<h2>Solution</h2>
Well, actually the static checker is really thinking ahead here. </br></br>First of all you've got the static checker which cannot <strong>prove</strong> that the the toValidate string isn't actually null. <strong>You know it</strong>, because you can clearly see from the code above. But the static checker cannot mathematically prove that you did not alter the toValidate string after it entered the public method. For all it knows, you might have maliciously set it to be null right after it entered the method, trying to crash my application once again!  This might seem like a limitation to the static checker, but imagine you made some calls to an external API before you called the private method here. The static checker is just really playing it safe.  </br></br>Secondly, for now you might have only one call to the private method, but what happens when you add more calls to it from methods which didn't have a precondition like the one above? Adding a precondition to the private method now can prevent future errors and possibly lots of debugging.

    public void ValidateString(string givenString)
    {
        Contract.Requires(!string.IsNullOrEmpty(givenString));
    
        var isValid = SomeValidatingMechanism( givenString );
    }
    
    private bool SomeValidatingMechanism( string toValidate )
    {
        Contract.Requires(!string.IsNullOrEmpty(toValidate));
        return toValidate.Contains(&quot;someImportantValue&quot;);
    }

With the above code the static checker's warning is gone, and your code feels safer once again =) You can sleep tight and never worry about some co-developer calling your private method with an empty string.  </br></br>So no, the static checker isn't really that thick, it's actually quite smart and following it's advice can often lead to better and safer code.
