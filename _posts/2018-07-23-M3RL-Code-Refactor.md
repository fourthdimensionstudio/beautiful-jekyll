---
layout: post
title: M3RL Code Refactor
image: /img/m3rl.png
---

Something that was on the backlog for a long long time was to implement the data persistence between the dungeon exploration and the "puzzle battle" from the **Match 3 Roguelike** game. Don't worry, it's a teporary name.

It was 2 long days of anxiety and "How to do this?" - The best, fastest and most secure way was to perform a major refactor on the code. Oh well, that happens. But it took only a morning, so two days avoiding to do it proved to be a total waste.

## How it was before?

Before the refactor there were 2 objects, the **Puzzle** object and the **Dungeon Exploration** object. It doesn't take much to realize that it doesn't make a lot of sense, these object simply can't handle all the information of the game.

What about the progression? Data Persistence? Statistics?

None of those things could be handled with just two objects, so the most sensible thing to do was to create the **GameManager**. This is a bit obvious since almost all games, at some point, will use a centralized Game Manager

## How it is now?

Well, I already said it.

There is the **Game Manager** holding all information related to progression and data used by the board and by the dungeon exploration part that might be changed in the future.

Let's look at some code.

```
// Level is the current floor
m_level = 1;

// STATISTICS
m_enemiesDefeated = 0;
m_damageDealt = 0;

```

If these statistics variables are going to really be used is yet unknown. The most important variable of the game is the level/floor, which is used as a base to calculate the difficulty of the game (puzzle velocity and, in the future, tune the Enemy AI).

For the Dungeon Exploration Part:
```
// Room Generation Related
m_roomWidth = 480;
m_roomHeight = 480;
m_tileSize = 32;
m_roomTileSizeWidth = m_roomWidth div m_tileSize;
m_roomTileSizeHeight = m_roomHeight div m_tileSize;
m_levelSteps = 15;
m_initialSquadX = m_roomTileSizeWidth div 2;
m_initialSquadY = m_roomTileSizeHeight div 2;
m_regenerateBoard = false;
GenerateBoard();

```

This is all the variables needed to generate the board, its size, the tile size for it to be rendered, where the player will start, how many 'blocks' are going to have and so on...

The script **GenerateBoard()** is also something that was changed, it wasn't a script and it is way better like this.

Finally, for the Puzzle Part.

```
m_maxTilesWidth = 6;        // fixed
m_maxTilesHeight = 9;       // fixed
m_piecesAmmount = 5;
m_initialBlockAmmount = 15;  // maybe can vary through the gameplay
m_enemyMaxLife = 30;
m_baseRowSpeed = 10;
m_speedIncreasePerLevel = 0.5;
m_minSpeed = 2;
```

Every information necessary to initialize the puzzle and increase its difficulty (how many blocks there will be at the beginning, enemy max life, speed progression, initial speed, etc...).

Max tiles width and height are there so I can easily play with these values later according to feedback. Panel de Pon, Tetris Attack, Pokemon Puzzle Challenge use 6 for width and *usually* 9 for height.

That was the major refactor!

The next step is to write the **Garbage System**, which will also have its own post on this devlog, this system is the most important part of the puzzle, where the challenge will be together with the increasing speed.

Hope you enjoyed the post!

You can always reach us on [Twitter](https://twitter.com/studio_fourth).

There's not much there right now as Fourth Dimension is just starting and the visual identity is still being created, but soon there will be more!

Have the nice day I'm sure you will have because I've already seen it from the Fourth Dimension.
