This is a tutorial for adding static or dynamic sprites to the game that can then be accessed from your code mod.  
For questions and feedback, please contact @coloursofnoise on the Celeste [Discord](https://discord.gg/6qjaePQ).

# Table of Contents:
## Understanding the Atlas system
- [Atlases](https://github.com/EverestAPI/Resources/wiki/Adding-Sprites#atlases)
- [SpriteBanks](https://github.com/EverestAPI/Resources/wiki/Adding-Sprites#spritebanks)
## Adding custom sprites to your code mod:
- [Using MTextures in code](https://github.com/EverestAPI/Resources/wiki/Adding-Sprites/#using-a-spritebank-file)
- [Using a SpriteBank file](https://github.com/EverestAPI/Resources/wiki/Adding-Sprites/#using-a-spritebank-file)
- [Using Sprites in code](https://github.com/EverestAPI/Resources/wiki/Adding-Sprites/#using-sprites-in-code)


# The Atlas System
## Atlases
Celeste stores it’s textures in Atlases, with each atlas being used for different aspects of the game.

To load a texture into a preexisting atlas, follow the directions [here](https://github.com/EverestAPI/Resources/wiki/Mod-Structure#file-layout) relating to pre-supported content mappings.

The atlases present in the game already include:
- Gameplay - for ingame textures
- Gui - for menus and title screens
- Portraits - for character dialogue

When the game is loaded, it takes every file present in each atlas’ [folder](https://github.com/EverestAPI/Resources/wiki/Mod-Structure#file-layout), and adds them to an Atlas object. They can then be referenced later by querying the atlas using the relative path of the file within the file structure.
## SpriteBanks
SpriteBanks are an extension of the Atlas system that incorporates an xml structure to compile multiple sprites into animations.

# Custom Sprites for Code Mods
## Using MTextures in Code
This is the simplest way to load a new texture into the game, however it is only really useful for static images. 

To retrieve a texture and assign it to a variable, simply access the Atlas as you would an array, using a string containing the relative path **excluding file extensions** of your image as the index.   
Ex: <code>MTexture myTexture = GFX.Game["pathname"];</code> for a texture in the Gameplay atlas.

To display your texture in game, hook the relevant Render method and call the Draw() or DrawCentered() method of your texture.  
Ex: <code>myTexture.Draw(position);</code>


## Using a SpriteBank File
Spritebank files are xml files that group textures into sprites with animations and states. They cannot be modified dynamically.

Most of the SpriteBanks are stored in the <code>Sprites.xml</code> file in the Graphics folder for celeste. To add your own spritebanks, you will need to copy this file into your own mod folder, in the <code>Graphics</code> subfolder.

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
Graphics  
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

To retrieve your sprite for use with an Entity, call <code>Sprite mySprite = GFX.SpriteBank.Create("spriteName");</code>. Then call <code>mySprite.Play("animID");</code> to play your loop or animation when needed.

## Using Sprites in Code
It is also possible to add and play custom animations without adding them to the Sprites.xml file. This allows for animations to be created dynamically as the program runs.

This method uses the Atlas to retrieve the sprite, then allows for the addition of loops and animations within the code:  
Ex: <code>Sprite mySprite = new Sprite(GFX.Game, "sprite/folder");</code>  
Calling <code>mySprite.AddLoop("loopID", "", delayFloat);</code> will add an animation that can later be called using <code>mySprite.Play("loopID");</code>

