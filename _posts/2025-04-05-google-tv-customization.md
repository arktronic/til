---
layout: post
date: 2025-04-05
title: Google TV customization
tags:
- tv
- google
- adb
---

I've been playing around with Google TV boxes, as well as actual TVs, and I've learned a few things about customizing them. *NB: Naturally, as operating systems and services get updated, this information will become outdated.*

One thing I like to do is reduce clutter and focus on just the tasks I want. On Google TVs, that pretty much consists of Jellyfin these days. A totally built-in way to remove a lot of unnecessary bloat from the home screen is to go into your logged in profile settings and select Apps Only Mode. This makes the Google TV operate almost like a Roku, focusing on apps, rather than "immersive" experiences.

Going beyond that, to remove additional advertising, you can install a different launcher. My go-to at the moment is [Projectivy Launcher](https://play.google.com/store/apps/details?id=com.spocky.projengmenu), which you can find in the Play Store and install right on the TV. This is where we run into the first complication. For a launcher to be useful, it must be, well, the launcher that actually gets used - the default. This can be easy or difficult to achieve, depending on the Google TV system that is in use. In some cases, enabling accessibility for Projectivy (which it prompts you to do anyway) and checking a couple of boxes in its settings will be good enough. The main settings screen even has a helpful button labeled "Change default launcher" to help with this. However, I've found that on some systems that button is disabled. In that case, a workaround is to go back to the Play Store and install [ADB TV](https://play.google.com/store/apps/details?id=com.cybercat.adbappcontrol.tv). Enabling that app involves going though the motions to get Android's Developer Mode turned on and configured, but once that's all done, ADB TV can be used to find and disable the built-in launcher app, Google TV Home (com.google.android.apps.tv.launcherx). Once disabled, the system will have no choice but to default to using Projectivy as the only available launcher.

Finally, since most of the time I just want to use Jellyfin, I've configured Projectivy to launch it on boot. It's simply a setting available in the launcher.
