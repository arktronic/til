---
layout: post
date: 2025-02-05
title: Using a Roku TV as a computer monitor
tags:
- tv
- roku
- monitor
---

I didn't learn this recently. In fact, I realized that it's been buried in my head for a while, until a coworker happened to mention that his screen looks a bit... off.

If you use a Roku television, no matter what brand (TCL, Hisense, etc.), as a computer monitor, you may notice that text doesn't render very accurately. You may also notice that color calibration is worse than usual. There is an unofficially documented fix for this, which, on the surface, makes no sense, but it does fix a lot of issues:

> Rename your HDMI input to "Computer".

Yes, a name shouldn't affect anything, but it does, in the specific case of "Computer". After renaming the HDMI input in Settings and rebooting the TV, it will start rendering things much more accurately. I've seen claims that this is because it avoids conversion between RGB and YCbCr, but I cannot confirm that. Regardless, it works and it helps.
