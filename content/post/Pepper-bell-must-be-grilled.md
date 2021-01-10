---
title: "Pepper Bell Must Be Grilled"
date: 2020-09-02T09:14:31+07:00
tags: [Unity, Ludumdare, GameJam]
weight: 5
draft: false
---

The entry for __Ludum Dare 43__ . \
The 4 players party game. Each player must catch and throw each other to the roaster to gain the point within the time imit.

![game](/img/pb-intro.png)

<!--more-->

game: https://csaratakij.itch.io/pepper-bell-must-be-grilled \
respository: https://github.com/CSaratakij/Ludumdare43

other member: \
[Chusak Tan](mailto:chusak_saetan@hotmail.com) (technical artist) \
[Jetniphat Likhitwatthanasakun](mailto:jetniphatoat@gmail.com) (artist) \
[Pattarawut Jarupramote](mailto:jmpt.pattarawut@gmail.com) (artist) \
[Panawat Khumgun](mailto:chikakito39@gmail.com) (artist)

responsible: game system

## Showcase
{{< youtube HQCoXmRc1NU >}}

## Introduction
This time, I manage to form a load of people with just an online jam. \
It's still fun, but getting less sleep as always.

## Technical Challenge
Like most of the jame, challenge is to implement stuff with limited time (72 hours). \
The first challenge of this game is to support 4 players.

Seconds is debug the core mechanics. \
I spend too much time debugging about hit detection.

That's why I don't have enough time to make a keyboard support and join room support with less than 4 players.

Also, without a proper hit detection, player can carry other player up to 3 people... \
(It should carry only one people at a time.)

![why it can carry 3 people?](/img/pepper-bell-must-be-grilled-obstacle.jpg)

For some reason, I choose rigidbody instead of character controller for the player character.

I have to give a proper physics material to its rigidbody, the one that have friction set to zero to avoid character getting stuck to the wall.

## Summary
Well, I pull this off somehow. \
Not my best performance, but it still a fun party game.

