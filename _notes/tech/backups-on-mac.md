---
title: Running backups on Mac
layout: tech
---
Conveniently, Apple have included a useful backup tool in Time Machine. You
simply need to plug in an external drive, tell Time Machine to use it and it
chugs away in the background backing things up. But, particularly with laptops,
you do need remember to both plug it in and eject it. What about using a
networked storage device for backing up to? It is always there.

To set this up, you need to create a virtual disk on your Mac that can be
mounted and pretend to be a disk available to Time Machine and put that on the
networked storage.

Importantly, it also needs to mimic the properties of the drive you're backing
up in terms of case-sensitivity (note the -fs flag below).

For me the command to generate the file is:

    hdiutil create -size 750g -type SPARSEBUNDLE -fs "Case-sensitive Journaled HFS+" -volname "TM_Rohan" MBA_TM.sparsebundle

You can then copy this file onto the network share you'd like.

To run the backup, you need to mount the new drive on the share, which is two
steps - mount the share and then the virtual drive. An easy way to deal with
Samba network shares is to [use the commandline](http://hints.macworld.com/article.php?story=20020610225855377).
You may need to make the mount-point first:

    mkdir /Volumes/Backup-Rohan

then:

    mount -t smbfs //GUEST:@192.168.145.145/Backup-Rohan /Volumes/Backup-Rohan
    sudo hdiutil attach -mountpoint /Volumes/TM_Rohan/ /Volumes/Backup-Rohan/MBA_TM.sparsebundle

The first time you set this up, you need to tell the Time Machine process to
use this disk:

    sudo tmutil setdestination -a /Volumes/TM_Rohan

Importantly, the -a tells the command to 'add' the destination, rather than
replace it. If you already use a disk, it will be removed as a destination
available to Time Machine without the '-a'.

Get the ID of the destination:

    tmutil destinationinfo

Noting the Volume ID, you can the tell Time Machine directly to back up now to
that device

    tmutil startbackup --auto --block --destination $VID
