---
title: "MyWinBar"
date: 2020-09-02T09:15:14+07:00
weight: 11
tags: [C++, Win32api, Tiling Window Manager]
draft: false
---

The custom taskbar design to use with __MyWinTiles__ to properly show the current workspace.

![preview](/img/mywinbar-preview.png)

<!--more-->

release: https://github.com/CSaratakij/MyWinBar/releases \
repository: https://github.com/CSaratakij/MyWinBar \
responsible: all

## Showcase
{{< youtube oZzpa10FVQ8 >}}

## Introduction
MyWinBar is the custom taskbar to be use with MyWinTiles.

It show information about workspaces, what window is currently on focus, battery status and current time.
The solely purpose is to make it easy to use MyWinTiles.

Making an ideals desktop environment consists of these stuff.

1) Window manager : MyWinTiles
2) Bar : MyWinBar
3) App Launcher : [Wox](https://github.com/Wox-launcher/Wox)

## Technical Challenge
### Documentation
Win32 API is huge... \
You can get lost in information if you don't know what you're looking for.

Well, I know this is about Windows Shell & Desktop Environment. \
After skimming through the document, I found exactly what I'm looking.

Windows call it "application desktop toolbar" (or appbar), this [docs](https://docs.microsoft.com/en-us/windows/win32/shell/application-desktop-toolbars) has everthing I need to know.

The thing is, this is not an usual application. \
That's why there is less information about this stuff on any forum.

I have to tell the __Windows Explorer Shell__ to reserve some space on the screen for the custom taskbar.
To prevent any normal application overlap on this custom taskbar.

Without the docs above, this is simply not possible.

### Communication with MyWinTiles
I need [interprocess communication (IPC)](https://docs.microsoft.com/en-us/windows/win32/ipc/interprocess-communications) to make MyWinTiles and MyWinBar talk to each other. \
Socket is way overkill for this task, So I use [Data Copy](https://docs.microsoft.com/en-us/windows/win32/dataxchg/data-copy).

I encode the information about workspace status as a bit to send the data in one go, avoid any race condition to occur.

![bit-encode](/img/mywinbar-bitflag.png)

All I need is 2 bytes, first 6 bits is for the current workspace. 10 bits after that is a bool flag status of wheter or not workspace currently have atleast 1 window.

To get the information, simply use bitwise. \
Shift bit to the right by 10 to get the current workspace. Use AND operation to get the bool flag.

## Summary
With win32 api magic and simple bitwise, I can make a custom taskbar.\
This thing is useless on its own, It need MyWinTiles to function.
