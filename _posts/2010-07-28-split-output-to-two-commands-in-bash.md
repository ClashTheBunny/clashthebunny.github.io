---
id: 27
title: Split output to two commands in bash
date: 2010-07-28T15:30:31+00:00
author: randall
layout: post
guid: http://clashthebunny.wordpress.com/?p=27
permalink: /2010/07/split-output-to-two-commands-in-bash/
jabber_published:
  - "1280331032"
reddit:
  - 'a:2:{s:5:"count";s:1:"0";s:4:"time";s:10:"1295464555";}'
sh5vp-video:
  - ""
sh5vp-youtube_video_id:
  - ""
sh5vp-vimeo_video_id:
  - ""
sh5vp-width:
  - "640"
sh5vp-height:
  - "480"
sh5vp-preload:
  - 'yes'
sh5vp-autoplay:
  - 'no'
sh5vp-loop:
  - 'no'
categories:
  - Linux
---
**UPDATE 2 (2012-12-06):** I think this was wrong until now, but I have it figured out. See the updated post below.

I have long wondered how to split output to two commands in bash, I figured it out today.
  
<!--more-->


  
[bash]
  
cat file.txt | tee >(head) | tail
  
[/bash]
  
will give both the head and the tail of the file. I have always wanted to run the output of a command through a Y into two separate commands and this is so logical that I can&#8217;t believe that I had never heard of it before

This uses the beautiful bash feature of creating a file descriptor from a programs output or input.  I love this feature and it allows for so much. Head will get the first 10 or fewer lines and tail will get the last 10 or fewer lines.