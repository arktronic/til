---
layout: post
date: 2025-09-04
title: Windows GUI vs. console apps
tags:
- windows
- exe
---

TIL of the specific differences between two of the most common "modes" of EXE applications. The PE (Portable Executable) format has a [Windows Subsystem](https://learn.microsoft.com/en-us/windows/win32/debug/pe-format#windows-subsystem) field, which is most often set to either `IMAGE_SUBSYSTEM_WINDOWS_GUI` or `IMAGE_SUBSYSTEM_WINDOWS_CUI`. When set to the GUI subsystem:

- No console is allocated or used by default
- Launching the app will not show a new console window
- Executing from inside an existing console will be done asynchronously (i.e., the command interpreter will return immediately)

On the other hand, when set to CUI (character subsystem):

- Launching from outside a console environment will create and show a new console window
- Executing from inside an existing console will be done synchronously (i.e., waiting for the app to finish before showing another prompt)

But what if I want some combination of the above? Can I have one EXE that does both?

Strictly speaking, the answer is no. Since that subsystem flag is compiled into the EXE, you can only have one or the other. However, there are workarounds. A GUI subsystem app can still allocate a console and, when launched from an existing console window, output data to it. However, because it's launched asynchronously, it would be outputting data at the same time as the command interpreter, which looks awful. Launching such an app using `start /wait` will fix that, but it's a bit annoying. Conversely, a character subsystem app can create a GUI window, but there is no way to prevent Windows from (briefly) showing a terminal window when the app is launched, which is annoying in a different way.

Another workaround is to simply have different versions of the same application. Windows even comes with apps that follow this pattern, such as `cscript` and `wscript`. Similarly, Visual Studio's `devenv.exe` has a companion `devenv.com` console app (although it's not a real COM format; it's just a renamed PE executable).
