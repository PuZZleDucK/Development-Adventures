---
layout: post
title: "These messes I&#39;m in and out of."
excerpt: "It's been a while since my last post so I thought it was about time to do a quick roundup of the current (shambolic, but fortunately improving) state of development in my apps. Stalin Phone... Where it all started. I started working on a…"
date: 2012-02-29 00:28:00 +0000
blogger_published_at: "2012-02-29T00:28:00.001-08:00"
categories: article
title-image: no_image.svg
source_url: "https://android-development-adventures.blogspot.com/2012/02/these-messes-i-in-and-out-of.html"
---

{% raw %}
<div dir="ltr" style="text-align: left;" trbidi="on"><div><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjZmdT_7oC3ShhaqbEcyH993iY-q0PT_2jIBTWfMETIUPkuXmDbooN352Tnd4u176JeXMK_RJnCy0vGTXtYTfYicOEvapBC5hbvXbiXY30_Pn6m5k9osNjMXAlqbuj3yu35wJwnK8DAnPpn/" imageanchor="1" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjZmdT_7oC3ShhaqbEcyH993iY-q0PT_2jIBTWfMETIUPkuXmDbooN352Tnd4u176JeXMK_RJnCy0vGTXtYTfYicOEvapBC5hbvXbiXY30_Pn6m5k9osNjMXAlqbuj3yu35wJwnK8DAnPpn/" /></a>It's been a while since my last post so I thought it was about time to do a quick roundup of the current (shambolic, but fortunately improving) state of development in my apps.<br />
<br />
<br />
Stalin Phone... Where it all started.<br />
<br />
I started working on a video recording version of Stalin Phone some time ago and got caught in a bit of a snag. It seems that video recording is not possible without a VideoView object from the layout (failed attempts included declaring a new video view in code). This puts me in a bit of a pickle as Stalin Phone runs in the background with no UI. I have come up with a couple of possible solutions to this since I last worked on it. One possibility is to use a custom toast notification with an embedded video view, possibly this might fall when the toast is dismissed but I could probably set it's timeout high enough to outlast your average call. Secondly (and preferably) I could try replacing the current notification with a custom status bar notification... the snag here being that I am not yet sure how much raw access to the custom layout I will have (i.e. Can I directly grab the video view or do I only get access to a handler).<br />
<br />
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiBO0AZZFkhuXhGbx2sJJy4_Zrf42EH9RE5nHyXGQRC-pt57gjYNQCEIz-e2SgeNrqMeyRKET-f6MRf8v2IVpU614PKy916wool-fzPZS3GuK5OimqiNLVp7kOVz87-R3CSVOUTqb3MqtKi/" imageanchor="1" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" height="200" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiBO0AZZFkhuXhGbx2sJJy4_Zrf42EH9RE5nHyXGQRC-pt57gjYNQCEIz-e2SgeNrqMeyRKET-f6MRf8v2IVpU614PKy916wool-fzPZS3GuK5OimqiNLVp7kOVz87-R3CSVOUTqb3MqtKi/" width="200" /></a>This leads into another couple of side projects I started to explore the world of status bar notifications.<br />
<br />
Photo-A-Day... Simple notifications.<br />
This is probably the most likely project to finish first as I haven't so much hit a snag as I have got distracted.<br />
<br />
I now have the framework for the app set up, just need to add shared preferences storage (started), resume on power up and a little bit of cut and polish :p <br />
<br />
<br />
<br />
Motivational Puzzles demonic offspring: Pseudomonarchia Daemonum...<br />
&nbsp;I've also refocused motivational puzzle into a demonic motivational piece based off the demonic book of names... Maybe an angelic counterpart should be on the books for the future.<br />
<br />
<br />
The experimental Puzzle Cam has also halted in its tracks for the time being as the rom I'm running (BCM) has flakey camera support at the moment. Last time I was working on it I was close to cracking the camera preview frame (fuzzy green images in triplicate), but not quite yet and I'm not sure when I'll pick this one up again. Low priority.<br />
<br />
<br />
Finally we come to my two babies: Target Live Wallpaper and Mou5e Live Wallpaper.<br />
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgdaJKbpRpA-ZtPPz0Jo_Zw9yUn20sDQoJYOKqEYPitPGKTRssEbknu2RW8VQ96ZmsVnY3cp958Zy_d3vc3VZZSVw-jgSVKkn98RyFg4dxVkBYP2onpxWpgg4wl6phLOjtaBgSemB7oJVAd/" imageanchor="1" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" height="200" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgdaJKbpRpA-ZtPPz0Jo_Zw9yUn20sDQoJYOKqEYPitPGKTRssEbknu2RW8VQ96ZmsVnY3cp958Zy_d3vc3VZZSVw-jgSVKkn98RyFg4dxVkBYP2onpxWpgg4wl6phLOjtaBgSemB7oJVAd/" width="200" /></a>Not much happening on the mouse lwp, but target lwp is almost exploding with new features. Well at least two anyway. I made some progress with the fireworks module, fireworks now explode better and fall back towards earth after explosion.<br />
I'm most excited about the last feature (mainly because I just nailed it about an hour ago): importing custom models... For now it's importing a hard coded sample, but once I integrate xml parsing it should be a sinch to import any model from Google <strike>sketchpad</strike>sketchup to use as the 3d model. Woot!<br />
<br />
Also just added "orbitals" checkout the video below to see the demo :D<br />
<div class="separator" style="clear: both; text-align: center;"><iframe allowfullscreen='allowfullscreen' webkitallowfullscreen='webkitallowfullscreen' mozallowfullscreen='mozallowfullscreen' width='320' height='266' src='https://www.youtube.com/embed/eIL6J8yq86o?feature=player_embedded' frameborder='0'></iframe></div><br />
<br />
<br />
<br />
</div></div>
{% endraw %}
