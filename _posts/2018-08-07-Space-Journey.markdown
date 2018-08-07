---
layout: post
title: Space Journey
image: /img/Hi-Res.png
---

Space Journey is a simple game inspired on Flappy Bird. What makes it different is that, as it happens on space, the game feel is a little bit more *floaty*, this was achieved by using a smaller gravity value, forces with a small value and using sounds on smaller frequencies.

The game was made in Unity 2018.2f and can be found on [play store](https://play.google.com/store/apps/details?id=com.FourthDimension.SpaceJourney).

This is some kind of a postmortem.

## What went right?
1. The first that went right was using **GitHub Projects** for organization, it is a very simple Kanban style board that is very helpful, the boards were also something that went right, it is divided in Backlog/This Week/Today/Done, instead of the usual To Do/Doing/Done.
2. Adding *Juice* made the game extremely more pleasant, things such as the screen shake when the core hits a satellite, the screen flash at the same time, animations for the game over menu and for the core when the screen is idle (on the menu screen and the "Tap to Start" screen)
3. Using Mathf.PingPong() and Sin/Cos to make the space core move on the main menu screen and on the "Tap to Play" screen. These functions are great to achieve the "floaty" feel, as their forms are basically waves.
4. Overall it was a very good experience on designing menus, because everything has to be interesting and simple as the game is so simple.

An interesting thing I would like to share, is the core rotation, it rotates in a funny way that I achieved while testing a lot of different types of rotation, I liked it so it stayed in the game.

The code is as simple as:

```
// rotate the core
if(m_rigidBody2D.velocity.y >= 0) {
	t_angle = Mathf.Lerp(m_rigidBody2D.transform.localEulerAngles.z, 30, m_rigidBody2D.velocity.y / 16f );
} else {
	t_angle = Mathf.Lerp(m_rigidBody2D.transform.localEulerAngles.z, -90, - m_rigidBody2D.velocity.y / 256f );
}

transform.rotation = Quaternion.Euler(0, 0, t_angle);
```

The values `16f` and `256f` were achieved by testing.

## What went wrong?
1. **Pixel Art:** Drawing the GUI buttons with pixel art is something that I'm not sure went right, not sure either if the color really matches the identity of the game, it might change in a future update.
2. Also, working with pixel art makes it harder to create icons for Play Store (512x512 and 1024x500 is required) - luckily enough, Photoshop has a very good canvas resize property, using it with the nearest neighbor method make the pixel art be as good in 256x256 as it was on 32x32.
3. **Sound:** As I said, the sound is more on low frequencies and I was doing them using headphones, what happened is that some sounds are hard to hear on a cellphone without using headphones, I'm even using 1.5 as pitch but it didn't change much.

As a Flappy Bird similar, there is not much to add, the development happened throughout 5 or 6 days, the main mechanic was built entirely in a single day, the others were dedicated to polish, juiceness, sound, art, etc... So, always remember the 80/20 Rule.

So that's about it! Have a good day and follow Fourth Dimension on [Twitter](https://twitter.com/studio_fourth)!
