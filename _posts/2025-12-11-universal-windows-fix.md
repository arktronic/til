---
layout: post
date: 2025-12-11
title: The universal Windows fix checklist
tags:
- windows
- troubleshooting
---

This keeps coming up in various contexts over and over, so I might as well document it. What do you do when Windows decides to misbehave and a reboot isn't enough? Nothing overly specific, but maybe an occasional error, Windows Update acting wonky, or there's some other odd behavior that only happens on one computer. Here's my checklist of things to verify/run, which will get the vast majority of problems resolved, or at least identified.

All command line tools must be run in an elevated prompt.

1. Install all Windows updates, including optional driver updates. If you have an OEM-specific driver installer, like Dell's Command Update utility, use that as well.

2. Execute `chkdsk /f C:` and reboot, letting the primary disk be checked for errors. Repeat for other disks as needed.

3. Execute `dism /online /cleanup-image /restorehealth` to repair the component store. It can take a while.

4. Execute `sfc /scannow` to use the newly repaired component store to ensure that critical files aren't corrupted.

5. Reboot again.

This should fix the majority of software issues. If problems persist, then there may be hardware issues. In that case, try the following. These will not fix anything, but can help to determine if a specific hardware component is failing.

1. Verify the stability of system RAM by using [Memtest86+](https://www.memtest.org/)

2. Stress-test the CPU by using [Prime95](https://www.mersenne.org/download/)

3. Stress-test the GPU with [FurMark](https://www.geeks3d.com/furmark/)

4. Benchmark the HDD/SSD with [CrystalDiskMark](https://sourceforge.net/projects/crystaldiskmark/files/) to verify that speeds are not tanking, which could indicate a failing disk

For additional disk testing, use [smartmontools](https://www.smartmontools.org/wiki/Download).

If none of the above helps, then consider reinstalling the OS and/or replacing the computer, as some hardware failures can be notoriously difficult to pinpoint.
