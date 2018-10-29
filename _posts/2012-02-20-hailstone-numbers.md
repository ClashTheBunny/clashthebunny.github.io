---
id: 152
title: Hailstone Numbers
date: 2012-02-20T17:46:10+00:00
author: randall
layout: post
guid: http://clashthebunny.mason.ch/?p=152
permalink: /2012/02/hailstone-numbers/
image:
  - ""
seo_follow:
  - 'false'
seo_noindex:
  - 'false'
categories:
  - Programming
tags:
  - Programming Praxis
  - prompt
---
I just did the most recent Programming Praxis, [Hailstones](http://programmingpraxis.com/2012/02/17/hailstones/)

Here&#8217;s my solution in Erlang.
  
<!--more-->


  
[erlang]
  
-module(hailstones).
  
-export([hailseq/1,hail/1]).

hail(1) -> 1;
  
hail(N) when N > 1, (N rem 2) == 0, is_integer(N) -> N div 2;
  
hail(N) when N > 1, (N rem 2) > 0, is_integer(N) -> 3*N+1.
  
hailseq(1) -> 1;
  
hailseq(N) when is_integer(N) -> io:fwrite(&#8220;~w &#8220;, [N]), hailseq(hail(N)).
  
[/erlang]