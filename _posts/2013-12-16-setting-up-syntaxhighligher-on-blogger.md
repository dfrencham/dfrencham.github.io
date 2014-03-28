---
layout: post
title: "Setting up SyntaxHighligher on Blogger"
description: ""
category: tech
tags: [development,blogging,syntax highligher]
---
{% include JB/setup %}
As a technical blogger, one of my first questions was: <blockquote>how do I add syntax highlighting to my blog?</blockquote> I discovered  [Syntax Highlighter](http://alexgorbatchev.com/SyntaxHighlighter/). 
Syntax Highlighter is a fantastic tool. It looks good, it is easy to set up, and it supports a large number of languages.
<!--more-->

I am going to walk you through setting up Syntax Highlighter on the Blogger platform. The first thing you need to do, is go to your blog template, and choose "Edit HTML".

We are going to use the CDN (shared hosting) version of the scripts. Paste this code block in the HEAD section:

{% raw %}<script class="brush: xml" type="syntaxhighlighter"><![CDATA[
<link href="http://alexgorbatchev.com/pub/sh/current/styles/shCore.css" rel="stylesheet" type="text/css" />
<link href="http://alexgorbatchev.com/pub/sh/current/styles/shThemeDefault.css" rel="stylesheet" type="text/css" />
<script src="http://alexgorbatchev.com/pub/sh/current/scripts/shCore.js" type="text/javascript" />
<script src='http://alexgorbatchev.com/pub/sh/current/scripts/shAutoloader.js' type='text/javascript'/>
<script src='http://alexgorbatchev.com/pub/sh/current/scripts/shBrushJScript.js' type='text/javascript'/>
<script src='http://alexgorbatchev.com/pub/sh/current/scripts/shBrushXml.js' type='text/javascript'/>
<script src='http://alexgorbatchev.com/pub/sh/current/scripts/shBrushCSharp.js' type='text/javascript'/>]]></script>{% endraw %}

This gives us the Syntax Highligher styles, core scripts, and support for HTML/C#/Javascript. If you need additional languages, simply copy the last line, and change the .js to one of the <a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/brushes/">available brushes</a>.

Next, go to the bottom of the page, above the  tag. Add the following:

{% raw %}<script class="brush: xml" type="syntaxhighlighter"><![CDATA[
&lt;script type='text/javascript'&gt;
    // code highlight
    SyntaxHighlighter.config.bloggerMode = true;
    SyntaxHighlighter.all()
&lt;/script&gt;]]></script>{% endraw %}

This causes Syntax Highlighter parse your code samples. Syntax highligher is now configured. So, how do we post code samples?

There are a number of ways, but I have found this is the most reliable way:

{% raw %}<pre class="brush: xml;">&lt;script type="syntaxhighlighter" class="brush: xml"&gt;&lt;![CDATA[ 
 // Your code goes here! 
]]&gt;&lt;/script&gt;
</pre>{% endraw %}
Note that the brush type needs to match one of the brushes you added in the .js imports further up. 

Why do we use that odd CDATA syntax? It turns out that embedding code in code (such as this page) is harder than you might think. The browser will try to interpret the code. We can change all the code characters to character codes - but that alters the original code and quickly gets tiresome.

Using &lt;script&gt; tags allows syntax highlighter to find your code sample. CDATA is a special tag that prevents XML/HTML parsers (such as your browser) from trying to parse that code block.

If you do use Syntax Highlighter, make sure you provide a link to the <a href="http://alexgorbatchev.com/SyntaxHighlighter/">author's site</a>, as he provides it free of charge.

**Reference URLs**
* Syntax Highlighter - [http://alexgorbatchev.com/SyntaxHighlighter/](http://alexgorbatchev.com/SyntaxHighlighter/)
* What is CData? - [http://stackoverflow.com/questions/7092236/what-is-cdata-in-html](http://stackoverflow.com/questions/7092236/what-is-cdata-in-html)