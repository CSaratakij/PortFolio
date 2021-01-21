---
title: "Doppelganger"
date: 2020-09-02T09:11:33+07:00
math: true
toc: true
tags: [Unity, NSC2018, Custom Editor]
weight: 1
draft: false
---
The puzzle platformer with a twist. Player can use a “Focus” power, the ability to bend a dimension to overcome the obstacle.

![Doppelganger](/img/dg-cover.png)

<!--more-->

game: https://csaratakij.itch.io/doppelganger \
respository: https://github.com/CSaratakij/DG-Script-Only

other member: \
[Nutthan Lekprasan](mailto:nutthanlekprasan@outlook.co.th) (game designer) \
[Jetniphat Likhitwatthanasakun](mailto:jetniphatoat@gmail.com) (artist)

responsible: game system & custom tools

## Showcase
### Focus Ability
{{< youtube YkUhBMcTIBo >}}

### How it works
{{< youtube 89UHRY-0vbk >}}

### Custom Editor
#### Sprite Plotter
{{< youtube f7WA2ed93RI >}}

#### Collision & Collider Plotter
{{< youtube 5gCgzt1DCqA >}}

#### Scene Selector
{{< youtube PaeOfl0nNyM >}}

## Introduction
Before you read any further, I have to warn you. There are some __spoiler__ of the puzzle in this game. Please play the game first to avoid any spoiler.

This game is the entry for __The Twentieth National Software Contest: NSC 2018__.
We have about __3 months__ to finish this project.

We manage to get the __2nd runner up__ in ___"Program for entertainment"___ .

Since I mainly do a game system and some of the game design, I will cover these topics with in depth. However, I will leave the art aspect to the 
artist himself.

## Why this game call "Doppelganger"
If you already play the game, you will notice that there isn't a single doppelganger in this game.
We name this game __"Doppelganger"__ at first because we want the game to do something about a clone of our player character.

Turns out, none of the things we discuss in the early stage made it into the final product.
Most of the things in the game come from a first month we made doing a rappid prototype and play testing a lot.

But this is the entry for the contest, We cannot change our name mid-way due to the proposal we sent during the first round of the competition. So we kinda have to live with that.

## Technical Challenge
Well, there are a lot of stuff I can cover. \
But I will highlight the most challenge stuff here.

If you interested in the __full postmortem__, please read [here](https://csaratakij.github.io/projects/doppelganger).

### Game System
The most challenge stuff to implement is the focus ability.\
It's the world wrapping mechanic.

Long story short.\
To make this work, I need to test if player able to wrap themself back first.

Let's say the overlap area is the testing area. \
And the blocker is an invinsible wall to prevent player from moving any further.

![img1](/img/dg-blocker-01.jpg)

If the testing pass, blocker will let player wrapping themself.

![img3](/img/dg-blocker-03.jpg)

But, if the testing fail, blocker will block player path.

![img4](/img/dg-blocker-04.jpg)

This is roughly how it works in the game.

![img5](/img/dg-blocking-kiss-allow-explain.png)

### Custom Editor
I need to finish the game system and speed up our level works as well.\
My custom sprite plotter and collision & collider plotter works perfectly.

The simple custom editor knowledge help making this possible. \
To speed up plotting stuff, you just plot by making A and
B point by clicking the mouse.

It'll form a rectangle, filling all the neccessary stuff inside it.

![img6](/img/dg-A-B.png)


### Time Management
As for the last 10 days, I adopt for the simple kanban board. \
This help me focus on the task better. \
You can see our board [here](https://trello.com/b/hVPRrx2p/dg-frame) .

## Summary
I pour heart and souls into this project, really worth it at the end. \
Don't forget to check for the full postmortem [here](https://csaratakij.github.io/projects/doppelganger) .

