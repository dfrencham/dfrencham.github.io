---
layout: post
category : tech
title: "Animating Aurelia"
tags : [tech,aurelia,javascript,css]
---
{% include JB/setup %}

Have you heard of Aurelia? It's Rob Eisenberg's new framework. If you travelled forward in time two years and wrote a framework based on cutting edge tech, Aurelia would be the result. Aurelia is built on technology so new that the standards haven't been ratified yet. I'm talking ES6, ES7, transpiling, a proper module loader, lambda expressions (arrow functions), computed properties, and more.

<img class="img-responsive blog-img " src="{{ site.url }}/assets/images/aurelia-logo.png" alt="Aurelia" />

Now let's use this massively powerful framework to animate a few boxes.

<!--more-->

## Applying CSS transitions to New DOM Elements in Aurelia ##

What we are going to do is this:

> Have new databound elements fade in as they are added to the DOM, using CSS transitions.

To achieve our goal, we're going to need to install Aurelia's animation library. Open a command prompt and add it to your project as follows:

<pre class="line-numbers"><code>
$> jspm install aurelia-animator-css
</code></pre>

If you haven't seen jspm before, check it out. It isn't limited to jspm packages. Jspm can also install and manage npm packages, as well as pulling modules down from github repositories.

### CSS Transitions ###

If you're unfamiliar with CSS transitions - don't worry. They are straight forward. You define the key points in the transition - the starting state (0%) and the end state (100%). Apply CSS styles for those key points. The browser will extrapolate the rest. Here is the definition for our "fade-in" transition:

<pre class="line-numbers"><code class="language-css">
@keyframes fade-in {
  0%   { opacity: 0; }
  100% { opacity: 1; }
}
/* for compatibility with older browsers */
@-webkit-keyframes fade-in{
  0%   { opacity: 0; }
  100% { opacity: 1; }
}</code></pre>

To use our new transition we need to create a CSS class to apply to our new DOM elements:

<pre class="line-numbers"><code class="language-css">
.fade-in-box {
  -webkit-animation: 0.5s fade-in;
  animation: 0.5s fade-in;

  border: 1px solid black;
  background: yellow;
}</code></pre>

### Aurelia .js class ###

This is our view model.

<pre class="line-numbers"><code class="language-javascript">
import {CssAnimator} from 'aurelia-animator-css';

export class ListExample{

  heading = 'List Example';

  listItems = [
    { listItem: 'pencils', qty: 2 },
    { listItem: 'glue', qty: 1 },
  ];

  addListItem() {
     this.listItems.push({listItem: 'packing tape',  qty: 1 });
  }

}</code></pre>

The code above creates a list of items and a button - which we bind our view to. Notice the nice ES6 syntax?

### Aurelia .html view ###

This is our view.

<pre class="language-markup"><code class="language-markup">
&lt;template&gt;
  &lt;section&gt;
    &lt;h2&gt;${heading}&lt;/h2&gt;

    &lt;div&gt;&lt;button click.trigger="addListItem()"&gt;Add List Item&lt;/button&gt;&lt;/div&gt;

    &lt;div role="grid"&gt;
      &lt;div repeat.for="row of listItems" style="display: flex;"&gt;
        &lt;div style="flex: 1 auto;" class="fade-in-box" &gt;${row.listItem}&lt;/div&gt;
        &lt;div style="flex: 1 100px;" class="fade-in-box" &gt;${row.qty}&lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/section&gt;
&lt;/template&gt;</code></pre>

In the view, we've defined a list, and used "repeat.for" to bind it to our view model list items. The button is bound to addListItem().

## Click! ##

When the user clicks the button, the following events occur:

1. The view model method *addListItem()* adds a new item to the list.
2. Aurelia observes the new item being added, and triggers a DOM insert to add it to the grid.
3. The Aurelia-animator module observes the DOM addClass event, and begins the *fade-in* animation.

Pretty cool, huh? Some subtle, unobtrusive animations can really make a page seem slick. Just don't go overboard, or you'll take us back to the hellish days of animated gif wall papers.

### Aurelia-animator Supported Events ###

The DOM events supported by Aurelia's animator are:

- **move** - Move element
- **enter** - Element enters view
- **leave** - Element leaves view
- **removeClass** - Class removed from DOM
- **addClass** - Class added to DOM

## Links ##

- [Aurelia](http://aurelia.io/)
- [Aurelia-animator](https://github.com/aurelia/animator-css)
