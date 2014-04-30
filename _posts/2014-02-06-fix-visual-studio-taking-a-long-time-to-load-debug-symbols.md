---
layout: post
title: "Fix Visual Studio taking a long time to load debug symbols"
description: ""
category: tech
tags: [development,visual studio,argh,C#]
---
{% include JB/setup %}

I lost a good couple of hours tracking this one down. If Visual Studio is taking a very long time to load debug symbols when debugging (think 5 minutes to 30 minutes), try this... 

**Delete all break points** (Debug - &gt; Delete All Break Points). 

Sometimes something small like this can be a lot more frustrating than a big issue. Hopefully this saves someone from going crazy.
