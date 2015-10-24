---
layout: post
title:  "JavaScript Everywhere!"
date:   2015-10-24 11:05:00
categories: javascript
---
For past few years, JavaScript has taken over the programming world like no other language before. From something like this:

{% highlight javascript %}

alert('How are you today?');

{% endhighlight %}

to something as complex as:

{% highlight javascript %}

var http = require("http");
var server = http.createServer(function(request, response) {
  response.writeHead(200, {"Content-Type": "text/html"});
  response.write("working");
});

server.listen(80);
console.log("Server is listening");

{% endhighlight %}

Today, you can create a web app, mobile app and a desktop app using JavaScript, HTML and CSS. That means if you spend sometime mastering JavaScript, you are not restricted in developing for a particular device. Apart fron powering web applications and web apps, JavaScript is powering text editors, pre processing tools, mobile apps and much more.

Beginning with the web space, we have seen countless frameworks and libraries coming up in the JS world recently. Starting with [jQuery](http://jquery.org). 