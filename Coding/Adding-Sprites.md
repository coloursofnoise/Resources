This is a tutorial for adding static or dynamic sprites to the game that can then be accessed from your code mod.  
For questions and feedback, please contact @coloursofnoise on the [Celeste Discord](https://discord.gg/6qjaePQ).

# Table of Contents:
## Understanding the Atlas system
- [Atlases](#atlases)
- [SpriteBanks](#spritebanks)
## Adding custom sprites to your code mod:
- [Using MTextures in code](#using-a-spritebank-file)
- [Using a SpriteBank file](#using-a-spritebank-file)
- [Creating Sprites in code](#creating-sprites-in-code)


# The Atlas System
## Atlases
Celeste stores its textures in Atlases, with each atlas being used for different aspects of the game.

Celeste's textures were packed using [Crunch](https://github.com/ChevyRay/crunch) using the binary format, resulting in the `.meta` and `.data` files in the `Contents` folder. These graphics have been extracted [here](https://drive.google.com/open?id=1ITwCI2uJ7YflAG0OwBR4uOUEJBjwTCet) in a process that preserved the original folder structure and may be freely used for Celeste modding.

To load a texture into a preexisting atlas, follow the directions [here](Mod-Structure#file-layout) relating to pre-supported content mappings.

Atlases that are shipped and loaded by the vanilla game include:
- `Gameplay` - for ingame textures
- `Gui` - for menus and title screens
- `Portraits` - for character dialogue

When the game is loaded, it takes every file present in each atlas’ [folder](Mod-Structure#file-layout), and adds them to an Atlas object. They can then be referenced later by querying the atlas using the relative path of the file within the file structure.

## SpriteBanks
SpriteBanks are an extension of the Atlas system that incorporates an xml structure to compile multiple textures into animations, or `Sprites`.

Vanilla SpriteBanks include:
- `Sprites.xml` - for gameplay sprites
- `SpritesGui.xml` - for hires menu and title screens
- `Portraits.xml` - for character dialogue

# Custom Sprites for Code Mods

## Using MTextures in Code
This is the simplest way to load a new texture into the game, however it is only really useful for static images. 

To retrieve a texture and assign it to a variable, simply access the Atlas as you would an dictionary, using a string containing the relative path **excluding file extensions** of your image as the index.  
Ex: `MTexture myTexture = GFX.Game["pathname"];` for a texture in the Gameplay atlas.

To display your texture in game, call the `Draw` or `DrawCentered` method of your texture in the appropriate `Render` method.  
Ex: `myTexture.Draw(position);`

An `Image` component can also be added to an entity to render an MTexture relative to the entity during the `base.Render()` call.  
Ex: `Add(new Image(myTexture));`


## Using a SpriteBank File
Spritebank files are xml files that group textures into sprites with animations and states. They cannot be modified dynamically.

Most of the vanilla Gameplay sprites are stored in the `Sprites.xml` file in the `Graphics` folder for celeste. To add your own sprites, you will need to make a similar file in your own mod folder, also in a `Graphics` subfolder.

A Spritebank file can also be created elsewhere within your mod, but it must be loaded separately by creating a new `SpriteBank` targeting the appropriate [Atlas](#atlases).

Adding your own sprite to this file will loosely emulate the following example:
```xml
<spriteName path="sprite/folder" start="initialanimation">
  <!-- If you want it centered: -->
  <Center/>

  <!-- This animation will loop until changed: -->
  <Loop id="loopID" path="texturename" delay="0.15"/>

  <!-- This animation will play once: -->
  <Anim id="animID" path="othertexturename" delay="0.08" frames="3,7-9"/>
</spriteName>
```

In the above example, your file structure would look something like this:
<pre>
Graphics/Atlases/Gameplay
  ↳ sprite
    ↳ folder
      ↳ texturename0
      ↳ texturename1
      ↳ texturename2
      ↳ othertexturename3
      ↳ othertexturename7
      ↳ othertexturename8
      ↳ othertexturename9
</pre>

Your sprite can then be retrieved from the SpriteBank with code similar to the following:
```cs
Sprite mySprite = GFX.SpriteBank.Create("spriteName");
Add(mySprite); // Add the sprite Component to your entity
mySprite.Play("animID") // Play an animation
```

:information_source: If you have created your own SpriteBank separate from the main Gameplay sprites, replace `GFX.SpriteBank` with a reference to your SpriteBank.


## Creating Sprites in Code
It is also possible to add and play custom animations without adding them to a SpriteBank file. This allows for animations to be created dynamically as the program runs.

This method uses the Atlas to retrieve the sprite, then allows for the addition of loops and animations within the code:  
```cs
Sprite mySprite = new Sprite(GFX.Game, "sprite/folder");
mySprite.AddLoop("loopID", "path", delayFloat); // Add an animation
mySprite.Play("loopID"); // Play that animation
```

