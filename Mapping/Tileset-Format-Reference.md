# Tileset Format
Vanilla tilesets are comprised of a series of "Masks": descriptions of the configuration of surrounding tiles that are used to pick the texture for a tile.

A tileset xml node is structured as follows:
```xml
<Tileset id="X" path="path/from/(Gameplay/tilesets)">
   <set mask="x0x-111-x1x" tiles="0,0"/>
   <set mask="padding" tiles="0,1"/>
   <set mask="center" tiles="1,0;1,1"/>
</Tileset>
```

### Let's break down each line:
---
```xml
<Tileset id="X" path="path/from/(Gameplay/tilesets)">
```
The beginning of the Tileset definition, where: 

`id` is the character used to represent this tile in the map binary
`path` is the path to the tileset image relative to `Gameplay/tilesets`

---
```xml
<set mask="x0x-111-x1x" tiles="0,0"/>
```
This is standard mask definition for a tileset, and will be used for the outer-most tiles.
The `mask` attribute describes a 3x3 square of tiles with the center tile representing the one currently being analyzed.  
Characters accepted in vanilla masks are:  
`1` - Presence of a tile  
`0` - Absense of a tile  
`x` - Any  

---
```xml
<set mask="padding" tiles="0,1"/>
<set mask="center" tiles="1,0;1,1"/>
```
These define the inner layers of the tileset, with `padding` describing one layer in from the outer tiles, and `center` describing everything else.

# Everest Features

Everest adds a few new features to custom tilesets as described below from [this pull request](https://github.com/EverestAPI/Everest/pull/241).

Instead of just padding and center inner layers, any number of fill layers can be defined:

```xml
<set mask="fill0" tiles=""/>
<set mask="fill1" tiles=""/>
...
```
Custom mask scan width/height can be set with attributes on the Tileset node:
```xml
<Tileset scanWidth="5" scanHeight"5">
```

The `y` filter can be used in a mask to mean "any tile that isn't this one".  
Custom filters can also be defined to be used in masks:
```xml
<define id="a" filter="4,5" ignore="true"/>
```
where:

`id` is the character to use in the mask.  
`filter` is the tileset ids to add to the filter.  
`ignore` determines whether the ids are whitelisted or blacklisted.


# AnimatedTiles
AnimatedTiles are textures that can be added to a tileset mask, and are displayed when that mask is used. They are used in vanilla for the wavy grass strands on the Grass and DeadGrass tilesets.

To add AnimatedTiles to one of your map's tilesets, a similar process must be followed for setup:  
- Retrieve the `AnimatedTiles.xml` file from `Content/Graphics/` in your Celeste folder.
- Copy the `AnimatedTiles.xml` into the same folder you put your other tileset xmls.
- In Ahorn, copy the path to your `AnimatedTiles.xml` into the "Animated Tiles" field in the Map Metadata window.

AnimatedTiles can be added to the xml as follows:
```xml
<sprite name="sprite_name" path="path/from/Gameplay/folder" delay="0.2" posX="0" posY="-8" origX="4" origY="4"/>
```
where:

`delay` is the animation speed.  
`posX` and `posY` are the position relative to the tile.  
`origX` and `origY` are the origin of the sprite.

To add an AnimatedTile to a tileset mask, add the `name` of the AnimatedTile to the `sprites` attribute of the mask in your `(Fore/Back)groundTiles.xml`:
```xml
<set mask="x0x-111-x1x" tiles="0,0" sprites="sprite_name"/> 
```
Multiple AnimatedTiles can be added to a mask, separated by commas, and will be chosen from randomly.

:information_source: AnimatedTiles are only displayed for Solid Tiles by default, and will not show up on most tile entities (DashBlock, CoverupWall, etc...)  
:warning: AnimatedTiles currently do not work with BackgroundTiles, however this may be added by Everest in a future update.