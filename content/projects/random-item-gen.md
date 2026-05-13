---
title: "RandomItemGen"
#date: 2021-04-03T22:53:58+05:30
draft: false
github_link: "https://github.com/gurusabarish/hugo-profile"
badges:
  - Unity - C#
  - Inventory & Equipment System
  - RPG Mechanics
imagelink:
  enable: true
  link: /projects/random-item-gen
image: /images/randomitemgen.png
#banner: /images/mallanebanner.png
description: ""
summary: "Item generator prototype with various RPG mechanic implementations. Click 'Read more' to learn about the features I developed for it!"
toc: 
---

{{<image width=100% maxwidth=100% src="/images/randomitemgenbanner.png">}}

## Overview

I made this project to more familiarize myself with common RPG mechanics such as inventories and equipment panels, handling various UI interactions such as dragging items between inventory and equipment slots, UI interactions for talent trees that have pre-requisites, stat displays, and more.

## Item System

The project started out with wanting to generate items similar to those found in ARPG games such as Path of Exile, where there are constraints on the item such as an item level that influences how high of tier of modifiers a given item can have, or a rarity quality that dictates how many attributes can be on that item at one time. 

### Implicit & Explicit Properties

Similar to itemization in Path of Exile, I wanted to emulate the idea that certain types of items come with implicit properties that they will always have, such as a jewelry subtype that always provides some amount of mana regeneration, or shield items always having some percentage chance to block attacks. Beyond their implicit properties, items can also have explicitly granted properties as well from a large pool of attributes that are shared amongst all item types. Each of these properties come with potential prefixes and suffixes that can be chosen to be added to the item's name.

{{<image width=100% src="/images/itemgen1.png">}}
In this example the 'Calibrated' prefix comes from the increased chance to hit modifier, and the 'of Brawn' suffix comes from the total strength increase modifier. The item also has an implicit modifier granting spell damage because of the item type 'Tome' that it has.

### Inventory & Equipment

After making the implementation for items, I wanted a way for players to be able to keep and equip their items, so I made an implementation for an inventory and equipment system that you might see in MMORPGs. I wanted to make this feature as intuitive to use as possible so it supports both drag and drop and right click to equip operations.

{{<video width=100% src="/images/itemgenui1.mp4">}}

### Applying Item Stats

Then I wanted to actually make the attributes on an item change stat values for the player, so I stubbed those out into a list of player stats and then loop over the equipped items and apply effects based on the current index attribute for said item.

{{<video width=100% src="/images/itemgenui2.mp4">}}

In this example these pair of gloves give the player +36 Maximum Mana, which when equipped you can observe the Mana stat going from its unbuffed value of 100, to it buffed value of 136. Similarly this is applied for each other attribute on the gloves and is reflected on the status panel to the right.

## Talent Tree

Another commonly encountered feature in MMORPGs are Talent Trees, which are generally started from a single point and allows players to make branching decisions to further enhance the elements that they in particular find fun. 

{{<video width=100% src="/images/itemgen2.mp4">}}
A core design element for most of these are constraints on which path the player can take at a given time, such as a node requiring one or more prerequisite talents to be unlocked, or to have a certain threshold of points in the tree in total.

## UI Implementations

I was particularly proud of the UI implementations I worked on throughout this project, namely the custom tooltips and the dynamic UI panels.

### Custom Tooltips

It feels like tooltips in games like these are mandatory so I wanted a robust system that handled displaying all the relevant info for something the player might hover over to gain more information on. I also wanted it to be concise and sleek in design, so I followed with the grey minimalist design patterns that the rest of the project had up to this point.

{{<video width=100% src="/images/itemgen3.mp4">}}

### Dynamic UI Panels

Again as previously stated, this is another commonly found feature in MMORPGs and RPGs in general, as there can be a multitude of information panels being presented to players, and it's useful to be able to move them around, reorder them, and to close and re-open at your leisure. I implemented these similar to how you expect a window to move on a desktop computer, with the top title bar being a drag zone.

{{<video width=100% src="/images/itemgen4.mp4">}}