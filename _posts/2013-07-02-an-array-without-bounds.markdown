---
layout: post
title:  "An Array Without Bounds"
date:   2013-07-02 19:37:56 +1100
categories: article
---

I just wanted to write a short piece about a horrifying little trick in java I learnt from trawling through the back catalogue of Dr. Heinz K's newsletter. I highly recommend skimming the article list for interesting titles at a minimum.

Anyhow, in article 162... (you need to scroll down to near the end where he's telling us what not to do :p) he mentions a technique of looping through an array without bounds checking the loop. Instead the exception mechanism is hijacked and used to exit the loop when the inevitable ArrayOutOfBounds exception is raised by simply executing a break to exit the infinite loop.

He implies in the article that in early versions of java this was faster than the standard for loop idiom, but that this is not true for modern JVMs. The article is a few years old now but at least preliminary testing on my pc seems to indicate that the exception-hijacking-idiom is once again faster... at least on 64bit Linux. Anyhow, the technique is not advised for every day use but is an interesting tool to have in the box.

Image: http://upload.wikimedia.org/wikipedia/commons/7/77/Bale_hooks_and_baling_twine.jpg
