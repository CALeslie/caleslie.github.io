---
title: "Deep Cover"
#date: 2021-04-03T22:53:58+05:30
draft: false
github_link: "https://github.com/gurusabarish/hugo-profile"
badges:
  - Unity - C#
  - Gameplay Programming
  - Raster Editor
  - Stealth Mechanics
imagelink:
  enable: true
  link: /projects/deep-cover
image: /images/deepcover.png
#banner: /images/mallanebanner.png
description: ""
summary: "Stealth based game with camo raster editing system, match your camo to your surroundings to avoid being caught! Click 'Read more' to learn about my involvement!"
toc: 
---

{{<image width=100% maxwidth=100% src="/images/deepcoverbanner.png">}}

## My Involvement

This game was made during my freshman year at college as my first gamejam submission to my universities' semesterly gamejam events. I handled all of the programming and implementations within Unity, while my partner helped with the art and design of the game.

## Camo System

This system works together with a few central parts, namely the raster editor for painting a canvas that is then applied to the player sprite using a custom masking system. This is then checked for color accuracy to the background behind the player before informing the enemy detection system how big or small their detection radius should be.

### Raster Editor

At that time we were studying how to make raster editors in Python using the Pygame library so I wanted to extend that implementation into my gamejam project, with my partner coming up with the idea to tie it into stealth mechanics by letting player's paint their own camo, and testing to see how much it matches the background behind them.

{{<image width=100% src="/images/deepcover1.png">}}

### Masking Player Camo

In order to better convey the act of camouflaging up, I wanted to do more than just apply the sprite behind the player's silhouette mask. I wanted the player-made camouflage to stay stationary while the player freely moved around, evoking a style similar to some cartoons from the late 90's and early 00's.

{{<video width=60% src="/images/deepcover2.mp4">}}

### Enemy Detection

As previously mentioned, the accuracy of the player's handpainted camouflage to the background behind the player modifies the detection radius for the Enemy AI in the game. In this GIF you can see the demonstration by seeing the difference in detection range from the enemy between the good and bad camouflage choices.

{{<image width=100% src="/images/deepcoverdetection.gif">}}

## Enemy AI

Since this was a gamejam project the Enemy AI is fairly simple, there are only two types of AI to encounter in this game. The first is the stationary guard, these enemies will stand still in a single area and rotate between set points after given intervals.

{{<video width=100% src="/images/deepcover3.mp4">}}

The other type of AI is the patroling guard, this type of enemy will move between given positions in an array of vectors, and they always look in the direction they are moving.

{{<video width=100% src="/images/deepcover4.mp4">}}