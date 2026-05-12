---
title: "Bone Rolla"
#date: 2021-04-03T22:53:58+05:30
draft: false
github_link: "https://github.com/gurusabarish/hugo-profile"
badges:
  - Unity - C#
  - Deckbuilding
  - RPG & Roguelike Mechanics
  - Music Production
imagelink:
  enable: true
  link: /projects/bone-rolla
image: /images/bonerolla.png
#banner: /images/mallanebanner.png
description: ""
summary: "Roguelike dice game with deckbuilding and RPG elements. Click 'Read more' to learn about the development of the game!"
toc: 
---

{{<image width=100% maxwidth=100% src="/images/bonerollabanner.png">}}

## Overview
This game was made during the summer period leading up to my first semester of college, and features a number of roguelike and RPG elements blended together into an interesting dice-based deckbuilding experience. The idea of the game is that players can find modified versions of familiar dice commonly used in tabletop gaming such as a Lucky D8 that only contains the upper half of the die multiplied twice, in one of three different dice types. These are represented in the form of dice with weapon names for damage, dice with equipment names for armor, and dice with spell names for healing. This game also marked my first attempt at composing and producing music, which continued on as a personal hobby ever since I picked up the skills necessary for making the music in this game.

{{<image width=100% src="/images/bonerolla1.png">}}

## RPG Mechanics
Beyond just having deckbuilding mechanics in obtaining and trading for new dice, I wanted a sense of continuous progression in the form of a leveling system for Bone Rolla. I also wanted a simple gold and shop mechanic that is common in RPG games as well, which facilitates a consistent way for players to ensure they can obtain and remove dice as they need during their run. Finally for my bullet point list of desired RPG mechanics, I wanted a breadth of enemies with differing kinds of strategies that are optimal for fighting them, the game currently has over 30 unique types of enemies to come across.

### Level Up System

The level-up system in the game is based on a hidden experience point attribute that differs between types of enemies. Every 2nd level the player is offered a choice between three random feats out of a pool of 18 total feats to find and obtain, varying in bonuses and designed to have synergies between other feats and specific dice modifiers.

{{<image width=100% src="/images/bonerolla2.png">}}

## Roguelike Mechanics
The primary goal of the project was focused on making a fun roguelike game, so the deckbuilding mechanic and surrounding mechanics that help facilitate it became the core of the game idea.

### Random Encounters
To provide more variety between combat encounters, I went with a simple implementation for a randomly revealed story type of event system. This example shows the conclusion of an event room with unidentified mushrooms that may or may not be beneficial to the players' survival. Before choices are made, each section would contain multiple choices to pick from that lead to a variety of outcomes, such as the one depicted here.

{{<image width=100% src="/images/bonerolla3.png">}}

### Path Choice
Between either random or combat encounters, the player gets a choice between a varying amount of options on where to go next. Sometimes there is a breadth of options for the player to make tactical decisions such as offloading gold for dice at the trader, or chancing a random event for a lucky item where they might just receive a cursed one instead. Then sometimes, it is fate that the critically low healthed player is backed into a corner of taking the only option before them of a combat encounter. This felt like it tied together well the rest of the encounter systems and the trading system to really complete the game loop.

{{<image width=100% src="/images/bonerolla4.png">}}
