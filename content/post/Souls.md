---
title: "Souls"
date: 2021-01-07T21:54:38+07:00
weight: 6
tags: [Unity]
draft: false
---

The game that inspired by the souls-like genre.

![preview](/img/souls_preview.png)

<!--more-->

game: https://github.com/CSaratakij/Souls/releases \
respository: https://github.com/CSaratakij/Souls \
responsible: game system

other member: \
[Pattarawut Jarupramote](mailto:jmpt.pattarawut@gmail.com) (artist)

## Showcase
{{< youtube H_EocJMy4ss >}}

## Introduction
This one start from the meme about the strong animal. \
It's weird....(I know)

![preview](/img/strong-dogu.jpg)

At that time, I used to play souls-like game a lot. \
So I taught, why not combine __meme__ with souls-like genre?

## Technical Challenge
### Animation
This is a mix of root motion and non-root motion.

The hit confirm system is simple, is just estimate the hit area in front of the player, checking for any potential enemy and register hit when player doing the slash animation.

The headache come from adjusting the timing of animation to determine the time player can start hitting something by slash animation.


### Camera
Surprisingly, I spend most of the time writing this.

If I realize sooner that the camera itself just orbiting player and look at the player all the time, things might speed up even further.

The challenge here is to make camera feels smooth as much as possible without obstruct by any obstacle (such as wall).

Simply raycast from player to camera to check any obstacle and adjust camera position smoothly do the tricks.

## Summary
Aside from not having an auto target lock system, it's play okay for me. \
Sure, the walking and combat need some fine tune. \
Still, not bad for a week of works.

