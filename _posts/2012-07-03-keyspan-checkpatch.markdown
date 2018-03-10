---
layout: post
title:  "Linux Kernel - Keyspan Checkpatch"
date:   2012-07-03
categories: article
title-image: tux.png
---

#### fixes for drivers/usb/serial/keyspan.c

From a search of Linuses git tree (http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/log/?qt=grep&q=ben+minerds) here is a nice little summary of the changes made in their final form. I also seem to remember having some issues (http://marc.info/?l=linux-kernel&m=134201585403638&w=2) with email formatting and having my emails mangled by gmail. I have just recently discovered the Eudyptula Challenge which may help with these kind of issues in the future, but I'll discuss that another time when I cover Eudyptula challenge one and how I may have inadvertanty sent HTML emails to the Linux Mailing list.

        Age "Commit message" (Author) Files Lines
        2012-07-17 "USB: serial: keyspan: Removed unrequired parentheses." (Ben Minerds) 1 -1/+1
        2012-07-17 "USB: serial: keyspan: Removed trailing whitespace." (Ben Minerds) 1 -1/+1
        2012-07-17 "USB: serial: keyspan: Fixed space near open parenthesis." (Ben Minerds) 1 -1/+1
        2012-07-17 "USB: serial: keyspan: Fixed space around equals." (Ben Minerds) 1 -1/+1
        2012-07-17 "USB: serial: keyspan: Fix spacing around conditional." )Ben Minerds) 1 -9/+9

... but it wasn't always so simple ...

The origional submission was pedanticaly and rediculiously verbose, with 21 seperate patches. The statistics were good, before: 19 errors, 69 warnings. After: total: 0 errors, 16 warnings. Unfortunatly the way I had put together the patch series wasn't the easiest to digest. I had kept each change seperate after recently learning about bisecting the kernel isolating changes. Of course the chances of introducing a bug that would crash the kernel in the documentation is pretty minimal, so my caution was a bit over zelious.

```bash
$ ls *.patch | xargs grep -h PATCH
Subject: [PATCH 01/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 02/21] USB: serial: Changes to conform with checkpatch.sh script. spaces required around '?' and ':'
Subject: [PATCH 03/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 04/21] USB: serial: Changes to conform with checkpatch.sh script. spaces required around '='
Subject: [PATCH 05/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 06/21] USB: serial: Changes to conform with checkpatch.sh script. white space around '('
Subject: [PATCH 07/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 08/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 09/21] USB: serial: Changes to conform with checkpatch.sh script. spaces required around '?' and ':'.
Subject: [PATCH 10/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 11/21] USB: serial: Changes to conform with checkpatch.sh script. parentheses not required
Subject: [PATCH 12/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 13/21] USB: serial: Changes to conform with checkpatch.sh script. spaces required around '?' and ':'.
Subject: [PATCH 14/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 15/21] USB: serial: Changes to conform with checkpatch.sh script. spaces required around '?' and ':'.
Subject: [PATCH 16/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 17/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 18/21] USB: serial: Changes to conform with checkpatch.sh script. spaces required around '?' and ':'.
Subject: [PATCH 19/21] USB: serial: Changes to conform with checkpatch.sh script. spaces required around '?'.
Subject: [PATCH 20/21] USB: serial: Changes to conform with checkpatch.sh script. space before tabs.
Subject: [PATCH 21/21] USB: serial: Changes to conform with checkpatch.sh script. trailing whitespace.
```

The responces from the mailing list was well put by Sergei Shtylyov (https://lkml.org/lkml/2012/5/10/111) that patch 2 could be merged with patches "9, 13, 15, 18, and 19 which claim to do the same thing". Alan Cox (https://lkml.org/lkml/2012/5/10/121) even suggested merging them all into one. So the next version breaks up the fixes into patches containing just that type of fix. So all the "space near (" fixes were in one patch, and all the "spaces around :?" in another

```bash
$ ls *.patch | xargs grep -h PATCH
Subject: [PATCH 1/6] USB: serial: Changes to conform with checkpatch. - space before tabs
Subject: [PATCH 2/6] USB: serial: Changes to conform with checkpatch. - spaces around '?' and ':'.
Subject: [PATCH 3/6] USB: serial: Changes to conform with checkpatch. - space around '='.
Subject: [PATCH 4/6] USB: serial: Changes to conform with checkpatch. - space near open parenthesis '('.
Subject: [PATCH 5/6] USB: serial: Changes to conform with checkpatch. - trailing whitespace.
Subject: [PATCH 6/6] USB: serial: Changes to conform with checkpatch. - parentheses not required.
```

28th may - The final version needed to be rebased off of Felipe Balbis (https://github.com/felipebalbi) tree (https://lkml.org/lkml/2012/9/10/316). Maybe I should have checked the maintainers first, but it seemed to be no big deal and just another thing to be aware of while roaming around the Kernel at random. I also don't remember accidently "trying to introduce" the Authored-By (https://lkml.org/lkml/2012/5/9/237) tag, thanks Rich. There seems to be a quite funnly long standing joke about the number of tags in the Kernel, funny stuff.

```bash
$ ls *.patch | xargs grep -h PATCH
Subject: [PATCH 0/6] USB: serial: Changes to conform with checkpatch.
Subject: [PATCH 1/6] USB: serial: Removed space before tabs.
Subject: [PATCH 2/6] USB: serial: Fix spacing around conditional.
Subject: [PATCH 3/6] USB: serial: Fixed space around equals.
Subject: [PATCH 4/6] USB: serial: Fixed space near open parenthesis.
Subject: [PATCH 5/6] USB: serial: Removed trailing whitespace.
Subject: [PATCH 6/6] USB: serial: Removed unrequired parentheses.
```
Then Greg KH pointed out (https://lkml.org/lkml/2012/7/11/345) that "Normally the 0/6 email is a text summary, and maybe the diffstat of the whole patchset. But not a patch itself" which is certainly correct, and I'm not sure what I was thinking at the time as I didn't see to do this on the eirlier versions of the patch, I guess I left writing this a bit too long.
