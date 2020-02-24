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