---
title: "HierachySection"
date: 2020-09-02T09:14:55+07:00
weight: 7
tags: [Unity, Custom Editor]
draft: false
---

The custom editor for Unity to highlight a game object that has a prefix __'---'__ in its name to help seperate stuff in the Hierachy panel.

![custom editor](/img/hs-intro.png)

<!--more-->

respository: https://github.com/CSaratakij/HierachySection \
responsible: all

## Showcase
{{< youtube jGPZKuENZG4 >}}

## How it works
This is possible by simply hook the event ["EditorApplication.hierachyWindowItemOnGUI"](https://docs.unity3d.com/ScriptReference/EditorApplication-hierarchyWindowItemOnGUI.html), Check the current gameobject item name whether it has a prefix "---" and draw the stuff on top of the current Hierachy Window item. (Immediate mode gui style)

