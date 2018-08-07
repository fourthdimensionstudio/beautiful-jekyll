---
layout: post
title: GameMaker vs. Unity
image: /img/m3rl-rl.png
---

I'm moving the Puzzle Game from GameMaker to Unity. In order to answer the question "Why are you moving the Puzzle Game from GameMaker to Unity" I have to address my impressions on both of them, what they are good at and what they are not so good at.

### A little bit of story

Early 2017 I started developing my first game, *Midnight Journey*, it is an Action RPG heavily based on *Zelda: A Link to the Past* and the *Souls* series, I *know* Souls are based on Zelda, but they are not the same and it's ok for me to draw inspiration from both of them.

Anyway, I developed a prototype in about a month and kind of struggled while doing this, the result wasn't good. Tha's when GameMaker Studio 2 kicks in. I got to try GameMaker while following a course on developing an ARPG (very convenient) and GMS2's strengths were **obvious** comparing to Unity.

**GMS2 Advantages (or Unity Disadvantages)**
1. **Tiles:** At the time Unity didn't have a Tileset, so using it on GMS2 was, by itself, a good enough reason to change engines. Tileset for Unity eventually arrived, but to this day, GameMaker's tiles are better and easier to use.
2. **Performance:** Unity always had that *unity*-like performance, FPS drops was not uncommon, input lag and a general *stuck* feel. GameMaker had, out of the box, a really smooth performance, so that was also a huge bonus. I **know** all the problems on Unity performance related can be solved by doing proper configurations and, well, good code, but this wasn't a simple task for the early 2017 me, and it isn't for a lot of people.
3. **GML:** GML is way more simple than C# so developing something is easier and faster, who doesn't like easier and better stuff?
4. **Ease of Use:** Doing everything on GameMaker seemed easier.

Sounds like a God sent engine, right?

Well, no. GMS2 has its problems, and there are lots of problems (Just as Unity also has a lot of problems, and also everything and everyone else)

As stated by **Heartbeast** in [this great video](https://www.youtube.com/watch?v=glPFa0_O-s8) at (4:26). GameMaker is an incredibly good engine for: (i) small 2D games with interesting mechanics, (ii) which does not have complex systems that interact with each other and (iii) which doesn't have a lot of UI. Basically, Platformers, Shooting Platformers, Metroidvania, Action RPG, this kind of things.

So, as I heard on the podcast **Coffee with Butterscotch**, GameMaker is a great tool if you do what it expects you to do. You can't try to use it for something it wasn't designed for as it is the same for any tool, right?

This made me get back to unity progressively and know I'm kind of using both, but this project I'm moving it to Unity.

**So what Unity does better? (or what GMS2 does worse)**
1. **UI:** I used to **hate** the canvas and everything UI-related on Unity, but now I *know* how to use it and I have to acknowledge how good it is.
2. **Complex Systems that interacts with each other:** C# and Object Oriented Programming allows that as it is a more powerful programming tool than GML.
3. **Exports:** Unity is famous for being able to put your game everywhere, and that's awesome.

**What to conclude?**

**GameMaker** performs good in games on these aspects: (i) small 2D games with simple yet interesting mechanics, (ii) not lots of complex systems interacting and (iii) not UI heavy. Being more specific: platformers, action rpg, even metroidvanias and rpgs with not much complexity, and **prototyping**. 

If the game will have bigger systems such as progression system, skill trees, all those heavy rpg stuff you should probably not be using GMS2. But consider it for prototyping is *ALWAYS* a good idea.

**Unity** performs better where GMS2 performs worse (duh.) and when you want to use its powerful export system. Unity also performs good on the strong points of GameMaker, but it can be a bit harder and slower to do something simple on Unity and it will perform not as good.

I love both engines and will be using both, but from now on I will be using more Unity as my games are either mobile (I don't have the mobile license for GameMaker) or *do* have those systems that interacts with each other. But I still want to have a platformer or ARPG done on GameMaker.
