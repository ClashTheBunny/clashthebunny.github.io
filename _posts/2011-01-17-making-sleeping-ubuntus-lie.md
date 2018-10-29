---
id: 60
title: Making Sleeping Ubuntus Lie
date: 2011-01-17T19:31:44+00:00
author: randall
layout: post
guid: http://clashthebunny.wordpress.com/?p=60
permalink: /2011/01/making-sleeping-ubuntus-lie/
jabber_published:
  - "1295292706"
reddit:
  - 'a:2:{s:5:"count";s:1:"0";s:4:"time";s:10:"1297712828";}'
categories:
  - Linux
---
Ubuntu stopped letting me force the display off while in X11 with a change to Gnome Screensaver. <!--more--> I used to just run 

_xset dpms force off_ but that doesn&#8217;t work anymore. Here&#8217;s a workaround that also works as a &#8220;command&#8221; on compiz. I have it set to the top left of my screen, so I just move my mouse over there and it turns off the screen.
  
<!--more-->


  
`sleep 1; xset dpms force off; gnome-screensaver-command -i & while xset q | grep -iq "Monitor is Off"; do sleep 10; done; killall gnome-screensaver-command`

You can also put this in a script that you can execute from the command line:

<pre>#!/bin/bash

sleep 1
xset dpms force off
gnome-screensaver-command -i &
while xset q | grep -iq "Monitor is Off"
do
    sleep 10
done
killall gnome-screensaver-command
</pre>

It will exit at most 10 seconds after you move your mouse or hit a key. Let it exit or your screensaver will be inactive for the rest of that session. Or until you run the script again and let it exit. Or until you just run _killall gnome-screensaver-command_.