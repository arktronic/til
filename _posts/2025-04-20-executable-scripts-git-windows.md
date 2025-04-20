---
layout: post
date: 2025-04-20
title: Committing executable scripts in Git on Windows
tags:
- git
- windows
- linux
---

I finally learned how to commit a shell script in Git on Windows that will have its executable bit set in Linux when the same repo is used there:

```sh
git update-index --chmod=+x scriptname.sh
```

That's all that needs to happen before you do the normal commit flow. Easy!
