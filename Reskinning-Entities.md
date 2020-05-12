This page will explain you how to change the appearance of entities **for your map only**. If you are working on a texture pack that should apply to the whole game, including vanilla maps, head to [How do I make a texture pack?](https://github.com/EverestAPI/Resources/wiki/How-do-I-make-a-texture-pack%3F)

You should grab [the graphics dump](https://drive.google.com/open?id=1ITwCI2uJ7YflAG0OwBR4uOUEJBjwTCet) to be able to use the vanilla sprites as a reference.

The steps to follow depend on which entity you are trying to reskin.

## Table of Contents

* [Entities that are reskinnable out of the box](#entities-that-are-reskinnable-out-of-the-box)
  * [Spikes](#spikes)
  * [Switch Gates](#switch-gates)
  * [Jump Throughs](#jump-throughs)
* [Reskinning entities through Sprites.xml](#reskinning-entities-through-spritesxml)
* [Other entities](#other-entities)

## Entities that are reskinnable out of the box

### Spikes

In order to make custom spikes textures:
- head to `Graphics/Atlases/Gameplay/danger/spikes` in the graphics dump and copy the spike textures you want to base yourself on.
- paste those in `Mods/yourmod/Graphics/Atlases/Gameplay/danger/spikes/yourmod/campaignname` and rename them. For example, `custom_down00.png`, `custom_down01.png`, etc. **Don't touch anything after the _**
- in Ahorn, in the "Type" field, use `yourmod/campaignname/custom`

### Switch Gates

In order to customize the switch gate block:
- head to `Graphics/Atlases/Gameplay/objects/switchgate` in the graphics dump and copy one of block.png, mirror.png, stars.png or temple.png.
- paste it in `Mods/yourmod/Graphics/Atlases/Gameplay/objects/switchgate/yourmod/campaignname/myblock.png`.
- in Ahorn, in the "Sprite" field, use `yourmod/campaignname/myblock`

### Jump Throughs

In order to customize jumpthru textures:
- head to `Graphics/Atlases/Gameplay/objects/jumpthru` in the graphics dump and copy one of them.
- paste it in `Mods/yourmod/Graphics/Atlases/Gameplay/objects/jumpthru/yourmod/campaignname/myjumpthru.png`.
- in Ahorn, in the "Texture" field, use `yourmod/campaignname/myjumpthru`. Note that you can also change the footstep sounds with the "Surface Index" parameter.

## Reskinning entities through Sprites.xml

In order to check if an entity is reskinnable through Sprites.xml, look for it in `Content/Graphics/Sprites.xml`. If you find it, this means you can change the appearance of this entity throughout your map, without affecting other maps.

In this example, we are reskinning Theo Crystal.

- copy `Content/Graphics/Sprites.xml` into `Mods/yourmod/Graphics/yourname/campaignname/Sprites.xml`
- open your copy, and look for Theo Crystal. You will find this:
```xml
  <theo_crystal path="characters/theoCrystal/" start="idle">
    <Origin x="32" y="42"/>
    <Loop id="idle" path="idle" delay="0.08"/>
    <Anim id="shatter" path="shatter" delay="0.08" goto="shattered"/>
    <Loop id="shattered" path="shatter" frames="16" delay="0.08"/>
  </theo_crystal>
```
`path="characters/theoCrystal/"` means you will find the textures for it in the graphics dump, at Graphics/Atlases/Gameplay/**characters/theoCrystal**.
- copy this folder into `Mods/yourmod/Graphics/Atlases/Gameplay/yourname/campaignname/theoCrystalReskin`, then modify them as you want.
- in your Sprites.xml copy, edit the path to match the folder you created at the previous step:
```xml
  <theo_crystal path="yourname/campaignname/theoCrystalReskin/" start="idle">
```
:warning: If there is a slash at the end of the path, don't remove it.
- in your map metadata in Ahorn, change Sprites to `Mods/yourmod/Graphics/yourname/campaignname/Sprites.xml`.

You're all set! Now, if you place a Theo crystal, it should use your custom texture in-game.

## Other entities

If an entity is not reskinnable out of the box and not in Sprites.xml, you might need to make a code mod to reskin it. Ask around on Discord if you are unsure if a code mod is necessary to reskin your entity.

Existing helpers provide more reskinnable entities:
- [Frost Helper](https://gamebanana.com/gamefiles/9201):
  - Spinners
  - Springs
  - Zip Movers
  - Custom colors for Fire Barriers, Rising Lava and Dream Blocks
- [max480's Helping Hand](https://gamebanana.com/gamefiles/11423):
  - Touch Switch and Switch Gate _icons_. Switch gate _blocks_ are reskinnable out of the box (see first part)
