---
title: "Bongocat Osu (Linux Native Port)"
date: 2020-09-02T09:15:21+07:00
weight: 7
tags: [C++, SFML, Linux, OSU]
draft: false
---

The bongo cat that show how user smash their keyboard and how their mouse or pen tablet might look like in the real world.
Very useful when streaming osu! game.

![app](/img/bongo-intro.png)

<!--more-->

This is the fork implements the linux specific quirk to make it function like its [upstream](https://github.com/kuroni/bongocat-osu).

repository: https://github.com/CSaratakij/bongocat-osu/tree/feature-linux-native-port \
responsible: linux port

## Showcase
### Run natively on linux
{{< youtube OylY3CnOpKs >}}

### Use with OBS
{{< youtube 3wbGySAu-Hw >}}

## The need to port this
I already used this program on Windows. But I want to run this program natively on linux. \
Normally, this program already run well with [wine](https://www.winehq.org/).

Unfortunately, In order to work with osu!, I have to run this program with the same [WINEPREFIX](https://wiki.winehq.org/FAQ#Can_I_store_the_virtual_Windows_installation_somewhere_other_than_.7E.2F.wine.3F) as the osu!.

I don't want to bother with that. \
And since this program use [SFML](https://www.sfml-dev.org/), It should be easy for me to port this.

My my!...How wrong was I. It took me 3 days to port this. \
Let me show you the struggle.

## Technical Challenge
### Building in general
The first step to make this possible is to make it build natively in the first place.

I need to comment the code in the part that is OS specific. Write a new Makefile. \
Also, I need to change from static link SFML to dynamic link which is prefer in linux.

### Win32 api struggle
This is why is not easy to port as it should be. \
Upstream use [Win32 API](https://docs.microsoft.com/en-us/windows/win32/api) for checking keyboard and mouse cursor position.

Since this is an OS specific, I need something equipvalent in linux. \
As for the keyboard input, SFML will do just fine.

But getting the mouse cursor position, I need to talk to [X11](https://en.wikipedia.org/wiki/X_Window_System).

There's a library call [libxdo](https://github.com/jordansissel/xdotool), which make my life easier for getting the information about window related stuff in x11.

Still, I need to talk to x11 directly for the screen resolution.

Also, I need to show the message box. The [GTK](https://www.gtk.org) and [Qt](https://www.qt.io) is way too overkill for this.
I don't know ahead of time if user have a linux ditro based on GTK or Qt. (Gnome or KDE for an example)

The amount of library dependencies that user need to install in order to show message box in those library is too much.

Instead, I opt for [SDL](https://www.libsdl.org). \
Way less bloat than those gui library.

### Linux specific quirk
Well, for some reason, x11 handle error strangely. \
If there is an error, x11 will force application to quit itself.

I have to overwrite this behaviour by writing my own handle error callback. \
Still, why you do this...x11?

## Summary
With some struggle, I manage to port this to linux. \
I still use this program, that's why I currently help upstream resolve issue and implement feature.

At the time of writing, the last feature I implement and got merge into upstream is a joystick support. \
You can take a look [here](https://github.com/kuroni/bongocat-osu/pull/115).

{{< youtube KlVhMYmJ4AU>}}

