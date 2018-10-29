---
id: 272
title: Upgrade armel to armhf
date: 2014-03-22T14:36:47+00:00
author: randall
layout: post
guid: http://clashthebunny.mason.ch/?p=272
permalink: /2014/03/upgrade-armel-to-armhf/
dsq_thread_id:
  - "4228165695"
categories:
  - Life
---
I&#8217;m doing this in my chroot on my OUYA:

`sudo apt-get update && sudo apt-get dist-upgrade<br />
sudo apt-get install debootstrap</p>
<p>sudo debootstrap --arch=armhf --download-only --include=openssh-client,openssh-server jessie ./bootstrap-armhf http://ftp.debian.org/debian/</p>
<p>sudo dpkg --add-architecture armhf</p>
<p>mkdir -p archives-apt/partial<br />
mkdir -p archives-dpkg/partial<br />
rm archives-*/*deb</p>
<p>sudo apt-get install -d -y -o Dir::Cache::Archives=./archives-apt apt:armhf<br />
sudo apt-get install -d -y -o Dir::Cache::Archives=./archives-dpkg dpkg:armhf</p>
<p>ls archives-dpkg/*deb | grep -v ^archives-dpkg/dpkg | xargs sudo dpkg -i<br />
ls archives-dpkg/*deb | grep ^archives-dpkg/dpkg | xargs sudo dpkg -i<br />
sudo  dpkg -i archives-apt/*.deb</p>
<p>sudo dpkg -i ./bootstrap-armhf/var/cache/apt/archives/*deb</p>
<p>aptitude search -F "%p" --disable-columns '~i!~M' | sed -e 's/:armel//g' | xargs sudo apt-get install</p>
<p>sudo apt-get -f install</p>
<p>sudo apt-get update && sudo apt-get dist-upgrade</p>
<p>dpkg -l | grep -i armel | grep -v :armel | grep -v ^rc | awk '{print $2}' | xargs sudo apt-get install -y</p>
<p>sudo apt-get autoremove<br />
` 
  
think about reinstalling these programs:
  
`dpkg -l | grep ^rc | awk '{print $2}' | grep -v :armel`

then:
  
`dpkg -l | grep -i ^rc | awk '{print $2 ":" $4}' | xargs echo sudo apt-get purge`