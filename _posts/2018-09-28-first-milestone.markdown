---
layout: post
title: Dreamlands Update - Gameplay
image: /img/dreamlands-2.png
---

# Last Week

Last week was actually my very first post about Dreamlands, you can read it [here](https://fourthdimension.studio/devlog/2018-09-21-what-is-dreamlands/). I briefly talked about what this project is going to be, what I want to achieve, my vision, pricing, hours of work, etc... But now it is time to talk about the game itself and its progress.

# This Week (First Milestone)

At this point the game looks like this:

![Dreamlands](/img/dreamlands-2/room1.png)

![Dreamlands](/img/dreamlands-2/room2.png)

I won't upload any videos at this point yet because every art is a placeholder and I'm working solely on mechanics and some early polish to get the game feeling good and juicy.

This is a list of the core mechanics that were coded:
- **Procedural Map Generation:** The map is generated creating different rooms and these rooms are randomly picked from a random template - there are different types of rooms, currently there is the starting room, regular enemy room and boss room - each one with their own templates.
- **Player Movement**
- **Simple Enemy Behavior**
- **Simple Boss Behavior:** Which pretty much works like an enemy, it just overrides the regular stats with stronger stats and override the movement logic
- **Simple UI:** Showing player health and handling when it reaches to 0.

**First Milestone:** October 5.

By this date I want to have a gameplay demo totally done, as I said on previous post, it will be on itch.io and I will start asking for early feedback before heading into alpha development.

**Backlog for Next Milestone:**
- **Boss Logic:** Although the boss is pretty much working I have to code the boss room behavior, that means locking the door when the battle starts, having a stair on the room and blocking it until the boss is not defeated. Also the boss battle will have a different music from the rest of the game, so I have to write a routine to fade out the old music and fade in the boss music.
- **Dungeon Logic:** The Level Generator works correctly but there isn't yet some kind of manager that tracks how much floors the player went down, this needs to be done and the floor will reflect on the overall difficulty of the game.
- **Enemies and Bosses:** The basic script is working, but I still need to create effective monsters and bosses, each one with their own moveset, characteristics, strenghts and weaknesses.
- **More Templates:** The rooms with enemies currently uses just 1 template, I should have at least 10 to have a somewhat interesting variation.

**On Backlog but Might Not Make it:**
- **Hazards:** Ground on fire, ground with ice (so the player and enemies would slip), traps that would require you to think on the turn based system...
- **Leaf Rooms:** Leaf Rooms are those rooms with only one connection, the boss is in one of those. Also there is the option to have a reward room or a shop on these, but this is definitely not going to be in the MVP.

This backlog are ideas that are not discarded but probably won't make for the next playable version of the game.

# Next Milestone

After October 5th - The second Milestone begins - This is where production really begin and I will call it Alpha Stage, the goal is to have the Alpha Version by November 2nd.

If you didn't notice the pattern, I'm making each iteration have around 1 month and finishing it on the first Friday of each month.

**Alpha Milestone Main Goal:** The goal of this milestone is to work on the aesthetics, design, art and sound mainly, some programming polish will be around but all the major systems should be nearly completed at this point.

To get the aesthetic correctly I'm researching a lot on Lovecraftian Horror and grasping the essentials, I also made a Lovecraft reading list, I've read some of them before but reading it again won't hurt.

The List:
- The History of Necronomicon
- The Call of Cthulu
- The Whisper in the Darkness
- The Shadow Out of Time
- At the Mountains of Madness
- The Lurking Fear
- The Colour Out of Space
- The Dunwich Horror
- The Outsider
- Dagon

----------------

I will cut this update here, if you are reading it and want to know something more specific you can reach it me on [Twitter](https://twitter.com/studio_fourth) or on email (contact@fourthdimension.studio) - Also if you have any early feedback or any consideration, also feel free to contact me. Something I want to write about in the future is about the Turn Based Combat I've developed, but I want to test it some more before effectively putting it out there.

The biggest point on this game is that I want to really listen to the community, mainly the roguelike niche players to have a really good game that adds to the community!

Thanks for reading this blog post, and hope to see you more! I will be writing here weekly and almost daily on [Twitter](https://twitter.com/studio_fourth).