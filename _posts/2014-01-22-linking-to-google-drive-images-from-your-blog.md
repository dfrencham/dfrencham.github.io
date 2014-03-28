---
layout: post
title: "Linking to Google Drive images from your Blog"
description: ""
category: tech
tags: [development,blogging,javascript]
---
{% include JB/setup %}

<p>A good number of us have content stored on google drive. Wouldn't it be handy if we could reference that content in our blog posts? Good news, you can!</p>
<h2>Steps</h2>
1.Go to your google drive account.
2.Ensure the folder the item is in, is shared (use the option <i>Anyone who has the link can view</i>).
3.Share the item (use the same option as above). Copy the "Link to Share" link.
4.Paste the link in the linkifier below
5.Copy the link produced, and insert it into your blog via any of your usual methods
<!--more-->
{% raw %}
<h2>How it works</h2>
A link with this format: <i>https://drive.google.com/file/d/\[id number\]/edit?usp=sharing</i> is transformed using a regular expression, to this format: 
	<pre>http://drive.google.com/uc?export=view&amp;id=(id number)</pre>

<h2>Google Drive Linkifier</h2>
<div id="gdrive_linkifier" style='background-color:#F6FCD4; border:1px solid #FFFACD; padding:7px;'>
<div id='gdrive_messages-error' style='display: none;' class='alert alert-danger'></div>
<div id='gdrive_messages-success' style='display: none;' class='alert alert-success'></div>
Paste your Google Drive Link Here <input type='text' id='gdrive_input' style='width:200px;' /> <br />
<small>Your link should have the format: https://drive.google.com/file/d/(id number)/edit?usp=sharing</small>
</div>
<br />
<p>Please post a comment if you have any problems.</p> 
<script src='http://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js?ver=1.7.2' type='text/javascript'></script>
<script>
$(document).ready(function () {

$('#gdrive_input').on('input',function() {

$('#gdrive_messages-error').hide();
$('#gdrive_messages-success').hide();
var link = $('#gdrive_input').val();
var fixedLink = 'http://drive.google.com/uc?export=view&id=';

var patt= new RegExp("https://drive\.google\.com/file/./(.*)/.*");
var result = patt.exec(link);

if (link != '') {
 if ((result != null) && (result.length === 2)) {
  $('#gdrive_messages-success').text('Link found: ' + fixedLink + result[1]);
  $('#gdrive_messages-success').show();
 }
 else
 {
  $('#gdrive_messages-error').text('Link not valid');
  $('#gdrive_messages-error').show();
 }
}
    
});
});
</script>
{% endraw %}