---
layout: post
title: Dreamlands Update - Refactor
image: /img/dreamlands-2.png
---

# Last Week

Last week I talked about what I have accomplished on that week and what the next milestone was going to be, now I will talk about how things turned out!

# This Week

Keeping things short, I created the first build which is a HTML5 build and just uplodead it on itch.io! Play it on [itch.io](https://fourthdimension.itch.io/dreamlands) - Feel free to play it and leave any feedback!

I had a list of things that changed and got into this build:
* **Boss Logic:** I created a very simple boss logic that just follows the players, also all the map logic (i.e. locking and unlocking doors and stairs on the room) and now the music changes on the boss fight.
* **Poor Dungeon Logic:** There is a very simple manager that just tracks how many floors you went down.
* **Pattern Enemies:** I have developed a script that I can use to create monsters that moves in patterns, not reacting to player input, which already leads to an interesting variety of room possibilities.
* **More Templates!** Enemies room now can use 5 different templates, all chosen randomly!

# Refactoring

A major refactor process started immediately after creating the WebGL build, the main goal is to divide the Level Generation System and the Turn Based Combat System. The Level Generation is pretty much done and I scrapped it and made it its own thing, I'm thinking on working on it and publishing to the Unity Asset Store, so I can try earn something to fund Dreamlands.

The Turn Based Combat system still has a lot to go through, the GameManager also has a lot to go through, the Game Manager will mainly link both systems, as I'm trying to make each one of them totally independent of the other.

# Alpha Milestone

Again, the Alpha Milestone (November 2nd) goal is to work on design, art, sound and some early programming polish.

I'm creating some tasks for it and here are some of them:
* **Fixes:** Should the rooms the player still didn't explore on the minimap.
* **Art:** Define a color palette, add particle systems.
* **Systems:** Refactor the combat and level systems, create a better stats system, fine tune the turn based system, have a progression (leveling up), weapons and shops.

----------------

I will keep this update short, if you are reading it and want to know something more specific you can reach it me on [Twitter](https://twitter.com/studio_fourth), on email (contact@fourthdimension.studio) or you can just comment on the comments section below!

Also if you have any early feedback or any consideration, also feel free to contact me.
