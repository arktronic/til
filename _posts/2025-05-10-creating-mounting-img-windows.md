---
layout: post
date: 2025-05-10
title: Creating and mounting .img files on Windows
tags:
- img
- windows
- idrac
- ops
---

Today I needed to create a blank `.img` (raw disk) file, format it with a filesystem, mount that filesystem, and put a file on it. The reason for this was absolute laziness: I didn't want to put a file on a flash drive and then go to my basement to plug it in to a server. Instead, I wanted to use the Dell iDRAC Virtual Media option to mount a disk with the necessary file. So, how does one create such a disk file?

The option I chose was [ImDisk](http://www.ltr-data.se/opencode.html/#ImDisk). It's free software that has apparently been around for quite a while, and it still works in Windows 11. It creates a Control Panel item (classic!) with a very old-school interface for creating and mounting disk images. Once created and mounted, I simply used the Windows disk formatter and then Explorer to get the necessary file into the virtual disk. Then, after unmounting, I connected the disk through iDRAC's Virtual Media options and transferred the file successfully to the server!
