---
layout: post
category : tech
tags : [regex,regular expressions]
---
{% include JB/setup %}

Being able to write Regex (otherwise known as Regular Expressions) is a skill every developer should learn. You can use Regex to find very specific text strings, to reformat files, and to do very specific replacements.

When combined with a good text editor, [you are unstoppable](https://xkcd.com/208/).

<!--more-->

Those with \*nix experience are generally familier with regex, as they have the useful sed/awk commands at their fingertips. Those with perl experience tend to use regex to the point of insanity ("hey look at what I can do in a single expression!").Microsoft scoped developers, on the other hand, generally only learn about regex when they are watching a coworker doing a large number of replacements in a file - *and gets a nice surprise when all of those replacements are done in one hit*.

Regex support used to be pretty rare in most text editors/IDEs, but these days pretty much any editor other than Notepad.exe probably supports it. Here's some details:

- [Notepad++](http://blog.creativeitp.com/posts-and-articles/editors/understanding-regex-with-notepad/comment-page-1/)
- Sublime Text uses [Boost regular expression syntax](http://www.boost.org/doc/libs/1_47_0/libs/regex/doc/html/boost_regex/syntax/perl_syntax.html)
- [XCode](http://roadfiresoftware.com/2013/12/replacing-regular-expressions-in-an-xcode-project/)

Visual Studio was - until recently - a special case. All versions up to and including Visual Studio 2010 used a bizarre custom syntax that was originally aimed at C++ developers. If you are using 2010 or earlier... *don't bother using the built in regex*. Just don't. Copy your text to a different editor with *sane* regex support and run your expressions there.

Visual Studio 2013 on the other hand (and 2012) both have [proper regex support](http://msdn.microsoft.com/en-us/library/2k3te2cs.aspx).

As much as I love Regex, there is one thing you should be aware of. Regex can be hard. Very hard. Sure, a basic find/replace is easy... but at some point you will want to do more. You'll end up with character classes to restrict matched characters, you'll want to negate matches, you'll learn what the term *greedy* means in the context of pattern matching.

<div class="post-image">
<a class="fancybox" href="http://imgs.xkcd.com/comics/regex_golf.png"><img class="img-responsive img-thumbnail" src="http://imgs.xkcd.com/comics/regex_golf.png" alt="Regex golf" /></a><br />
</div>

When you are writing and debugging expressions, keep this in mind:

>It should not take longer to write and debug your expression than it would take you to manually do the find/replace.

If it is taking that long - stop.

Here is a practical example of using regex:

###Transform comma delimited data into SQL inserts###

I've used this exact case many times before. Given some comma delimited data, like this:

	34930,Bob,Jones,23 Developer St,Baker
	94084,Anne,Jackson,11 Side St,Plumber
	90385,Jean,Gray,5 Hollywood Place,Engineer

We can use a regular expression to transform it into SQL inserts.

Here is our match expression:

	^(.*),(.*),(.*),(.*),(.*)\r\n

Here is our replace rule:

	INSERT INTO ContactDetails (CardNumber,FirstName,LastName,Address,Occupation) Values ($1,'$2','$3','$4','$5')\r\n
	
Here is the result:

	INSERT INTO ContactDetails (CardNumber,FirstName,LastName,Address,Occupation) Values (34930,'Bob','Jones','23 Developer St','Baker')
	INSERT INTO ContactDetails (CardNumber,FirstName,LastName,Address,Occupation) Values (94084,'Anne','Jackson','11 Side St','Plumber')
	INSERT INTO ContactDetails (CardNumber,FirstName,LastName,Address,Occupation) Values (90385,'Jean','Gray','5 Hollywood Place','Engineer')


<div class="post-image">
<a class="fancybox" href="{{ site.url }}/assets/images/regex.png"><img class="img-responsive img-thumbnail" src="{{ site.url }}/assets/images/regex.png" alt="Regex window in Visual Studio" /></a><br />
</div>

### Guides for getting started ###

- [Regular Expressions Quickstart](http://www.regular-expressions.info/quickstart.html)
- [Wikipedia Article on Regex](http://en.wikipedia.org/wiki/Regular_expression)
- [30 minute regex tutorial](http://www.codeproject.com/Articles/9099/The-Minute-Regex-Tutorial)
- [Perl Regex Tutorial](http://perldoc.perl.org/perlretut.html)


