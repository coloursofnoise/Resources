Some decals in the game have hardcoded properties which cannot be replicated normally with custom decals. This is where the **Decal Registry** is useful.

To start using it, first create a `DecalRegistry.xml` file in your Mod's root (next to the everest.yaml). An example file:
```xml
<decals>
	<decal path="frosttemple/icegrass/grass_a">
		<banner amplitude="2" sliceSize="1" speed="2" sliceSinIncrement="0.05" easeDown="false" offset="-2" />
	</decal>
</decals>
```
You can add as many `<decal>`s as you want. The `path` attribute of `<decal>`s is the path to your decal sprite relative to `Graphics/Atlases/Gameplay/decals/`

Inside of a `<decal>`, you can specify as many properties as you want. While other mods can extend this, Everest currently supports these properties:
* `<banner>`: Attributes: `amplitude(float), sliceSize(int), speed(float), sliceSinIncrement(float), easeDown(bool), offset(float)` - Used for grass for example, makes the decal wobble left/right.
* `<floaty>`: No Attributes - Makes the decal floaty.
* `<smoke>`: Attributes: `inbg(bool), offsetX(float), offsetY(float)` - Makes the decal create smoke
* `<parallax>`: Attributes: `amount(float)` - Adds parallax to the decal
* `<depth>`: Attributes: `value(int)` - Sets the Depth of the decal, useful for making decals show up in front/behind specific objects
* `<animationSpeed>`: Attributes: `value(int)` - Sets the animation speed of the decal
* `<sound>`: Attributes: `event(string)` - Makes the decal play the sound specified in the `event` attribute
* `<bloom>`: Attributes: `offsetX(float), offsetY(float), alpha(float), radius(float)` - Adds bloom to the decal
* `<coreSwap>`: Attributes:
  * `coldPath`: The path to the sprite to use when the room is in cold core mode
  * `hotPath`: The path to the sprite to use when the room is in hot core mode
* `<mirror>`: Attributes: `keepOffsetsClose(bool)` - Makes the reflection offset look slightly closer to the player.
  * To make the decal reflective, create a folder named `mirrormasks` on the same level as your `decals` folder, and create all the subfolders corresponding to the decal's original file path. Create a texture file with the same name as the original decal in this path (for example, `decals/modname/mytexture.png` will have a corresponding `mirrormasks/modname/mytexture.png` texture file).  
The red channel controls the horizontal offset of the reflection, and the green channel controls the vertical offset (the blue channel is unused). So 255 red and 255 green makes it the closest to the player, 0 red and 255 green makes it furthest horizontally, 255 red and 0 green makes it furthest vertically, and 0 red and 0 green makes it the furthest in both axis. Transparent pixels do not cast reflections.
* `<solid>`: Attributes: `x(float)`, `y(float)`, `width(float)`, `height(float)`, `index(int)`, `blockWaterfalls(bool)` - Adds a solid block relative to this decal
  * `x` and `y` are offsets relative to the decal position.
  * `index`: the SoundSurfaceIndex to use for the solid.
* `<staticMover>`: Attributes: `x(int)`, `y(int)`, `width(int)`, `height(int)` - Attaches this decal to solid entities within the relative collision box described by the attributes (see `solid` for details) (not guaranteed to work with other properties)
* `<scared>`: Attributes:
  * `range(int)`, `hideRange(int)`, `showRange(int)`: The distance from the player (in pixels) at which each animation will play. `range` sets the values of both `hideRange` and `showRange`
  * `idleFrames`: Plays by default and after `showFrames` (Loops)
  * `hideFrames`: Plays when the player comes closer than `hideRange`
  * `hiddenFrames`: Plays after `hideFrames` (Loops)
  * `showFrames`: Plays when the player moves farther than `showRange`

  `Frames` attributes use the same formatting as the animations in the Sprites.xml (`0,1,2-5,6*3`)
