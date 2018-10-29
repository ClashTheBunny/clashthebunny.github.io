---
id: 37
title: 'rsync&#8217;ing NFS shares'
date: 2010-10-05T16:32:57+00:00
author: randall
excerpt: "One time I was moving all of an application's data to a new NFS server where I worked.  I did an rsync to copy everything over, then took the application offline to do a re-sync of just the changes that happened during the first rsync.  I do, because it took forever and I had to explain the downtime to the CEO.  This is how I should have done it."
layout: post
guid: http://clashthebunny.wordpress.com/?p=37
permalink: /2010/10/rsyncing-nfs-shares/
jabber_published:
  - "1286296377"
reddit:
  - 'a:2:{s:5:"count";s:1:"0";s:4:"time";s:10:"1295464554";}'
dsq_thread_id:
  - "4228220343"
categories:
  - Linux
---
One time I was moving all of an application&#8217;s data to a new NFS server where I worked. I did an rsync to copy everything over, then took the application offline to do a re-sync of just the changes that happened during the first rsync. I do, because it took forever and I had to explain the downtime to the CEO.
  
<!--more-->


  
I think about it every once in a while now because I backup my work computer to a SMB share at work with rsync and it takes forever. The reason is that all of the data has to be transmitted over the network if you don&#8217;t use either ssh or a standard rsync server.

What I did when I transferred the data over was:
  
`mount oldNFSserver:/data /data2<br />
rsync -avH /data2/ /data/<br />
[take down web application]<br />
rsync -avH /data2/ /data/`
  
Which transferred all of the data again.

What I should have done was:
  
`rsync -avH oldNFSserver:/data/ /data/<br />
[take down web application]<br />
rsync -avH oldNFSserver:/data/ /data/`
  
Which would have only transferred only the delta over ssh the second time.

I&#8217;ve been thinking about this because I am starting to set up a redundant NAS at my house and my parent&#8217;s house. This way if either are damaged by flood/lightning/fire I will have a copy of my data _somewhere_.