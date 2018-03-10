---
layout: post
title:  "Linux Kernel: Missing in action"
date:   2018-03-10 01:00:00 +1000
categories: jekyll update
title-image: tux.png
---

This week I had the unfortunate experience of rebooting my laptop and finding out the hard way that the linux kernel image i was running from had mysteriously vanished. It seems that some updates had failed to complete and had left the system in an unbootable state (at least that is what I think happened).

It happened that I'd just turned up to the first FOSS hack night at YBF Teamsquare when this tragedy unfolded and I was able to borrow a [Kali Linux][kali-linux] boot usb from someone at the meetup to boot up the laptop and confirm the hardware was still all functional. Memory was ok, I could read the drive fine, and almost everything seemed to be the there... except in the boot directory only the memtest86 images were present... What happened to my kernel images :o

Spoiler alert: I never figured out why they dissapeared, but there is a very Linuxey happy ending to it all. A few people at the hack night pointed me in the direction of [chroot-ing][chroot] into the disk and repairing the system in place. It took a few tries to get everything to work, but for future reference the process was as follows:

From the live-system open a terminal and run the following:

````bash
umount /dev/mmcblk1p1   # unmount the automounted drive before starting
cd /mnt
sudo mkdir duck     # create a working directory to use
sudo mount /dev/mmcblk1p1 /mnt/duck   # mount the disk in our temp directory
sudo mount -t proc none /mnt/duck/proc   # mount system directories for chroot
sudo mount -o bind /dev /mnt/duck/dev
sudo mount -o bind /run /mnt/duck/run
sudo mount -o bind /sys /mnt/duck/sys
sudo chroot /mnt/duck /bin/bash
````

Now we are running the non-booting-system with its devices, processes and system. We can now run commands to repair the system:

````bash
apt upgrade
apt search linux-image
apt install linux-image-extra-4.13.0-36-generic linux-image-4.13.0-31-generic
apt purge grub grub-pc grub-common
apt install grub-common grub-pc
exit
````

Finally we need to cleanly unmount everything else before unmounting the drive:

````bash
sudo umount /mnt/duck/proc
sudo umount /mnt/duck/dev
sudo umount /mnt/duck/run
sudo umount /mnt/duck/sys
sudo umount /mnt/duck
exit
````

Now the system can boot again (allowing me to write this update amongst other things)

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at . If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[chroot]: http://man7.org/linux/man-pages/man2/chroot.2.html
[kali-linux]: https://www.kali.org/
