---
id: 226
title: Internet Speed
date: 2012-02-29T13:46:21+00:00
author: randall
excerpt: "My internet speed is way faster than my phone's memory card speed."
layout: post
guid: http://clashthebunny.mason.ch/?p=226
permalink: /2012/02/internet-speed/
categories:
  - Life
---
**UPDATE:** I think that one of the problems was a USB 1.1 port on my computer.  Does everybody know that some of the ports on their computer are USB 1.1 and some are USB 2.0 and you can usually get better performance from one or the other? It&#8217;s a good thing to know if you use flash drives and usb hard drives.

* * *My phone&#8217;s memory card erased itself the other day so I&#8217;ve been restoring some files from a backup.</p> 

I&#8217;m at work, my backup is at home, and my phone is plugged into my work computer.

I started the restore and then went to look at other things on my TODO list.

It&#8217;s a big file so I didn&#8217;t give it much thought until I looked at my computer status: [<img class="alignnone size-full wp-image-227" title="sawtoothInternet" src="http://clashthebunny.mason.ch/wp-content/uploads/2012/02/sawtoothInternet.png" alt="" width="84" height="24" />](http://clashthebunny.mason.ch/wp-content/uploads/2012/02/sawtoothInternet.png)

Yellow is network activity and orange is disk activity.  The yellow says that the internet can take a break every once in a while while the orange says that the disk is working at a constant rate.  This means that my phone&#8217;s memory card is the bottle neck.  This means that if I were to want to choose the fastest method of listening to music or watching a movie on my phone, it would be better to play it directly from the internet than to save to my memory card and play it back from the file.  This would be the same as comparing purchasing a movie from iTunes or watching it from Netflix.  It would be faster to watch the same movie from Netflix than to purchase it from iTunes, sync, and watch it.

A couple rough numbers.  The peek numbers on the internet are very roughly 1.9 MB/s (big B means bytes).  The average throughput including my card is 989 kB/s.  That&#8217;s less than half my actual download speed and much less than if the disk wasn&#8217;t the bottleneck.  With this same transfer going, I tried out the same files to make sure that something wans&#8217;t going on with my backup server.  I saw peak transfers of around 2.3 MB/s.

Some technical notes:

The transfer chain was like this: backup server&#8217;s hard drive -> backup server -> ethernet -> home router -> internet -> work router -> ethernet -> work computer -> USB port -> Eye-Fi SD card converter -> SD to MicroSD converter -> Wintech Class 10 MicroSD card.

The card I have has some bad reviews on throughput: <http://www.newegg.com/Product/Product.aspx?Item=20-161-411>, maybe I just need a new card.

I&#8217;ll probably update later on what&#8217;s the deal with this.