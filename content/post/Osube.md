---
title: "Osube"
date: 2020-09-02T09:15:34+07:00
weight: 8
tags: [Python, Shell Script, Linux, OSU]
draft: false
---

The little script that help extract multiple osu! beatmaps. \
It come with a file watcher to detect and auto extract any beatmap in the watching directory.

![osube](/img/osube-intro.png)

<!--more-->

This help improve my experience when playing osu in linux with multiplayer mode without the osu supporter.

release: https://github.com/CSaratakij/Osube/releases \
respository: https://github.com/CSaratakij/Osube

responsible: all

## Showcase
{{< youtube 7gUCAANz3oo >}}

## The need to write this
I'm a fan of [osu!](https://osu.ppy.sh/home), and I used to play this game a lot (this is my [profile](https://osu.ppy.sh/users/2800315)).

There is the things call **osu! supporter**, which is the in-game feature to download any beatmap without leaving the game at all.

But, it cost money and there is a time when I rarely play this game in a month.\
So, paying for osu! supporter without playing the game is not worth it.

Also, I use Linux to play osu!.\
The normal funtional to extract beatmap that game provide is simply not work.

That's why I wrote this little script to extract osu! beatmap with ease. \
Which is really useful when I download a bunch of beatmaps, and need to try all of those beatmaps.

## How it works
Even though osu! beatmap file extension is ".osz", But it's actually just an archive file like ".zip" .\
All I need to do is to extract .osz file to the right directory and make sure the folder structure is correct to make it works.

## The technical challenge
This is a command line application. \
Every time I want to extract beatmap, I need to manually execute the command.

Doing this many times starting to get me, So I decide to automate my script. \
To make my automation works, I need a file watcher.

Lucky for me, linux kernel provide the file system events stuff already.\
There's a utility call [inotifywait](https://linux.die.net/man/1/inotifywait) which use the [inotify](https://en.wikipedia.org/wiki/Inotify) to report the file system events.

With inotifywait, I can write a simple shell script to act as a file watcher.

All I need is to watch for the certain directory and execute osube command to extract beatmap once the watcher found the .osz file.

The file system events I need is "move_to" event.

The reason is simple. While using Google Chrome, any unfinished download file will have ".crdownload" extension.

Once the file downloaded, It'll rename the file to match the original name of the download.\
The act of renaming the file will trigger "move_to" event.

## Summary
With python to unzip the file and simple shell script, I can make my life easier. \
Now, I can play osu! in linux with [wine](https://www.winehq.org/) without having to manually extract beatmaps.

