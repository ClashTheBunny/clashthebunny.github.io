---
id: 239
title: Gmail IMAP Folders in Different Languages
date: 2012-03-22T11:32:03+00:00
author: randall
layout: post
guid: http://clashthebunny.mason.ch/?p=239
permalink: /2012/03/gmail-imap-folders-in-different-languages/
dsq_thread_id:
  - "4229419159"
categories:
  - Life
---
I had a project where I needed to retrieve messages from my IMAP mailbox of my Bulgarian gmail.  The problem is that I didn&#8217;t know what to call it or how to figure out what to call it.  I tried the equivilent in English &#8220;All Mail&#8221;, folder not found.  I tried the name of the mailbox in Bulgarian in UTF-8 &#8220;Цялата поща&#8221;, that just gave an error.  I found out that there is some sort of encoding for IMAP for international boxes from a [bug report](https://bugzilla.mozilla.org/show_bug.cgi?id=432060){.broken_link} for Thunderbird, a great open-source email client.  It said that I needed to look at [RFC3501](http://www.faqs.org/rfcs/rfc3501.html) to see the standard for how the mailbox should be encoded.  It turns out that it&#8217;s a variant of UTF-7, the 7-bit universal format. <!--more--> It took a while to get a converter going, but it looks a little like this:

[shell]

echo <UTF-8 string> | iconv -f utf-8 -t utf-7 | sed -e &#8216;s/+/\&/g&#8217; -e &#8216;s/\>\([^-]\)/-\1/g&#8217; -e &#8216;s#/#,#g&#8217;

[/shell]

so, for my &#8220;All Mail&#8221; box, which is Цялата поща in Bulgarian, I would do:

[shell]

echo Цялата поща | iconv -f utf-8 -t utf-7 | sed -e &#8216;s/+/\&/g&#8217; -e &#8216;s/\>/-/g&#8217; -e &#8216;s#/#,#g&#8217;

[/shell]

So, I needed to update my getmail configuration, replacing &#8220;All Mail&#8221; with the string that resulted: &#8220;&BCYETwQ7BDAEQgQw- &BD8EPgRJBDA-&#8220;.  This turned out to have some weird issues since the characters that the modified UTF-7 was using were control characters in sed, so my sed command became a little more complicated:

[shell]

sed -i -e &#8220;s/All Mail/$(echo -n Цялата поща | iconv -f utf-8 -t utf-7 | sed -e &#8216;s/+/\\\&/g&#8217; -e &#8216;s/\>\([^-]\)/\\-\1/g&#8217; -e &#8216;s#/#,#g&#8217;)/g&#8221; getmail_clashthebunny

[/shell]