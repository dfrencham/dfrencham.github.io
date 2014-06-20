---
layout: post
title: "Get Angular Running in 5 minutes "
description: ""
category: tech
tags: [development,single page app,javascript]
---
{% include JB/setup %}

Want to try some [Angular](https://angularjs.org/) development? Need to get a dev environment set up? With a couple of automation tools, I'll have you up and going in 5 minutes.

<!--more-->

##Prerequisites##

You need the following two apps installed:

1. Git
2. [Chocolately](https://chocolatey.org/) package manager.

##Instructions##

We are going to use the [Angular Seed](https://github.com/angular/angular-seed) project template.

Fire up a command window, then run the following commands:

	cd\git   (change this to the folder you intend to use) 
	git clone https://github.com/angular/angular-seed.git
	cd angular-seed
	cinst nodejs.install
	"c:\Program Files\nodejs\npm" install
	"c:\Program Files\nodejs\npm" start

You should now be able to open **http://localhost:8000/app/** in your web browser.

What just happened?

	git clone https://github.com/angular/angular-seed.git

This cloned Angular Seed to your local drive.

	cinst nodejs.install

Chocolatey installed nodejs and npm (node package manager).

	"c:\Program Files\nodejs\npm" install

NPM found the node based project in your current folder, and automatically installed the node dependencies.

	"c:\Program Files\nodejs\npm" start

NPM launched the node.js instance, which happens to be available at **http://localhost:8000/app/**

Too easy! :)

For a full run down of how to use the template, go here: [angular-seed on github](https://github.com/angular/angular-seed).
