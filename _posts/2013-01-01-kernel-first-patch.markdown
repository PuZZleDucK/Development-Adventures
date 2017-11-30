---
layout: post
title:  "Linux Kernel - Intro and Setup"
date:   2013-01-01
categories: article
---


##### It's all Greg K-H's fault

Greg Kroah-Hartman started all this by giving such an inspiring talk about four years ago, which motivated me to do something I'd been meaning to do for years... get a patch into the Linux Kernel.
https://www.youtube.com/watch?v=LLBrBBImJt4

Getting started in comedy drivers... step one: go streight to the penguins source and clone Linus's tree:

git clone https://github.com/torvalds/linux.git

Now lets get out beyond the bleeding edge of the current stable kernel and add the Linux Next branches, this seems to be the preffered route into the kernel for usb driver related submissions. I have begun to realise that some other high level maintainers have their own "linux next" like trees, so do a quick bit of research into what branch or repository is appropriate for your patch.

```bash
git remote add linux-next git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git
git fetch linux-next
git fetch --tags linux-next
```

To avoid getting too far behind and increasing the possibility of creating conflicts with others working on the same part of the kernel, when returning to a possibly stale tree (24 hrs? haha) we should always update our tree:

```bash
git remote update
```

For my own records at least my configuration while submitting to the linux kernel is as follows.

```bash
# :: Setup git user ::
git config "user.name" "Ben Minerds"
git config --global "user.email" puzzleduck@gmail.com
```

Other useful long term resources:

If you run Linux... your already here :D file:///usr/src/
