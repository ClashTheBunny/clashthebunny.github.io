---
id: 15
title: Setting the date of a UNIX/Linux machine over the network with just ssh
date: 2010-03-09T16:42:47+00:00
author: randall
layout: post
guid: http://clashthebunny.wordpress.com/2010/03/09/setting-the-date-of-a-unixlinux-machine-over-the-network-with-just-ssh/
permalink: /2010/03/setting-the-date-of-a-unixlinux-machine-over-the-network-with-just-ssh/
image:
  - ""
seo_follow:
  - 'false'
seo_noindex:
  - 'false'
dsq_thread_id:
  - "4229418978"
categories:
  - Linux
tags:
  - ssh date linux unix set remote
---
I run into machines from time to time that do not have any method of network time setting installed that I know has an incorrect date or time.<!--more-->They usually do have ssh though, so this is my solution from the host with the bad time:


  
`` sudo date `ssh <hostWithGoodClock> "date +%m%d%H%M%C%y.%S"` ``
  
or if you are doing this from a computer with ssh access to the device:
  
`ssh %lt;hostWithBadClock> "sudo date $(date +%m%d%H%M%C%y.%S)"`

Note, this has issues when it comes to time zones.  Do this only with servers in the same timezone.