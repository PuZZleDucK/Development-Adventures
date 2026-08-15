---
layout: post
title: "Installing a custom rom on the Huwei U8510 ... using nothing but my linux!"
excerpt: "All the instructions for rooting and installing custom roms for the Huwei U8510 seem to be for windows users, so here it is the world exclusive ;) Huwei U8510 rooting and custom rom guide for linux! Sanity checks: 1. Android SDK & tools…"
date: 2012-04-23 02:33:00 +0000
blogger_published_at: "2012-04-23T02:33:00.003-07:00"
categories: article
title-image: no_image.svg
source_url: "https://android-development-adventures.blogspot.com/2012/04/installing-custom-rom-on-huwei-u8510.html"
---

{% raw %}
<div dir="ltr" style="text-align: left;" trbidi="on">
All the instructions for rooting and installing custom roms for the Huwei U8510 seem to be for windows users, so here it is the world exclusive ;) Huwei U8510 rooting and custom rom guide for linux!<br />
<br />
Sanity checks:<br />
1. Android SDK &amp; tools installed (i.e. "adb" and "fastboot" work)... check!<br />
2. Prerequisite knowledge: you knew "adb" and "fastboot" were terminal commands... check!<br />
3. "adb devices" returns the u8510 and only the u8510 (just a precaution i like to take)... check.<br />
<br />
Roms:<br />
-&nbsp;<a href="http://www.mediafire.com/?78oha1q7z5cag16">Spanish</a><br />
- <a href="http://forum.xda-developers.com/showthread.php?t=1393756&amp;page=4%20%20-%20http://blog.podtwo.com/android/rom/de-branded%20ROM%20for%20Huawei%20U8510%20%5Bgingerbread%5D.html">deBranded</a><br />
-&nbsp;<a href="http://www.mediafire.com/?ju91cdq19y46noo">Zad</a> <br />
<br />
Recovery (kudos: <a href="http://androidforums.com/members/lebo.html">Lebo</a>):<br />
- <a href="http://www.mediafire.com/?irr4cc14xy9ygs9">Recovery</a><br />
<br />
Other info tying it all together but with busted links (kudos: <a href="http://android.stackexchange.com/users/11257/leandros">Leandros</a>):<br />
<a href="http://android.stackexchange.com/questions/18158/how-do-i-root-a-huawei-x3">http://android.stackexchange.com/questions/18158/how-do-i-root-a-huawei-x3</a><br />
<br />
Step 1: Download roms and Recovery.<br />
Step 2: Replace SD card (goldcard may be required... I'm using mine), copy roms onto sd card.<br />
Step 3: prepare phone, go to settings &gt; apps and disable "fastboot".<br />
Step 4: Unplug USB. <br />
Step 5: Boot into fastboot mode (reboot and hold Volume Down + Power).<br />
Step 6: Plug in usb. Verify fastboot with "sudo fastboot devices". Your devices serial number may be "??????????"... mine was.<br />
Step 7: "sudo fastboot erase recovery".<br />
Step 8: "sudo fastboot flash recovery recovery.img".<br />
Step 9: "sudo fastboot reboot" ... Steps 7, 8 and 9 should result in "OKAY" feedback.<br />
[Optional]. Backup. and Wipe.<br />
Step 10: Start flashing roms... WOOT!!!<br />
<br />
Step 11: Smile smugly to yourself because you did it and didn't need to touch those nasty Windows and you'll never again have to see that ugly Vodaphone logo.<br />
<br />
<br />
Rom1: De-branded<br />
Faster, cleaner UI, nicer lock screen, faster camera, Android 2.3.5, 2.6.35.7-perf kernel, SU, navigation and market.<br />
<br />
Rom2: Eclipse<br />
Feels faster again, same lock screen, same Android and kernel, english-as-second-language, androidlost, goomanager, market, brut-maps, SU, xda-app, nice status bar update (numeric battery display).<br />
<br />
Rom3: Zad<br />
Custom boot animation &lt;3, same lock, Android 2.3.3, same kernel, horrible jellybean app drawer (can't wait to drop ADW over this ugly sucker), astro, market, xda, brut, SU, Titanium, goomanager, cpu master and MerkaMarket (Spanish market?). ADW improves things somewhat.<br />
<br />
Rom4: Spanish<br />
Fail to install... maybe one day,<br />
<br />
but for now,<br />
<br />
&nbsp;the winner is:<br />
<br />
...<br />
<br />
Eclipse... only the Zeam version... I never use it (except for in demos), but I like Zeam. :D<br />
<br />
<br />
<br />
<br />
<br />
<br /></div>
{% endraw %}
