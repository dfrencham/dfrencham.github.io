---
layout: post
title: "Developing for Screen Readers is a special kind of hell"
category : tech
tags : [aria,accessibility,screen reader,JAWS,NVDA]
---

Picture the scenario.... your manager asks you add support for assistive technologies to your shiny new SPA (Single-Page-App is a development pattern that can be roughly described as a highly responsive javascript explosion). Your client wants to implement the W3C-AA Accessibility Standard.

You are going to pull out your IDE, make a few tweaks to the app, and the screen reader will happily read your web application out to appriciative users.

After adding a few ARIA tags, you fire up a screen reader....

<!--more-->

You'll likely discover that your screen reader will miss half of your content, read out things it shouldn't, and spend a surprising amount of time making funny noises on punctuation symbols.

### The Internet Sucks for Blind People ###

Until I started running a screen reader over a few random sites, I had no idea just how much the internet *really really sucks* for visually impaired users.

This is a rough diagram showing how the internet feels if you are blind:

<div class="post-image">
<img src="{{ site.url }}/assets/images/assistive-technology.jpg" alt="How the internet feels for blind people" />
</div>

Most websites are not structured properly (those H1, H2, H3 tags do have more importance than just changing text size). They have terrible keyboard navigation (you'd be surprised at just how many websites have buttons and widgets only bound to mouse clicks).

If you are blind, you get the double punch of a website you can't navigate coupled with an ascii waterfall coming from your speakers.

### How a Developer Expects a Screen Reader to Work ###

As a developer, logically you think a screen reader is going to read out the visible content - and maybe you can slip some extra content in with a call like this:

    // don't actually try this, because it won't work
    document.accessibility.readtext("Your phone number has been updated");

Maybe you need to hide something from a screen reader, can you do something like this?

    // no, you can't. Not yours.
    $('pointless-visual-widget').prop("screen-reader-visible","false");

Sadly, like most things designed by large committees, *it doesn't quite work that way*.


### How Screen Readers Actually Work ###

A screen reader doesn't read the web site directly. Your web browser presents an accessibility API. This API presents various events and meta data that a assistive technologies can work with.

In theory, there is a set of agreed upon accessibility standards (ARIA) that a developer can leverage whilst writing code. With a few extra attributes you can leverage to make the screen reader behave as expected. 

In reality it is more like this:

You can use (x) accessibility feature if
- the browser in question supports it
- the browser will actually present it via the accessibility API in your scenario
- the screen reader implements that particular feature
- the screen reader feels like reading it (screen readers seem to get into odd states and not work properly after working perfectly a few minutes prior)

There is no way to directly tell a screen reader to "just go ahead and read this" with Javascript. The closest you can get is to dynamically insert objects into the DOM with role=alert set. That gave me the following result (with NVDA):

- Firefox read it twice
- Chrome read it some times, but not consistantly
- IE ignored it completely, unsurprisingly

Guh.

All this could be avoided if Browser devs simply gave us a way to raise accessibility events directly via Javascript. 


https://developer.mozilla.org/en-US/docs/Mozilla/Accessibility/Accessibility_architecture

