---
layout: post
title:  "Linux Kernel - Belkin Serial Patch"
date:   2012-04-02
categories: article
---

#### Uneventfull beginnings.

Inspired by Gregs talk I mention in the last post, I created this simple little patch. It modifies "/drivers/usb/serial/belkin_sa.c" to conform with the checkpatch script. The patch was accepted as first submitted but there was a requirement to use a "real" name for the Signed-off-by tag (https://www.kernel.org/doc/Documentation/SubmittingPatches). Which is fair enough.

There is a great visualization of the diff here (http://code.google.com/p/linux-picosam9g45/source/diff?spec=svn70f3c7586c708bce8f525246c8b27322edc00cc7&r=70f3c7586c708bce8f525246c8b27322edc00cc7&format=side&path=/drivers/usb/serial/belkin_sa.c) and the patch in Linuses tree is here (http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=70f3c7586c708bce8f525246c8b27322edc00cc7). The first is a handy little visualization for viewing this patch as it is all modified whitespace, a few spaces before tabs removed and the formatting of a case statement updated. In the Linux tree you'll need to use a trick to "see" the changes.

The LKML entry for the origional submission can be found here (https://lkml.org/lkml/2012/4/26/70). It is included below (although the changes are not visible as they are mushed up by HTML, thems the breaks).

        From	puzzleduck@gmail ...
        Subject	[PATCH] USB: serial: Changes to conform with coding style
        Date	Thu, 26 Apr 2012 19:31:04 +1000

        Removed some spaces before tabs and reformatted switch statement.
        Signed-off-by: PuZZleDucK
        ---
        drivers/usb/serial/belkin_sa.c | 13 +++++++------
        1 files changed, 7 insertions(+), 6 deletions(-)
        diff --git a/drivers/usb/serial/belkin_sa.c b/drivers/usb/serial/belkin_sa.c
        index a52e0d2..35b0d3d 100644
        --- a/drivers/usb/serial/belkin_sa.c
        +++ b/drivers/usb/serial/belkin_sa.c
        @@ -2,17 +2,17 @@
        * Belkin USB Serial Adapter Driver
        *
        * Copyright (C) 2000 William Greathouse
        (wgreathouse@smva.com)
        - * Copyright (C) 2000-2001 Greg Kroah-Hartman (greg@kroah.com)
        + * Copyright (C) 2000-2001 Greg Kroah-Hartman (greg@kroah.com)
        * Copyright (C) 2010 Johan Hovold (jhovold@gmail.com)
        *
        * This program is largely derived from work by the linux-usb group
        * and associated source files. Please see the usb/serial files for
        * individual credits and copyrights.
        *
        - * This program is free software; you can redistribute it and/or modify
        - * it under the terms of the GNU General Public License as published by
        - * the Free Software Foundation; either version 2 of the License, or
        - * (at your option) any later version.
        + * This program is free software; you can redistribute it and/or modify
        + * it under the terms of the GNU General Public License as published by
        + * the Free Software Foundation; either version 2 of the License, or
        + * (at your option) any later version.
        *
        * See Documentation/usb/usb-serial.txt for more information on using this
        * driver
        @@ -403,7 +403,8 @@ static void belkin_sa_set_termios(struct tty_struct *tty,
        case CS8:
        urb_value = BELKIN_SA_DATA_BITS(8);
        break;
        - default: dbg("CSIZE was not CS5-CS8, using default of 8");
        + default:
        + dbg("CSIZE was not CS5-CS8, using default of 8");
        urb_value = BELKIN_SA_DATA_BITS(8);
        break;
        }
        --
        1.7.2.5

This recieved the following reply from Greg K-H:

        On Thu, Apr 26, 2012 at 04:41:57PM +0400, Sergei Shtylyov wrote:
        > Hello.
        >
        > On 26-04-2012 13:31, puzzleduck@gmail.com wrote:
        >
        > >From: PuZZleDucK
        >
        > >Removed some spaces before tabs and reformatted switch statement.
        >
        > >Signed-off-by: PuZZleDucK
        >
        > Real name is needed here, no aliases allowed.

        I agree, please see Documentation/SubmittingPatches for what
        "Signed-off-by:" means, and why we can't accept this as-is.

        greg k-h

So I fixed that up in the patch, resubmitted and now it's in Linuses tree :D (http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=70f3c7586c708bce8f525246c8b27322edc00cc7).
