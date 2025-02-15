---
layout: post
date: 2025-02-15
title: Recovering data from Windows dynamic mirrored disks
tags:
- windows
- linux
- data recovery
---

Today, I made a terrible mistake. I attempted to do a live upgrade of a Windows mirrored disk pair to use larger SSDs. The procedure started normally, but in the middle of one of the resync operations, I realized that I would need to break the mirror (again) in order to resize the partition because mirrored partitions are not resizable, so I naively stopped the resync. Bad idea. The source drive ended up in an "invalid" state, which Windows refuses to work with in any way, it would seem.

Luckily, Linux can help with this issue! All I needed to do was `apt install ldmtool` on my Debian machine. Then, once I connected the "invalid" disk to it, the primary partition on that disk auto-mounted, and I could immediately access all of the data on it. The next steps were obvious: copy the data to another disk and start over. The final resync is running right now.

P.S. I hate that Windows uses the term "resynching" - with the "h" in there.
