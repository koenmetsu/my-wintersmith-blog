As stated <a href="http://koenmetsu.wordpress.com/2010/05/13/using-code-contracts-to-define-behavior/">previously</a>, Code Contracts can give you certainty that your classes behave exactly in the way you want them to.
By defining pre- and postconditions on them, you can tell what you expect from a certain class and what others can expect from your classes.

A number of posts and concerns about Code Contracts revolve around the static checker, and how to make it prove that certain contracts are correctly followed.
Sometimes this can be quite challenging, though I see this more as a pro than a con.
Making you think twice (or more) about your code is never a bad thing, really.

But for those who desperately seek salvation in their quest to annihilate all static checker warnings ( with or without Contract.Assume() ), I would recommend the following guidelines:

1. Install the Code Contracts Extension for Visual Studio 2010.
2. Use Reflector to see Code Contracts on the Base Class Libraries.
3. Use Pex to automatically test your methods.
4. Split more complicated statements into multiple lines.
<h2>1. Code Contracts Intellisense.</h2>
<a href="http://koenmetsu.wordpress.com/2010/09/10/new-code-contracts-extension-see-contracts-in-intellisense/">Install the Code Contracts Extension</a> for Visual Studio 2010. This brings contracts right to your Intellisense as you type, as well as some other handy features.
<h2>2. Use Reflector to see Code Contracts on the Base Class Libraries.</h2>
When you use the static checker, you might notice that a lot of methods in the BCL already have contracts defined on them. For example, the IList.Clear() method has a postcondition stating that the Count property will be equal to zero.

These contracts are not magically inferred from the BCL assemblies, but rather found in the Contract Reference Assemblies that are included with the Code Contracts installation. These assemblies are found under &lt;%YourProgramFiles%&gt;\Microsoft\Contracts\Contracts\.NETFramework\v4.0.

<a href="http://koenmetsu.files.wordpress.com/2010/11/code_contracts_bcl_assemblies.png"><img class="size-full wp-image-169" title="Code_Contracts_BCL_Assemblies" src="http://koenmetsu.files.wordpress.com/2010/11/code_contracts_bcl_assemblies.png" alt="Code Contracts BCL Assemblies" width="476" height="307" /></a>

Using <a href="http://www.red-gate.com/products/reflector/">Reflector</a> you can browse through these assemblies, which contain nothing but Contracts. Although a lot of methods already have contract defined on them, the BCL contract assemblies still have a lot of contracts missing.
Using Reflector on these assemblies, you can find out for yourself why you keep getting a warning that a certain "contract cannot be proven".

<a href="http://koenmetsu.files.wordpress.com/2010/11/code_contracts_bcl_reflector.png"><img class="size-thumbnail wp-image-170" title="Code_Contracts_BCL_Reflector" src="http://koenmetsu.files.wordpress.com/2010/11/code_contracts_bcl_reflector.png?w=150" alt="Code Contracts String.Format in Reflector" width="300" height="146" /></a>
<h2>3. Use Pex to automatically test your methods</h2>
Pex provides a way to create parameterized unit tests to see which input causes your method to violate a contract. Actually, it does a lot more than that. Way too much to elaborate on in this post.

To make a long story short, Pex can automatically unit test your parameterized methods with different kind of inputs ( without resorting to brute-force). What's great about this, is that it works in combination with Code Contracts, and can actually suggest contracts for you.

The <a href="http://research.microsoft.com/en-us/projects/pex/documentation.aspx">documentation pages</a> includes a <a href="http://research.microsoft.com/en-us/projects/pex/pexandcontracts.docx">nice tutorial</a> on how to use the power of Pex in combination with Code Contracts.
<h2>4. Split more complicated statements into multiple lines.</h2>
Although simple, quite effective.

A lot of concerns surrounding the static checker's inability to prove something are easily solved by this one. Some developers have the tendency of joining multiple statements in one big statement. This can improve readability and shorten your code files, but also confuse you about which statement the static checker is complaining about.

Split your big statement into several lines, and it will become more clear which method the static checker is complaining about.

For example:
<pre class="prettyprint"><code>StringHelper.CleanUrl( new PageManager("BasePage.aspx").GetFullUrl()) ;</code></pre>

has a lot of places where there could be a nullreference occurring. Splitting this into several statements would make this a lot easier for you to see what method gives you the problem. ( This is actually general debugging advice, not just for the static checker )
<h2>Conclusion</h2>
A lot of static checker warnings will easily be solved by following one or more of the solutions provided here, others will require more digging through your own code. There will be times when you will still need to Assume some conditions, as the static checker will never be able to statistically proof every line of code you write.

However, hopefully these guidelines will aid you in proving your contracts to the static checker, further improving your code base with better documented behavior, promises and expectations.
