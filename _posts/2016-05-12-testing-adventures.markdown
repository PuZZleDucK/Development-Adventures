---
layout: post
title: "Testing Adventures"
excerpt: "Building a verification toolkit ... ... without a software department - Part 1 Binary image verification For larger companies and manufacturers who already heavily invest in R&D and software development there is a low barrier to produce…"
date: 2016-05-12 08:45:00 +0000
blogger_published_at: "2016-05-12T08:45:00.001-07:00"
categories: article
title-image: no_image.svg
source_url: "https://android-development-adventures.blogspot.com/2016/05/testing-adventures.html"
---

{% raw %}
<div dir="ltr" style="text-align: left;" trbidi="on">
<h4 style="text-align: left;">
Building a verification toolkit ...</h4>
<h4 style="text-align: left;">
... without a software department - Part 1</h4>
<h2 style="text-align: left;">
Binary image verification</h2>
<div style="text-align: left;">
For larger companies and manufacturers who already heavily invest in R&amp;D and software development there is a low barrier to produce in-house binary image writing and verification tools. However for the new entrant into the industry and entities who do not invest in producing their own software the prospect of commissioning custom software could seem a daunting challenge. However many may not be aware that the state of the art in cryptographic verification is right at our fingertips in an open source format which is itself verifiable and inspectable.<br /><br />OpenSSL provides a plethora of hash based verification methods and with very few exceptions (and combining it with crc32) can be used to verify the binary images for almost all jurisdictions. If you are part of a regulatory body considering a new hash technique, ensuring it is available in OpenSSL makes sure you'll always have an independent, verifiable reference implementation that is easy for manufacturers to verify their implementations against and easy for test labs to start utilizing.<br /><br />The following bash functions can be put into your bashrc file to allow very convenient verification of binaries:<br />&nbsp;</div>
<h2 style="text-align: left;">
Image Verification Functions</h2>
<blockquote class="tr_bq">
function hmac-sha1 () { date &gt; hmac-sha1.txt; openssl dgst -sha1 -mac HMAC -macopt hexkey:0000 $@ | tee -a hmac-sha1.txt; }<br /><br />function sha1 () { date &gt; sha1.txt; openssl dgst -sha1 $@ | tee -a sha1.txt; }<br /><br />function crc () { date &gt; crc.txt; crc32 $@ | tee -a crc.txt; }</blockquote>
<div style="text-align: left;">
<br /><br />so now we can just run the commands (replacing &lt;file-name&gt; with the aquired image):</div>
<blockquote class="tr_bq">
<div style="text-align: left;">
sha1 &lt;file-name&gt;<br />hmac-sha1 &lt;file-name&gt;<br />crc &lt;file-name&gt;</div>
</blockquote>
<div style="text-align: left;">
<br />and we get the output files below containing timestamps and the cryptographic digest of the supplied file:</div>
<blockquote class="tr_bq">
sha1.txt<br />hmac-sha1.txt<br />crc.txt</blockquote>
<div style="text-align: left;">
<br />&nbsp;</div>
<div style="text-align: left;">
This give us timestamped logs of the digest values that allow us to verify binary images for the majority of jurisdictions around the world. Next in the series we'll look into tools for acquiring the binary images from a given device.<br />&nbsp;</div>
<div style="text-align: left;">
<br /></div>
<h2 style="text-align: left;">
OpenSSL Resources</h2>
<div style="text-align: left;">
<a href="https://www.openssl.org/docs/apps/openssl.html">OpenSSL Command</a>&nbsp;</div>
<div style="text-align: left;">
<a href="https://www.openssl.org/docs/apps/sha.html">Digest Function</a><br /><br /></div>
</div>
{% endraw %}
