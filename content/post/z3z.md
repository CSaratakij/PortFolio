---
title: "Z3z"
date: 2020-09-02T09:14:43+07:00
weight: 2
tags: [Unity]
draft: false
---

The first person shooting that heavy inspired by __Lovely Planet__. \
Player must defeat all enemies within the level to proceed to the next level.

![game](/img/z3z-intro.png)

<!--more-->

game: https://github.com/CSaratakij/z3z/releases \
respository: https://github.com/CSaratakij/z3z \
responsible: all

## Showcase
{{< youtube 8EtqjO4foA4 >}}

## Introduction
Lovely Planet is amazing, But I want to add more level. \
So, I try to clone it.

## Technical Challenge
The fact that player saw bullets travel from the gun barrel make things a little complicated.

### Hit Register
Since bullets need to move, I need to make sure the chance of collision tunneling is low. \
I need __Continuous Collision Detection (CCD)__, using it with bullets.

Unity provides collision detection type ["Continuous Speculative"](https://docs.unity3d.com/ScriptReference/CollisionDetectionMode.ContinuousSpeculative.html). \
Which is the CCD but cheaper to calculate than the CCD with a sweep based.

I also need to keep the bullet traveling with resonable low speed, further avoding the chance of tunneling.

### Bullet Trajectory
I need to make bullet appears at the gun barrel and travel with the aim direction. \
The aim direction in the player perspective is from the center of the screen.

The gun itself need to look like it point to the center of the screen as well. \
So, I need to rotate a gun to make it look like that some how.

Because there is no crosshair in this game, player should be able to aim from the hip by the line sight that gun model create.

![gun line sight](/img/z3z-gun-line-sight.png)

Without this line sight, aiming is stupidly difficult.

To rotate the gun, I simply find a look direction of camera in world space, offset it forward and then make gun model look at that position (Rotate only Y-axis).

![rotate explain](/img/z3z-rotate-explain.png)

## Summary
I already tweak the feels of player controlling. \
The core functional works pretty well, more level and enemy type I guess.

This one is about trying to clone the game mechanic, so I don't have an intention to release this to game site such as [itch.io](https://itch.io/) (aside from the source).

