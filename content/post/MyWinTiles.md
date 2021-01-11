---
title: "MyWinTiles"
date: 2020-09-02T09:15:04+07:00
weight: 9
tags: [C++, Win32api, Tiling Window Manager]
draft: false
---

The tiling window manager for Windows, built on top of Windows Explorer Shell. \
Aim to improve productivity of any user that heavily use keyboard on their daily basis.

![app](/img/mywintiles-intro.png)

<!--more-->

It focus heavily on keyboard usage (vim-like) to prevent mouse usage which
usually need in the typical stacking window manager (use mouse to minimize, maximize, focus and close window) .

release: https://github.com/CSaratakij/MyWinTiles/releases \
respository: https://github.com/CSaratakij/MyWinTiles

responsible: all

## Showcase
### Ideals Desktop Environment
{{< youtube pSBTtKgShQQ >}}

### Tiling Window Manager Explain
{{< youtube GHOhQw8JxgM >}}

## Introduction
    First, to avoid any confusion, I will refer "Windows" as an operating system.
    And refer "window" (without 's') as window of program (GUI).

Most of my workflow is on the linux side.

Tiling Window Manager with [full (comfortable)keyboard control](https://i3wm.org/) is one of the things I miss when using Windows.

I get annoyed everytime I have to micro management window. \
For example, move window around with mouse, click minimize/maximize window, etc..

So, I decide to hack things together to create my ideals desktop environment in just a week.

My ideals desktop environment consists of:
1) Tiling window manager
2) Bar (or taskbar)
3) App Launcher

This is possible, thanks to Win32 API. \
Although, it has its own limit.

## Technical Challenge
Oh boys..where to begin..\
I'll highlight just only the crucial stuff.

But first, I need to explain the terms.

HWND is a window handle.\
It's an int pointer, it can use to refer to window.

![image about session, desktop and window HWND](/img/mywintiles-overview.png)

Desktop and virtual desktops is not the same thing. (they call 'virtual' for a reason) \
Virtual desktops is mimick multiple desktops without using the real multiple desktops.

Workspace is a group of window, virtual desktops and workspace is refer to the same thing.

### Virtual Desktop limitation
    Don't confuse this with Windows Virtual Desktop that run on Azure.

Since Windows 10, Virtual Desktops has been introduced.

The feature is great, but only a little COM api has been [public](https://docs.microsoft.com/en-us/windows/win32/api/shobjidl_core/nn-shobjidl_core-ivirtualdesktopmanager). \
The rest of virtual desktops api is hidden, undocument.

Seriously, hidden to the point of being useless.

That's why I can't control how virtual desktops behave programmatically. \
I have to implement this stuff myself.

The simple array to hold HWND and making window minimize if the window is not belong to the current workspace do the tricks. 

### HWND quirk
The key to make this program works is to make sure HWND point to the same window at the time of this program collect window information.

Such as, when this program initialize, detect if some window get create/destroy, etc..

Unfortunately, Windows decide to recycle HWND. \
So, I cannot ensure the HWND that I get will point to the same window after initialize.

One thing for sure is, when window is hide (not show in the Task Switcher), HWND will get free. \
That HWND becomes obsolete, ready to be recycle by Windows.

I need to avoid hiding window.

Also, getting HWND by the window title name is not reliable.\
Some window will change its window title from time to time, for an example the Web Browser.

### Window Filter
The reason window need to be filter is simple.

Win32 api provides the way to get all the window in the desktop, which is what I want. \
But it'll get all the window regardless of its visibility.

From user perspective, visible window is the one user can see. \
And all user care about is the one that they can see.

But for some reason, the api that test if some window is really visible is not accurate. \
It'll report some hidden window back for me.

I need to checks other information as well, like for example, window title information to be certain about its visibility.

### Custom Shell limitation
To get the event message of every window in the desktop, I need to register shell hook.

The event message is the key to know whether or not some window will get create, destroy, maximize, minimize, etc...

The default gui shell in Windows is Windows Explorer Shell.

At first, I want to replace the default shell. \
Like how [cairo shell](https://github.com/cairoshell/cairoshell) did.

Unfortunately, there is no shell message available for custom shell. \
So, that's why this need to built on top of the Windows Explorer Shell.

## Summary
With this functional implement, I can use Windows peacfully. \
As long as Win32 API remain backward compatibility, it should works fine. \
This is currently my first program to install and run when I need to use any computer with Windows on it.

