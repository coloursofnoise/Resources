## Table Of Contents

<div class="table-of-contents">

*   [Map Name](#map-name)
*   [Map Icon](#map-icon)
*   [Map Icon background ("scarf")](#map-icon-background-scarf)
*   [Chapter Card](#chapter-card)
*   [Map Position On The Mountain](#map-position-on-the-mountain)
*   [Customizing the overworld](#customizing-the-overworld)
     * [Custom mountain/moon models](#custom-mountainmoon-models)
     * [Custom textures](#custom-textures)
     * [Custom colors](#custom-colors)
     * [Custom Background Music and Ambience](#custom-background-music-and-ambience)
     * [Disabling the snow](#disabling-the-snow)
*   [Chapter Complete Screen](#chapter-complete-screen)
     * [Graphics](#graphics)
     * [Music](#music)
*   [Loading Vignette](#loading-vignette)
*   [Checkpoint Images](#checkpoint-images)

</div>

## Map Name

First, you have to ensure your map follows the [mod structure](Mod-Structure).
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

You can see them in the graphics dump (check the [Useful Links](Useful-links) page).

If you want to use a custom icon, place it in `Mods/yourmodname/Graphics/Atlases/Gui/areas/yournickname/campaignname/mymapicon.png` (and `mymapicon_back.png` for the icon's back), then use `areas/yournickname/campaignname/mymapicon` as the map's icon.

## Map Icon background ("scarf")

You can change the scarf that appears behind your map's icon by placing the texture for it in a folder that matches your campaign/map's path.

If your map is in `Mods/yourmod/Maps/foldername/mapname.bin`:
- if you want a scarf specific to your campaign, drop it in `Mods/yourmod/Graphics/Atlases/Gui/areas/foldername/hover.png` 
- if you want a scarf specific to one of your maps, drop it in `Mods/yourmod/Graphics/Atlases/Gui/areas/foldername/mapname_hover.png`

You will find the vanilla scarf in the graphics dump (check the [Useful Links](Useful-links) page), in `Graphics/Atlases/Gui/areas/hover.png`.

## Chapter Card

You can change the chapter card (the card that shows up when your chapter is selected, showing collected berries, deaths, etc):

![image](https://cdn.discordapp.com/attachments/445236692136230943/749300899813261392/unknown.png)

If your map is in `Mods/yourmod/Maps/foldername/mapname.bin`:
- if you want a chapter card specific to your campaign, drop the textures in `Mods/yourmod/Graphics/Atlases/Gui/areaselect/foldername/card.png`, `cardtop.png`, `card_golden.png` and `cardtop_golden.png`.
- if you want a chapter card specific to one of your maps, drop the textures in `Mods/yourmod/Graphics/Atlases/Gui/areaselect/foldername/mapname_card.png`, `mapname_cardtop.png`, `mapname_card_golden.png` and `mapname_cardtop_golden.png`.

Here is an example setup for a map in `Mods/CardTestMod/Maps/SSM24/cardtest/test2.bin`, for both the campaign and the map itself:

![image](https://cdn.discordapp.com/attachments/429775439423209472/748488914138038282/unknown.png)

You will find the vanilla chapter card in the graphics dump (check the [Useful Links](Useful-links) page), in `Graphics/Atlases/Gui/areaselect`.

## Map Position On The Mountain

To define that, you need to create a meta.yaml next to your map: for example, create `testmap.meta.yaml` next to `testmap.bin`.

To define your map's position, add this to the meta.yaml file:
```yaml
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
```
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

You can find the vanilla mountain models in the Content/Overworld folder. If you need to add more models than there are in vanilla in the overworld, you can add them in the same folder, naming them `extra0.obj`, `extra1.obj`, etc.

ℹ️ Be sure to use models using triangles for their faces; some display issues might occur otherwise.

### Custom textures

To change the mountain textures when your map is selected, you can define a custom model directory in your map meta.yaml:
```yaml
Mountain:
  MountainTextureDirectory: yourname/campaignname
```
After defining that, you can drop your custom textures in `Mods/yourmod/Graphics/Atlases/Mountain/yourname/campaignname`.

You can find the vanilla mountain textures in the graphics dump, in `Graphics/Atlases/Mountain`. `buildings`, `mountain` and `skybox` have 3 textures, depending on the mountain `State` (0 is night, 1 is Dawn, 2 is day; see the [Map Position On The Mountain](#map-position-on-the-mountain) section).

If you added extra models, you should add their textures in this directory: for example, `extra1_2.png` will be the texture applied to `extra1.obj` when the mountain is in state 2 (day).

### Custom colors

Some textures and objects used in the overworld are tinted with colors you can customize. Here is what you can put in your meta.yaml (here with values used in vanilla):

```yaml
Mountain:
  FogColors:
    - 010817
    - 13203E
    - 281A35
    - 010817
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

- `FogColors` are the colors of the fog on the mountain, for each `State` (see [Map Position On The Mountain](#map-position-on-the-mountain)). 2 colors will be used by the game: the one for the state your custom mountain uses, and the first one (state 0) on the main menu. **Defining all the values isn't mandatory**: if you define less than 4 values, the others will be at their default. _This means if you're using state 0, you only need 1 value._
- `StarFogColor` is the color of the fog in space.
- `StarStreamColors` is the color of the "streams" visible behind the moon. [Check this image](https://cdn.discordapp.com/attachments/445236692136230943/734524129511866378/unknown.png) to visualize what they are when set to red, green and blue. **You have to specify exactly 3 values** if you use this.
- `StarBeltColors1` and `StarBeltColors2` are the colors of the small stars rotating around the moon. They are dispatched in 2 "belts" that are slightly misaligned between each other. **You can specify any number of colors for each one**, star colors will be picked randomly among the colors you give. If you give an empty array (`StarBeltColors1: []`), the star belt will be removed.

### Custom Background Music and Ambience

For a different background music and ambience to play when the player selects your map, use this in your map meta.yaml:
```yaml
Mountain:
  BackgroundMusic: event:/max480/test_music
  BackgroundAmbience: event:/env/amb/06_lake
```
Note that both are optional: if you want custom music but the default ambience, you can omit `BackgroundAmbience`.

Check the [custom audio tutorial](Audio:-How-Tos) to make the game load your custom music.

You can also set _music params_ through metadata, following the following format:
```yaml
Mountain:
  BackgroundMusicParams:
    param1: value1
    param2: value2
```

For example, **this is what you want to use if you want to have the Farewell background music on your map**:
```yaml
Mountain:
  BackgroundMusicParams:
    moon: 1
```

### Disabling the snow

```yaml
Mountain:
  ShowSnow: false
```

This will turn off the snow that is falling on the mountain, or floating in space.

## Chapter Complete Screen

### Graphics

The image displayed on the chapter complete screen is also defined in the meta.yaml file (see previous section to set it up).
To set up a static image as an endscreen, add something like this:

```yaml
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
          - Type: "ui" # delete this line if you don't want the "Chapter Complete" text to appear
```

Here, the endscreen will be loaded from `Mods/yourmodname/Graphics/Atlases/Endscreens/yournickname/campaignname/mapname.png`.
If your chapter complete screen is an image taking up the whole screen, its size should be 1920x1080px.

Putting multiple images in `Images` will create an animation:
```yaml
        Layers:
          - Type: "layer"
            Images: [ "mapname1", "mapname2", "mapname3" ]
            Position: [ 0.0, 0.0 ]
            Scroll: [ 0.0 ]
            FrameRate: 6 # FPS
```

To create an parallax animation like vanilla endscreens, you can specify multiple layers and give them different `Position` and `Scroll` values:
```yaml
    Layers:
      - Type: "layer"
        Images: [ "00" ]
        Position: [ -75.0, -60.0 ]
        Scroll: [ 0.0 ]
      - Type: "layer"
        Images: [ "01" ]
        Position: [ -75.0, -60.0 ]
        Scroll: [ 0.1 ]
      - Type: "layer"
        Images: [ "02" ]
        Position: [ -75.0, -60.0 ]
        Scroll: [ 0.2 ]
      - Type: "layer"
        Images: [ "03" ]
        Position: [ -75.0, -60.0 ]
        Scroll: [ 0.3 ]
        Alpha: 0.5 # make this layer 50% transparent
```

`Position` controls the position of the layer, and `Scroll` how much it scrolls when the chapter complete screen appears.

### Music

You can make custom music play on the Chapter Complete screen, with this configuration in your meta.yaml (here with default values):

```yaml
CompleteScreen:
  MusicBySide:
    - event:/music/menu/complete_area # A-side
    - event:/music/menu/complete_bside # B-side
    - event:/music/menu/complete_bside # C-side
```

The 3 items in the list correspond to the 3 sides. You don't need to specify 3 elements if you have 1 or 2 sides.

If you want your endscreen to use the same music as the chapter 7 endscreen, use `event:/music/menu/complete_summit`.

To make your own, [import your music in FMOD](Audio:-How-Tos). The music will start playing as soon as the "snow falling" animation will start. When the chapter complete screen appears, the `end` audio param will be set to 1. You can use this to make your music synchronize with the endscreen.

### Title

You can make custom title text shown on the Chapter Complete screen without editing image anymore, with this configuration in your meta.yaml (here with default values):

```yaml
CompleteScreen:
  Title:
    ASide: 'AREACOMPLETE_NORMAL' # A-side complete ("Chapter Complete")
    BSide: 'AREACOMPLETE_BSIDE' # B-side complete ("B-Side Complete")
    CSide: 'AREACOMPLETE_CSIDE' # C-side complete ("C-Side Complete")
    FullClear: 'AREACOMPLETE_NORMAL_FULLCLEAR' # A-side full clear ("Chapter Clear")
  Layers:
  - Type: 'ui' # don't forget to add this line for your text to appear
```

You can replace the Dialogue IDs to your custom ones. If an item is omitted, it will automatically fallback to default value.

Here is an example usage and preview to display "D-Side Complete" on vanilla Chapter 2 endscreen after completing A-side:

![image](https://user-images.githubusercontent.com/7558201/102515332-96a58980-40c8-11eb-86a0-6fa696d846c0.png)

In meta.yaml file:

```yaml
CompleteScreen:
  Atlas: 'OldSite'
  Start: [0.0, 1050.0]
  Center: [0.0, 250.0]
  Offset: [-108.0, 0.0]
  Title:
    ASide: 'WEGFan_CompleteScreenTest_Endscreen_A_Side'
  Layers:
  - Type: 'layer'
    Images: ['00']
    Position: [0.0, 0.0]
    Scroll: [0]
  - Type: 'layer'
    Images: ['01']
    Position: [0.0, 0.0]
    Scroll: [0.02]
  - Type: 'layer'
    Images: ['02']
    Position: [0.0, 0.0]
    Scroll: [0.04]
  - Type: 'layer'
    Images: ['03']
    Position: [0.0, 0.0]
    Scroll: [0.06]
  - Type: 'layer'
    Images: ['04']
    Position: [0.0, 0.0]
    Scroll: [0.10]
  - Type: 'layer'
    Images: ['05']
    Position: [0.0, 0.0]
    Scroll: [0.10]
  - Type: 'layer'
    Images: ['06']
    Position: [0.0, -20.0]
    Scroll: [0.11]
  - Type: 'layer'
    Images: ['07']
    Position: [0.0, 0.0]
    Scroll: [0.12]
  - Type: 'ui'
  - Type: 'layer'
    Images: ['08']
    Position: [0.0, -680.0]
    Scroll: [0.13]
  - Type: 'layer'
    Images: ['09']
    Position: [0.0, 0.0]
    Scroll: [0.13]
  - Type: 'layer'
    Images: ['10']
    Position: [0.0, -680.0]
    Scroll: [0.15]
```

In your dialog file:

```text
WEGFan_CompleteScreenTest_Endscreen_A_Side= D-Side Complete
```

## Loading Vignette

A loading vignette is displayed when a level is selected, similarly to the Intro, Summit, and Core chapters.

To display an image, use the same structure as a [Chapter Complete Screen](#chapter-complete-screen), but replace `CompleteScreen` with `LoadingVignetteScreen`.

To display text, add the following:
```yaml
LoadingVignetteText:
    Dialog: "YourDialogHere"
```
Note that only one of these can be used for each level.

## Checkpoint Images

First of all, checkpoint images need to be masked to look like vanilla ones: [follow the instructions to do that here](Mapping-on-PC#how-do-i-add-a-checkpoint-mask-onto-my-custom-checkpoints).

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