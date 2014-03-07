---
layout: post
title: "Entity Tags (Etags)... what they are and why they rock"
description: ""
category: tech
tags: [development,caching]
---
{% include JB/setup %}

<p>Last week, a coworker asked me a question about Etags. I'd never heard of of Etags - in spite of them being around since 1999!</p> 

<blockquote><p>In a nutshell, an etag is an identifier assigned to a specific version of a hosted object by a webserver - for the purposes of caching. </p></blockquote>

<p>Etags operate as follows:</p> 

<ol>
<li>1. A client sends a HTTP request for an object.</li>
<li>2. The server returns the object to the client, along with the ETag value (as an Etag field, eg: <i>ETag: "686897696a7c876b7e"</i>). The client caches the object.</li>
<li>3. When the client needs re-display the object, a it sends a HTTP request along with a If-None-Match field, eg: <i>If-None-Match: "686897696a7c876b7e"</i>. </li>
<li>4. If the If-None-Match field matches the Etag for the resource, a HTTP 304 (NOT MODIFIED) response is sent. If the If-None-Match field does not match, a HTTP 200 (OK) response is sent along with the updated resource.</li>
</ol>

<p>This mechanism allows objects to be transmitted only when they have changed - saving on bandwidth. What's even better, is that Etags are on be default in IIS and Apache and supported by all major browsers. Sounds like a win-win!</p>

<h2>Notes</h2>
<ul>
<li>Etags work with all major browsers (IE8+,FF,Chrome,Safari)</li>
<li>Etags work along side other cache headers (such as expiry)</li>
<li>Etags are usually generated based on timestamps</li>
<li>Etags can be used as a tracking mechanism</li>
</ul>

<h2>References</h2>  
<ul>   
 <li><a href="http://www.w3.org/1999/04/Editing/#2">Detecting the Lost Update Problem Using Unreserved Checkout (W3C 1999)</a> </li>    
 <li><a href="http://en.wikipedia.org/wiki/HTTP_ETag">Wikipedia ETag article</a> </li> 
 <li><a href="http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html">HTTP 1.1 If-None-Match</a></li>
</ul>