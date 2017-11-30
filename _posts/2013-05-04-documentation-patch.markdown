---
layout: post
title:  "Linux Kernel - Documentation Patch"
date:   2013-05-04
categories: article
---

Documentation Patch (What have I gotten myself into?)
Trying to remove a broaken link... to embed or not to embed (and the importance of running checkpatch.c)

My inspiration for this patch came from simply exploring the kernel documentation and bumping into a couple of links that failed to work, but what a can of worms I opened.

My first idea was to import the documents so that they could be managed in the kernel, the kernelhub website (http://www.kernelhub.org/?msg=264068&p=2) has a good summary of the patch series (spinics.net (http://www.spinics.net/lists/linux-doc/msg10724.html) also have a decent summary):
This patch series

        1. adds "the perfect patch" doc.
        2. adds "submission format" doc.
        3. update refs to perfect-patch.
        4. fix link in perfect patch.
        5. update refs to sub-format.
        6. fix source ref in perfect patch.
        7. reformat submission format doc.
        8. move other documents into patch sub directory.

or:
        Documentation: Adding "The Perfect Patch" by Andrew Morton
        Documentation: Adding "Linux Kernel Patch Submission Format"
        Documentation: Replacing references to broken perfect patch URL
        Documentation: Replacing reference to broken perfect patch URL
        Documentation: Replacing reference to broken submission format URL
        Documentation: Updating a broken link in "the perfect patch"
        Documentation: Reformatting "Linux Kernel Patch Submission Format"
        Documentation: Move other patch related document

This proposal sparked a few interesting responses (https://lkml.org/lkml/2013/5/24/2) :) ... none of them good :( ... with Rob Landley (https://lkml.org/lkml/2013/5/24/2) asking the poin question "What's in this that _isn't_ in SubmittingPatches? What does having this second file add?" (http://www.spinics.net/lists/linux-doc/msg10735.html) to which I must admit there was no good answer... I had mindlessly imported the document wholesale and (well not mindlessly, I did read it first and there was plenty of good general advice, but) there was no specific requirements stated there that were not in SubmittingPatches.txt. A few other bits of Robs advice rang true, but I felt I should have waited untill they were in the kernel before making the changes... but alas they have to be there to be updated, such is life.

So my final patch ended up just being a simple url update:

TODO: Dave Jones (https://lkml.org/lkml/2013/5/23/456) also notes a couple of broaken links and outdated infos

An old reference to: ftp://ftp.kernel.org/pub/linux/kernel/v2.6/snapshots/

And some other text in the file where the regex s/bitkeeper/git/ would do wonders

Thanks Dave :) Links are going on the todo list.
