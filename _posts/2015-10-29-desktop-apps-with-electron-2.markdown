---
layout: post
title:  "Desktop apps with Electron - 2"
author: "Vishnu"
date:   2015-10-29 08:00:00
categories: javascript
---
##Creating multiple windows in your electron app

In my [last post](http://neoelemento.com/blog/2015/10/25/desktop-apps-with-electron-1/), I wrote about how to get a basic Electron app up and running. But what do you do if you want a multiple window app? For example, if you want to display preferences once you select from the app menu.


{% highlight javascript %}
// app.js
var app = require('app');
var BrowserWindow = required('browser-window');
app.on('ready', function() {
  var mainWindow = new BrowserWindow({
    width: 800, // specifying the height
    height: 600 // and width of the app window
  });
  mainWindow.loadUrl('file://' + __dirname + '/modules/main/main.html');
  mainWindow.openDevTools(); // Optional. Used for debugging purposes.
  
  // for new window to display options
  var optionsWindow = new BrowserWindow({
    width: 500,
    height: 500,
    show: false
  });
  optionsWindow.loadUrl('file://' + __dirname + 'options.html')
});

{% endhighlight %}