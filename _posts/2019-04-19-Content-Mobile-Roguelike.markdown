---
layout: post
title: Creating Content for a Mobile Roguelike
image: /img/mobrogue/mobrogue2.png
---

Last post I've talked a little bit about the Mobile Roguelike I'm currently working on and I'm aiming for it. As the name implies, this is a game that is, well, mobile and a roguelike! There's a very raw prototype you can play on [Fourth Dimensions' itch page](https://fourthdimension.itch.io/mobile-roguelike) and it will be a full mobile game app, with in game store, in app purchase, achievements, leaderboards and lots, lots of content!

## Creating Content

Last week was all about focusing on Game Design Documents, Designing the game itself and effectively creating enemies and hazards to have enough game content so it can be a more appealing game. I have currently 6 enemies and 7 hazards coded, and that's what I will be talking a little bit about today. They are all with temporary sprites and I still have 5 enemies and 1 more hazard to code, when I do then I shall write another post! And then another post when I have more definitive sprites!

### Enemies

![Slime](/devlog/img/mobrogue/GIFS//20190419/en_slime.gif)

**Slime**

The slime is the most simple and stupid enemy of the game, it does not do any harm to the player, but it might look cute.

![Imp](/devlog/img/mobrogue/GIFS//20190419/en_imp.gif)

**Imp**

The Imp is the second most simple and stupid enemy of the game, it can offer a little bit of harm if the player is unaware, does not look cute.

![Skeleton](/devlog/img/mobrogue/GIFS//20190419/en_skeleton.gif)

**Skeleton**

The Skeleton does whatever it wants. As dead entities, they decided not to not agree upon the rules enforced by the game and there's nothing I can do about it. But luckily, as they are skeletons, they don't live that much.

![Goblin](/devlog/img/mobrogue/GIFS//20190419/en_goblin.gif)

**Goblin**

The Goblin is the first enemy that reacts to whatever the player does, he is not the smartest doing that, but still, he tries his best.

![Anti Player](/devlog/img/mobrogue/GIFS//20190419/en_antiplayer.gif)

**Anti Player**

Basically the dark and opposite side of the player!

### Hazards

![Ice Tile](/devlog/img/mobrogue/GIFS//20190419/hz_icetile.gif)

**Ice Tile**

You know, sometimes random parts of the ground can freeze, it happens. A gif doesn't do much to show what effectively is happening, but the Ice Tile forces you to take the same movement you've taken the last turn.

![Misdirect Tile](/devlog/img/mobrogue/GIFS//20190419/hz_misdirect.gif)

**Misdirect Tile**

You shall not step on them.

![Movement Blocker](/devlog/img/mobrogue/GIFS//20190419/hz_moveblocker.gif)

**Movement Blocker**

Not sure what exactly this is going to be, it blocks the movement of an Actor for 1 turn, a gif like this doesn't do much in order do showcase it.

![Moving Hazard and Spawner](/devlog/img/mobrogue/GIFS//20190419/hz_movinghazard.gif)

**Fireball Moving Hazard and Spawner**

Sometimes the danger can also move, the moving hazard is the fireball, the "monster" is a temp. sprite for the moving hazard spawner (which in this case is something that throws a fireball) and they **cannot** be attacked! In the future I plan to add enemies that casts these moving hazards.

![Vanishing Tile](/devlog/img/mobrogue/GIFS//20190419/hz_vanishing.gif)

**Vanishing Tile**

The dungeon is dangerous, duh. Beware of falling ground. Anything can be below it! Just another regular ground or maybe another hazard!! Or maybe nothing!

## Future Content

That's not all the content the game is going to have! Here is a quick list of things I want to add the next days:

### Hazards
* **Frostbolt:** Moving Hazard that deals freeze, which blocks movement for 1 turn.

### Enemies
* **Charge Enemy:** It loosely follows the player, when it is on the same axis as the player (either horizontal or vertical) it locks its movement on a direction trying to hit the player, the enemy is locked until it hits something.
* **Search Algorihtm Enemy:** All the enemies that react to the player has a pretty dumb algorithm, I want to make a base enemy that has a smarter way to track the player in order to do stronger enemies (the ones below).
* **Bomber Goblin:** Follows the player, with a bomb! But it accidentaly explodes after some turns (case area damage).
* **Mimic:** Pretends to be a chest. Has to be waken by the player.
* **Pyromaniac Goblin:** Stays at a safe distance from the player, throws fireballs.
* **Ice Elemental:** Stays at a safe distance from the player, throws frostbolt.

That's pretty much it for these last days working on the game, planning and creating enemies and hazards!

This was another short update on the status of the Mobile Roguelike I'm currently developing, I'm not sure when it will hit the stores because I'm working on the core gameplay, but ideally it won't take _too long_. You can expect more updates in form of tweets and devlogs from now on!

Follow Fourth Dimension on [Twitter](https://twitter.com/studio_fourth) for frequent retweets on Freshman's Quest and some ocasional tweets about other projects!
