---
layout: post
title: "Ubuntu app showdown"
excerpt: "I think there's about 4 days left in the Ubuntu app showdown and my entry is finally starting to resemble a functional program :) For my entry I have chosen to write a GUI wrapper around the Android sdk tools, mainly adb, but also the sdk…"
date: 2012-07-05 21:59:00 +0000
blogger_published_at: "2012-07-05T21:59:00.001-07:00"
categories: article
title-image: no_image.svg
source_url: "https://android-development-adventures.blogspot.com/2012/07/ubuntu-app-showdown.html"
---

{% raw %}
<div dir="ltr" style="text-align: left;" trbidi="on">
<div>
I think there's about 4 days left in the Ubuntu app showdown and my entry is finally starting to resemble a functional program :)<br />
For my entry I have chosen to write a GUI wrapper around the Android sdk tools, mainly adb, but also the sdk manager and the virtual machine manager. It's called ADBassist, check out the code: https://code.launchpad.net/~puzzleduck/adbassist/trunk.<br />
At the moment all it does is download the sdk, update them to get adb, run adb and create a new tab for each device... now I've got to keep the tabs up to date (I will probably poll adb every 5-10 seconds for a device list for now, but monitoring dbus for USB events would probably be a smarter/better way to go).<br />
I will also spend the weekend setting up the individual device tabs with useful functions such as an apk and other files upload facilities (adb push), file download and backup (adb pull), device status (adb shell df -h for example) and advanced functions like reboot and mock locations... maybe even screenshots and/or remote control.<br />
Finally a release mode testing would be super... In turn each possible avd is downloaded, a virtual machine created for each, apk is installed and run on the virtual device in turn... It's a nice dream anyway :) <br />
Oh, and in other "big" news ADBassist now has a logo... Bask in the glory:<br />
<br />
<img height="200" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjQlVDOWXJoNKvXEuuIeHvJTreuwjRtWgCGPFUdPEOaO4ueaWkFmqqS79WmnHaMSAnbzY7vdWbPrC5GmplLA95ZdAzwGdo417EetHH16h0ZyCcFHGwjLP1rqfHceBnju5uWsmWIB8yxSOnX/" width="200" /></div>
</div>
{% endraw %}
