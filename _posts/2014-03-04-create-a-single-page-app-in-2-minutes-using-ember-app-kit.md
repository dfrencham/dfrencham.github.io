---
layout: post
title: "Create a Single Page App in 2 Minutes using Ember App Kit"
description: ""
category: tech
tags: [development,spa,single page app,javascript,ember]
---
{% include JB/setup %}

Single Pages Apps (SPAs) are the current flavour of the month. They have seemingly appeared from nowhere, but now it seems like every developer is talking about them. Wikipedia describes this pattern as follows:<br />
<blockquote class="tr_bq">
<div style="background-color: white; font-family: sans-serif; font-size: 13px; line-height: 19.200000762939453px; margin-bottom: 0.5em; margin-top: 0.4em;">
A&nbsp;<b>single-page application</b>&nbsp;(<b>SPA</b>), also known as&nbsp;<b>single-page interface</b>&nbsp;(<b>SPI</b>), is a&nbsp;<a href="http://en.wikipedia.org/wiki/Web_application" style="background-image: none; background-position: initial initial; background-repeat: initial initial; color: #0b0080; text-decoration: none;" title="Web application">web application</a>&nbsp;or&nbsp;<a class="mw-redirect" href="http://en.wikipedia.org/wiki/Web_site" style="background-image: none; background-position: initial initial; background-repeat: initial initial; color: #0b0080; text-decoration: none;" title="Web site">web site</a>&nbsp;that fits on a single&nbsp;<a href="http://en.wikipedia.org/wiki/Web_page" style="background-image: none; background-position: initial initial; background-repeat: initial initial; color: #0b0080; text-decoration: none;" title="Web page">web page</a>&nbsp;with the goal of providing a more fluid user experience akin to a desktop application.</div>
<div style="background-color: white; font-family: sans-serif; font-size: 13px; line-height: 19.200000762939453px; margin-bottom: 0.5em; margin-top: 0.4em;">
In a SPA, either all necessary code –&nbsp;<a href="http://en.wikipedia.org/wiki/HTML" style="background-image: none; background-position: initial initial; background-repeat: initial initial; color: #0b0080; text-decoration: none;" title="HTML">HTML</a>,&nbsp;<a href="http://en.wikipedia.org/wiki/JavaScript" style="background-image: none; background-position: initial initial; background-repeat: initial initial; color: #0b0080; text-decoration: none;" title="JavaScript">JavaScript</a>, and&nbsp;<a class="mw-redirect" href="http://en.wikipedia.org/wiki/CSS" style="background-image: none; background-position: initial initial; background-repeat: initial initial; color: #0b0080; text-decoration: none;" title="CSS">CSS</a>&nbsp;– is retrieved with a single page load,<sup class="reference" id="cite_ref-Flanagan2006_1-0" style="line-height: 1em; unicode-bidi: -webkit-isolate;"><a href="http://en.wikipedia.org/wiki/Single-page_application#cite_note-Flanagan2006-1" style="background-image: none; background-position: initial initial; background-repeat: initial initial; color: #0b0080; text-decoration: none; white-space: nowrap;">[1]</a></sup>&nbsp;or the appropriate resources are dynamically loaded and added to the page as necessary, usually in response to user actions.&nbsp;</div>
</blockquote>
In my experience they offer some advantages over traditional apps:<br />
<ul style="list-style-type: disc;">
<li>Very responsive</li>
<li>Rapid development time</li>
<li>Data is usually provided via a REST API - making integration to other systems easy</li>
</ul>
along with some disadvantages:<br />
<ul style="list-style-type: disc;">
<li>Usually implemented with javascript (with all baggage it brings, such as horrendous function passing syntax everywhere)&nbsp;</li>
<li>Can be harder to debug - you can end up in dependency hell</li>
<li>Common tasks such as continuous integration is harder than with more mature patterns such as MVC (example: making javascript unit tests play nice with TFS).</li>
</ul>
The high responsiveness alone makes SPAs worth of investigating. Responsive web apps == &nbsp;happy users!<br />
<h2>
Ok, I'm sold. What now?</h2>
So, where do we start? The SPA (and javascript) community is fast moving place. I have lost track of the number of new templates and libraries in use... Knockout, Angular, Durandal, Ember, Bootstrap, JQuery, etc, etc, etc. You can attempt to roll your own SPA from the ground up, or you can use a ready made project template - such as the <a href="https://github.com/stefanpenner/ember-app-kit">Ember App Kit</a>.<br />
&nbsp;Ember App Kit gives you:<br />
<ul style="list-style-type: disc;">
<li>A nice project structure</li>
<li>GruntJS automation for minification, compilation, and deployment</li>
<li>Ember SPA framework - with Handlebar templates, routing, controllers</li>
<li>Unit tests with QUnit</li>
<li>Javascript 6 (ECMA6) modules (this is very very cool- a tool called a <i>transpiler</i>&nbsp;is used. ECMA6 takes Javascript into the realm of modern languages with a proper object model and sane module support)</li>
</ul>
Esentially, this kit gives us an out-of-the-box ready to go application. You can use it as a starting point to customise and build on for your own application.  <br />
<h2>
Let's get started</h2>
<div>
<ol style="list-style-type: decimal;">
<li>Go to Ember App Kit's git hub page and either&nbsp;<a href="https://github.com/stefanpenner/ember-app-kit/archive/master.zip">Download the template</a>&nbsp;(and unzip it to a folder) or clone the repo.<br />&nbsp;</li>
<li>Install Node JS if you don't already have it. Ember App Kit uses Grunt to automate various tasks, and grunt uses Node.<br />&nbsp;</li>
<li>Once you have Node, open a command window and do a global install of Grunt using the following command:<br />
<code>npm install -g grunt-cli</code><br />&nbsp;
</li>
<li>Now install Bower. Bower is a client side package manager:<br />
<code>npm install -g bower</code><br />&nbsp;
</li>
<li>Still in the commend window, change to your new folder from step one. Install your npm dependencies:<br />
<code>npm install</code><br />&nbsp;</li>
<li>Install your Bower dependencies:<br />
<code>bower install</code></li>
</ol>
<h2>
Now run the app</h2>
</div>
<div>
The following command will run your app in debug mode <b>and</b>&nbsp;watch for file changes (restarting the app as needed):&nbsp;</div>
<code>grunt server</code>
<br />
<div>
<br />
...and this is the result:</div>
<div>
<span style="font-family: monospace;"><br /></span>
</div>
<div>
<br /></div>
<img src="http://drive.google.com/uc?export=view&amp;id=0BzEmq4lTwA-sMG5HZUxVX01YVU0" />  <br />
<h2>
Where to now?</h2>
<div>
You now have a fully working Ember app ready to build on. Check out the Ember Sherpas guide as well as the getting started guide to get some in depth detail on some of the features mentioned above. Be sure to leave a comment if you find this helpful (or not so helpful).</div>
<h2>
References</h2>
<ul style="list-style-type: disc;">
<li><a href="https://github.com/stefanpenner/ember-app-kit">Ember App Kit</a> </li>
<li><a href="http://iamstef.net/ember-app-kit/guides/getting-started.html">Ember App Kit Getting Started Guide</a></li>
<li><a href="http://embersherpa.com/articles/introduction-to-ember-app-kit/">Ember Sherpas - Introduction to Ember App Kit</a></li>
<li><a href="http://emberjs.com/">EmberJS</a> </li>
<li><a href="http://gruntjs.com/">GruntJS</a> </li>
</ul>
