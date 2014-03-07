---
layout: post
title: "Auto mocking with AutoMoq"
description: ""
category: tech
tags: [development,testing,C#,dotnet]
---
{% include JB/setup %}

AutoMoq is a nice little package I came across today. The AutoMoq home page describes it as follows:

<blockquote>AutoMoq is an &quot;auto-mocking&quot; container that creates objects for you. Just tell it what class to create and it will create it.</blockquote>

Why is this useful? Consider the following scenario. We have a BananaCakeFactory class, that relies on a Banana Repository. Here is the constructor:

{% raw %}<script type="syntaxhighlighter" class="brush: csharp"><![CDATA[public BananaCakeFactory(IBananaRepo bananaRepo);]]></script>{% endraw %}

If we want to run Unit Tests on methods in BananaCakeFactory, we will have to write all the mocking code to mock IBananaRepo. That's fine.

Time goes on, our app grows more complex. Now our BananaCakeFactory needs to Sugar Repo as well...

{% raw %}<script type="syntaxhighlighter" class="brush: csharp"><![CDATA[
public BananaCakeFactory(IBananaRepo bananaRepo, ISugarRepo sugarRepo);
]]></script>{% endraw %}

We add mocks for our Sugar Repo, and update all our constructor calls for BananaCakeFactory. When we have a large solution, time spent adding new mocks and updating constructors really adds up. AutoMoq can take the pain away.

Here is an example of how we use AutoMoq to create a mocked class, ready for testing: 

{% raw %}<script type="syntaxhighlighter" class="brush: csharp"><![CDATA[
// init
mocker = new AutoMoqer();

// mock a Banana Cake Factory
var cakeFac = mocker.Create<BananaCakeFactory>();

// inject our IRepo
mocker.GetMock<IBananaRepo>();

// do work
var result = cakeFac.Bake();
]]></script>{% endraw %}

Now if we want to add our Sugar Repo, all that's needed is the following additional line:

{% raw %}<script type="syntaxhighlighter" class="brush: csharp"><![CDATA[mocker.GetMock<ISugarRepo>();]]></script>{% endraw %}

Happy Coding!

<h2>Reference URLs</h2>
<li><a href="https://github.com/darrencauthon/AutoMoq">AutoMoq Homepage</a></li>
<li><a href="http://www.nuget.org/packages/AutoMoq/">AutoMoq Nuget Package</a></li>
