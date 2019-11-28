---
layout: post
title: Turn-Based System for Aglarond
image: /img/aglarond/cover.png
---

A traditional roguelike is very tied in with a Turn-Based Combat System, the combat system I was developing for Aglarond was the result of the iteration on three projects: Dreamlands, a "Mobile Roguelike" and Aglarond. Aglarond is no longer under development, so I decided to write this post about how the turn-based system works. 

![Combat System](/devlog/img/aglarond/gifs/final_view_aglarond.gif)

[Actions speak louder than words, code speak louder than any blog or tech post, Aglarond is now open source](https://github.com/fourthdimensionstudio/Aglarond)

## Combat System Overview

![Combat System](/devlog/img/aglarond/tbs-diagram.png)

The idea is actually pretty simple, the Turn-Based Manager holds a reference to all Actors that are going to take a turn, and every frame the manager queries the actor like: "Hey, did you take a turn yet?" - For that the actor could say yay or nay. For example, enemies always take a turn, but there can be a situation in the future where an enemy thinks too much with its behavior tree and takes more than a frame to take the turn, and the player only returns "yay" when the actual player (you) presses a key to move the character, while that doesn't happen, the hero always say "nay" to the query.

```
private void ProcessCurrentActorTurn() {
    if(m_dynamicActorsOnScene[m_currentActorTurn].HasTakenTurn()) {
        if(m_dynamicActorsOnScene.Count > 0) {
            m_currentActorTurn = ((m_currentActorTurn + 1) % m_dynamicActorsOnScene.Count);
        }
    }
}
```

Here's the simple game loop for the turn based system.

After receiving a "yay" a bunch of processing happens, the actor checks for collisions, for combat and let the manager know about all that, so that it can be handled correctly, after all that, the movement is resolved, resulting in a movement, a combat action or a movement denied.

### Everything is in memory

The turn based manager keeps everything in memory, the game screen is just a representation of everything that is happening, it is kinda like there is parallel game running in the memory. So when checking for a combat collision, the actual scene is not used, here's how it is done:

```
public bool IsThereAnActorAt(Vector2 _positionToCheck) {
    foreach(Actor.DynamicActorComponent dynamicActor in m_dynamicActorsOnScene) {
        if(dynamicActor.CurrentPosition == _positionToCheck) {
            return true;
        }
    }

    return false;
}

public Actor.DynamicActorComponent WhatActorIsAtPosition(Vector2 _positionToCheck) {
    foreach(Actor.DynamicActorComponent dynamicActor in m_dynamicActorsOnScene) {
        if(dynamicActor.CurrentPosition == _positionToCheck) {
            return dynamicActor;
        }
    }

    return null;
}
```

### Exploring

The Hero contains two very important things to help exploration: a Field of View and an enemy detection range.

```
public override bool HasTakenTurn() {
    if(m_currentMovementDirection == Input.EMovementDirection.NONE) {
        return false;
    }

    Move(m_currentMovementDirection);
    m_fieldOfView.RefreshVisibility(m_currentPosition);
    return true;
}
```

Here's how the Hero's turn look like.

And a little bit more insight on how the Move function looks like:

```
public void Move(Input.EMovementDirection _movementDirection) {
    Vector2 movementDirection = Input.InputUtilities.GetMovementVectorFromDirection(_movementDirection);

    // Handling Combat
    bool willEngageInCombat = WillEngageOnCombatOnMovement(movementDirection);
    bool canMoveOnDirection = false;

    // Handling Movement
    if (!willEngageInCombat) {
        canMoveOnDirection = CanMoveOnDirection(movementDirection);
    }

    Move(movementDirection, canMoveOnDirection, willEngageInCombat);
}
```

The Enemy Detection is what handles checking enemies that are in range and either adding or removing them from the turn list that is processed on the turn-based manager. Sounds like a weird trick, but it works.

This is just some very basic and a very high overview of this turn-based system, [the specifics can be seem on the actual repository](https://github.com/fourthdimensionstudio/Aglarond) and you can always ask me something on [Twitter](https://twitter.com/guilhermepo2)!
