Create a file named Portraits.xml in your Graphics folder (see [here](Mod-Structure) for how to set that up).

Follow this example, replacing {yourportrait} with the name of your portrait:
```xml
<?xml version="1.0" encoding="utf-8" ?>
<Sprites>
  <portrait_{yourportrait} path="{yourportrait}/" sfx="{yourportrait}" textbox="{yourportrait}">
    <Center />
	 
    <sfxs>
      <normal index="1"/>
    </sfxs>
	 
    <Loop id="idle_normal" path="normal" delay="0.1" frames="0"/>
  </portrait_{yourportrait}>
</Sprites>
```

`portrait_{yourportrait}` corresponds to `YOURPORTRAIT` in `[YOURPORTRAIT right normal]`
- `path` indicates the folder within the Portraits atlas (`Graphics/Atlases/Portraits/`) :warning: Make sure to include the `/` at the end
- `sfx` refers to the audio event used, and is appended to `event:/char/dialogue/`
- `textbox` is the path to the textbox texture relative to `Graphics/Atlases/Portraits/textbox` 
- `phonestatic` can be either "mom" or "ex" (Optional)
- `glitchy` can be "true" or "false" (Optional)

the `Center` tag is reccomended to center the portrait in the textbox

There are three different prefixes that can be used for animation `id`s:
- `begin`: played before the idle or talk animation
- `idle`: played when not talking
- `talk`: played when talking

Each group of animations (or __expression__) also needs an assigned `index` in the `sfxs` element, which is used as the `dialogue_portrait` audio parameter
The `dialogue_end` audio param will be set to 1 if the audio is ending.

TextBoxes will also use an additional `_overlay` sprite if present.  
MiniTextboxes will use the associated `_mini` sprite if present.