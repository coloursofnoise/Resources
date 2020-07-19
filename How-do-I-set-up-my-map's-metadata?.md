## Table Of Contents

<div class="table-of-contents">

*   [Map Name](#map-name)
*   [Map Icon](#map-icon)
*   [Map Position On The Mountain](#map-position-on-the-mountain)
*   [Customizing the overworld](#customizing-the-overworld)
     * [Custom mountain/moon models](#custom-mountainmoon-models)
     * [Custom textures](#custom-textures)
     * [Custom colors](#custom-colors)
     * [Custom Background Music](#custom-background-music)
*   [Chapter Complete Screen](#chapter-complete-screen)
*   [Loading Vignette](#loading-vignette)
*   [Checkpoint Images](#checkpoint-images)

</div>

## Map Name

First, you have to ensure your map follows the [mod structure](https://github.com/EverestAPI/Resources/wiki/Mod-Structure).
In particular, your map bin should be in `Mods/yourmodname/Maps/yournickname/campaignname/mapname.bin`.

You should now create the file `Mods/yourmodname/Dialog/English.txt`.
It should contain the following:

    yournickname_campaignname= Campaign Name
    yournickname_campaignname_mapname= Map Name

It also works to define checkpoint names:

    yournickname_campaignname_mapname_roomname= Checkpoint Name

As a general rule, if you see `{blah_blah}` in the game, and you want it to display `some text` instead,
you need to add this in your English.txt:

    blah_blah= some text

(If you feel like translating your map name in other languages, you can create other files in the Dialog directory, for example `French.txt`.
All non-existing languages will fall back to English.)

## Map Icon

You can define the map icon in Ahorn, in the "Title Banner Icon" field of the Map > Metadata menu.
The banners for the base levels are:

*   areas/intro
*   areas/city
*   areas/oldsite
*   areas/resort
*   areas/cliffside
*   areas/temple
*   areas/reflection
*   areas/summit
*   areas/core
*   areas/farewell

You can see them in the graphics dump (check the [Useful Links](https://github.com/EverestAPI/Resources/wiki/Useful-links) page).

If you want to use a custom icon, place it in `Mods/yourmodname/Graphics/Atlases/Gui/areas/yournickname/campaignname/mymapicon.png` (and `mymapicon_back.png` for the icon's back), then use `areas/yournickname/campaignname/mymapicon` as the map's icon.

## Map Position On The Mountain

To define that, you need to create a meta.yaml next to your map: for example, create `testmap.meta.yaml` next to `testmap.bin`.

To define your map's position, add this to the meta.yaml file:

    Mountain:
        Idle:
            Position: [ 7.565, 8.614, -5.318 ]
            Target: [ 6.210, 7.754, -4.125 ]
        Select:
            Position: [ 8.782, 6.271, -1.953 ]
            Target: [ 6.799, 6.172, -2.194 ]
        Zoom:
            Position: [ 6.462, 5.235, -1.605 ]
            Target: [ 4.542, 5.754, -1.819 ]
        Cursor: [ 5.706, 5.492, -1.542 ]
        State: 2
        ShowCore: false
        Rotate: true

You can get the coordinates by enabling debug mode (in Mod Options), restarting the game, and pressing Space on the mountain screen.
Look around with the mouse, move around with WASD and move the camera up/down with Q and Z.
The coordinates will be displayed on the top left.

*   `Idle` defines the camera position during level selection.
*   `Select` defines the camera position when you selected the level and looking at checkpoint selection or side selection.
*   `Zoom` is the camera position when you zoom into the level after you start.
*   `Cursor` is the location of the Madeline cursor on the mountain.
To place this, move the camera to where you want the cursor to be, then copy the `Position` coordinates.
*   `State` defines the lighting of the mountain: 0 is night, 1 is Dawn, 2 is day, 3 is moon.
*   `ShowCore` decides whether the Core Heart should be shown on the Mountain.
*   `Rotate` decides whether the camera should rotate around the Mountain.

**If you just want to copy the coordinates of a vanilla chapter, have a look at the values defined in `Content/Overworld/AreaViews.xml`.**

## Customizing the overworld

### Custom mountain/moon models

You can customize the mountain 3D models that are displayed when your map is selected, by defining a custom model directory in your map meta.yaml:
```yaml
Mountain:
  MountainModelDirectory: Mountain/yourname/campaignname
```
After defining that, you can drop your custom objects in `Mods/yourmod/Mountain/yourname/campaignname`.

You can find the vanilla mountain models in the Content/Overworld folder.

### Custom textures

To change the mountain textures when your map is selected, you can define a custom model directory in your map meta.yaml:
```yaml
Mountain:
  MountainTextureDirectory: yourname/campaignname
```
After defining that, you can drop your custom textures in `Mods/yourmod/Graphics/Atlases/Mountain/yourname/campaignname`.

You can find the vanilla mountain textures in the graphics dump, in `Graphics/Atlases/Mountain`. `buildings`, `mountain` and `skybox` have 3 textures, depending on the mountain `State` (0 is night, 1 is Dawn, 2 is day; see the [Map Position On The Mountain](#map-position-on-the-mountain) section).

### Custom colors

Some textures and objects used in the overworld are tinted with colors you can customize. Here is what you can put in your meta.yaml (here with values used in vanilla):

```yaml
Mountain:
  StarFogColor: 020915
  StarStreamColors:
    - 000000
    - 9228e2
    - 30ffff
  StarBeltColors1:
    - 53f3dd
    - 53c9f3
  StarBeltColors2:
    - ab6ffa
    - fa70ea
```

- `StarFogColor` is the color of the fog in space.
- `StarStreamColors` is the color of the "streams" visible behind the moon. [Check this image](https://cdn.discordapp.com/attachments/445236692136230943/734524129511866378/unknown.png) to visualize what they are when set to red, green and blue. **You have to specify exactly 3 values** if you use this.
- `StarBeltColors1` and `StarBeltColors2` are the colors of the small stars rotating around the moon. They are dispatched in 2 "belts" that are slightly misaligned between each other. **You can specify any number of colors for each one**, star colors will be picked randomly among the colors you give. If you give an empty array (`StarBeltColors1: []`), the star belt will be removed.

### Custom Background Music

For a different background music to play when the player selects your map, use this in your map meta.yaml:
```yaml
Mountain:
  BackgroundMusic: event:/max480/test_music
```
Check the [custom audio tutorial](https://github.com/EverestAPI/Resources/wiki/Audio:-How-Tos) to make the game load your custom music.

## Chapter Complete Screen

This is also defined in the meta.yaml file (see previous section to set it up).
To set up a static image as an endscreen, add something like this:

    CompleteScreen:
        Atlas: "Endscreens/yournickname/campaignname"
        Start: [ 0.0, 0.0 ]
        Center: [ 0.0, 0.0 ]
        Offset: [ 0.0, 0.0 ]
        Layers:
          - Type: "layer"
            Images: [ "mapname" ]
            Position: [ 0.0, 0.0 ]
            Scroll: [ 0.0 ]

Here, the endscreen will be loaded from `Mods/yourmodname/Graphics/Atlases/Endscreens/yournickname/campaignname/mapname.png`.
Its size should be 1920x1080px.

Putting multiple images will create an animation.

## Loading Vignette

A loading vignette is displayed when a level is selected, similarly to the Intro, Summit, and Core chapters.

To display an image, use the same structure as a [Chapter Complete Screen](#chapter-complete-screen), but replace `CompleteScreen` with `LoadingVignetteScreen`.

To display text, add the following:
```
LoadingVignetteText:
    Dialog: "YourDialogHere"
```
Note that only one of these can be used for each level.

## Checkpoint Images

First of all, checkpoint images need to be masked to look like vanilla ones: [follow the instructions to do that here](https://github.com/EverestAPI/Resources/wiki/How-do-I-make-maps-on-PC%3F#how-do-i-add-a-checkpoint-mask-onto-my-custom-checkpoints).

Then, if your map is in Mods/yourmodname/Maps/**mapfolder/mapname**.bin, you should drop your checkpoint images to this location for them to work:

Mods/yourmodname/Graphics/Atlases/Checkpoints/**mapfolder/mapname**/side/roomname.png

Replace `side` with A, B or C, and `roomname` with the name of the room the checkpoint is in, or `start` for the starting checkpoint.

For example, if your map is in:
```
Maps/
  orbittwz/
    polygondreams/
      1-itooktheelevator.bin
```

and has a checkpoint in room `03a`, your checkpoint images will go here:
```
Graphics/
  Atlases/
    Checkpoints/
      orbittwz/
        polygondreams/
          1-itooktheelevator/
            A/
              03a.png
              start.png
```

_If any of this information is incorrect, feel free to correct it and to shout at max480 on Discord._