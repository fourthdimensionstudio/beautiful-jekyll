---
layout: post
title: Tiles and Field of View for Aglarond
image: /img/aglarond/cover.png
---

One of the base core features of a good (or any) roguelike is a tile based map and movement system and, of course, the field of view, limiting what the player can see is what gives us the satisfactorily feel of exploring a dungeon, it is always more fun when you don't know what is lurking around the corner, right?!

![Field of View](/devlog/img/aglarond/gifs/20191006_fieldofview.gif)

For this post I want to address a little bit of my process about doing the tiles and the field of view for Aglarond, the roguelike game I'm currently developing!

### What went wrong?

First I want to talk a little bit about what actually went wrong when trying to make tiles for a roguelike game, it seems like an easy and simple task, right? Shouldn't be hard.

At first I had the dungeon generation using the Unity Tilemap system, it was an easy and pretty solution because I could in the future use RuleTile, from their 2d-extras, and have all the tiles nicely sorted out without much effort. But unfortunately, that was not the case.

The question here is: **What does a roguelike need from their tiles?** - And the answer is: **The tiles need to be individual objects that can be either visible, not visible or not discovered**. And the problem is that Tilemaps are not a solution built for treating each tile as an individual object, they are a solution for static environments, basically it is a tool for easier 2D Level Design. I tried extending the base tile class and creating my own in order to have a tile with those characteristics and it wasn't possible, that's ok because the tilemap tool is not what we want to solve this problem, it simply was not designed for this use-case and that's fine.

### What went right?

My solution was much less elegant and possibly way more expensive for memory and cpu, you probably guessed already, I created a script for a single tile, which means that every tile is a GameObject in Unity! This gives us what we want: being able to access each individual tile and verify or change their state as visible, not visible or not discovered. Here is the variables I'm using:

```
[Header("Sprites for the Tile")]
public Sprite totallyVisibleSprite;
public Sprite partiallyVisibleSprite;
public Sprite nonVisibleSprite;

[Header("Colors for Sprite")]
public Color totallyVisibleColor;
public Color partiallyVisibleColor;
public Color nonVisibleColor;

[Header("Sorting Layers")]
public string visibleSpriteMask = "Default";
public string partiallyVisibleSpriteMask = "Default";
public string nonVisibleSpriteMask = "Default";
```

**Why the Sorting Layers?** When the tile is partially visible (i.e. tile was discovered but player cannot see it) and when the tile was not discovered at all we want enemies, items, treasures and everything to **not** be visible to the player, because that's how life works, when you can't see something, you cannot see it! So the sorting layers are adjusted in real time to be hide everything the player should not be seeing.

There is a couple more variables for `tilePosition`, `tileVisible`, `tileDiscovered` and `isWall` and a cached reference for the tile's sprite renderer. But with all that addressed, a function to update the tile according to its current state should be provided.

```
public void UpdateTile() {
    if(m_isTileVisible) {
        UpdateSpriteRenderer(totallyVisibleSprite, totallyVisibleColor, visibleSpriteMask);
    } else if(m_wasTileDiscovered) {
        UpdateSpriteRenderer(partiallyVisibleSprite, partiallyVisibleColor, partiallyVisibleSpriteMask);
    } else {
        UpdateSpriteRenderer(nonVisibleSprite, nonVisibleColor, nonVisibleSpriteMask);
    }
}

private void UpdateSpriteRenderer(Sprite _sprite, Color _color, string _sortingLayer) {
    m_spriteRenderer.sprite = _sprite;
    m_spriteRenderer.color = _color;
    m_spriteRenderer.sortingLayerName = _sortingLayer;
}
```

### But where do we update the tiles?!

Ha! Nice question! The field of view algorithm I'm using is an adaptation for Unity from this [article here](http://journal.stuffwithstuff.com/2015/09/07/what-the-hero-sees/). I recommend you to take a look. It is a shadowcast field of view and the algorithm translates pretty well, the only work I had was to adapt the syntax. The algorithm to refresh the octant ended up as the following:

```
private void RefreshOctant2(Vector2 _originPosition, int _octant) {
    ShadowLine line = new ShadowLine();
    bool fullShadow = false;


    for(int row = 1; row < km_maxDistance; row++) {
        for(int col = 0; col <= row; col++) {
            Vector2 position = _originPosition + ConvertPositionToOctantPosition(row, col, _octant);
            Dungeon.DungeonTile currentTile = m_dungeonGeneration.GetTile((int)position.x, (int)position.y);

            if(currentTile == null) {
                continue;
            }

            if(fullShadow) {
                currentTile.IsVisible = false;
            } else {
                Shadow projection = ProjectTile(row, col);

                // Setting Visibility of this tile...
                bool visible = !line.IsInShadow(projection);
                currentTile.IsVisible = visible;
   
                if(visible) {
                    currentTile.WasTileDiscovered = true;
                }
                        
                if(visible && currentTile.IsWall) {
                    line.AddShadowToLine(projection);
                    fullShadow = line.IsFullShadow;
                }           
            }

            currentTile.UpdateTile();
        }
    }
}
```

The biggest headache on all of this story though, was on the function `Shadow ProjectTile(int _row, int _col)` - in my head, this function had to return the tile that was being ommited by the shadow, but this is **not true**, I literally lost 2 days trying to figure this out, the algorithm has to return a Shadow that is indicated by two floats, forming a slope, which indicates the direction of the shadow, and **that** is used to see which tiles are visible or not!

Here is how my `ProjectTile` function ended up.

```
private Shadow ProjectTile(int _row, int _col) {
    // forcing row and col to be float so we don't get bamboozled by int/float conversion somewhere
    float row = _row;
    float col = _col;

    float topLeft = (col / (row + 2));
    float bottomRight = (col + 1) / (row + 1);

    return new Shadow(topLeft, bottomRight);
}
```

As you can see, my biggest problem was trying to convert everything to an integer, to improve legibility I created float variables and added a comment for my future self to prevent me from commiting the same mistake, with all that, the field of view algorithm worked nicely enough for me!

This post I wanted to address how I went about creating tiles and making the field of view for **Aglarond** the roguelike game I'm currently working on, **Aglarond** is scoped as a 2~3 months project, but as life happens and I have to take care of Masters and Capstone stuff, I expect it to actually take 3~4 months, but you can always keep an eye on this blog for more posts or you can follow me on [Twitter](https://twitter.com/guilhermepo2) for ocasional updates and random posting about games!

With anything on this post was not clear and you want to know more, also feel free to reach me on twitter or by email!