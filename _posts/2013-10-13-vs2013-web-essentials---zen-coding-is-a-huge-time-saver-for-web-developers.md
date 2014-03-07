---
layout: post
title: "VS2013 Web Essentials   Zen Coding is a huge time saver for web developers"
description: ""
category: tech
tags: [development,html,visual studio,javascript]
---
{% include JB/setup %}

As a web developer, I have regularly found myself needing to type a large amount of HTML layout code. Your page starts to grow, and your eyes begin to glaze over as you type DIV after DIV.

Enter <a href="https://code.google.com/p/zen-coding/">Zen Coding</a>. In a nutshell, ZenCoding is a set of editor extensions, allowing a developer to use shorthand for common tasks. Microsoft have incorporated these extensions into <a href="http://visualstudiogallery.msdn.microsoft.com/56633663-6799-41d7-9df7-0f2a504ca361">Web Essentials</a> for Visual Studio 2013.

I can't overstate how awesome this feature is. For example, if I type:

{% raw %}<script class="brush: xml" type="syntaxhighlighter"><![CDATA[
div
]]></script>{% endraw %}

...and then hit the tab key, I get:

{% raw %}<script class="brush: xml" type="syntaxhighlighter"><![CDATA[
<div>
</div>
]]></script>{% endraw %}

A div has been added for me. But what if I need to add a CSS Id?

{% raw %}<script class="brush: xml" type="syntaxhighlighter"><![CDATA[
div#mainContent

// tab...
<div id="mainContent">
  </div>
]]></script>{% endraw %}

We can add a CSS class too:

{% raw %}<script class="brush: xml" type="syntaxhighlighter"><![CDATA[
div#mainContent.redbox

// tab...
<div id="mainContent" class="redbox">
</div>
]]></script>{% endraw %}

Maybe we need some test data to check our layout? Zen even supports Lorem Ipsum!

{% raw %}<script class="brush: xml" type="syntaxhighlighter"><![CDATA[
div>lorem

// tab...
<div>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit fusce vel sapien elit in malesuada semper mi, id sollicitudin urna fermentum ut fusce varius nisl ac ipsum gravida vel pretium tellus.
</div>
]]></script>{% endraw %}

This part is cool. What if we want 3 table rows, each with 2 columns? (yes, I know, you all use pure CSS now - not tables)..

{% raw %}<script class="brush: xml" type="syntaxhighlighter"><![CDATA[
table>tr*3>td*2

// tab...
<table>
<tr>
        <td></td>
        <td></td>
    </tr>
<tr>
        <td></td>
        <td></td>
    </tr>
<tr>
        <td></td>
        <td></td>
    </tr>
</table>
]]></script>{% endraw %}

If you find it isn't working after installing Web Extensions, make sure you are using the release copy of Visual Studio 2013 (the latest version of Web Extensions doesn't work with VS2013 pre-release). Let me know if you find more handy short cuts.<br />
