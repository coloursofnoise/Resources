## Map name

First, you have to ensure your map follows the [mod structure](https://github.com/EverestAPI/Resources/wiki/Mod-Structure). In particular, your map bin should be in `Mods/yourmodname/Maps/yournickname/campaignname/mapname.bin`.

You should now create the file `Mods/yourmodname/Dialog/English.txt`. It should contain the following:
```
yournickname_campaignname= Campaign Name
yournickname_campaignname_mapname= Map Name
```

It also works to define checkpoint names:
```
yournickname_campaignname_mapname_roomname= Checkpoint Name
```

As a general rule, if you see `{somestring}` in the game, you need to define `somestring` in your English.txt.

You must restart Celeste or use Ctrl+F5 (in debug mode) for the changes in English.txt to take effect.

## Map Icon

You can define the map icon in Ahorn, in the "Title Banner Icon" field of the Map > Metadata menu.

The banners for the base levels are:
* areas/intro
* areas/city
* areas/oldsite
* areas/resort
* areas/cliffside
* areas/temple
* areas/reflection
* areas/Summit
* areas/core

You can see them in the graphics dump (check the [Useful Links](https://github.com/EverestAPI/Resources/wiki/Useful-links) page).

areas/farewell exists too, but please avoid using it, as it will change when the DLC comes out.

If you want to use a custom icon, place it in `Mods/yourmodname/Graphics/Atlases/Gui/areas/auniquename.png` (and `auniquename_back.png` for the icon's back). Then use `areas/auniquename` as the map's icon. To ensure the name is unique, include your nickname in the filename for example (`max480_testmap.png`).

## Map position on the mountain

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
```

You can get the coordinates by enabling debug mode (in Mod Options), restarting the game, and pressing Space on the mountain screen. Look around with the mouse and move around with WASD. The coordinates will be displayed on the top left.

* `Idle` defines the camera position during level selection.
* `Select` defines the camera position when you selected the level and looking at checkpoint selection or side selection.
* `Zoom` is the camera position when you zoom into the level after you start.
* `Cursor` is the location of the Madeline cursor on the mountain.
* `State` defines the lighting of the mountain: 0 is night, 1 is Dawn, 2 is day.

## Chapter Complete screen

This is also defined in the meta.yaml file (see previous section to set it up). To set up a static image as an endscreen, add something like this:

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
```

Here, the endscreen will be loaded from `Mods/yourmodname/Graphics/Atlases/Endscreens/yournickname/campaignname/mapname.png`. It's size should be 1920x1080px.

Putting multiple images will create an animation.


_If any of this information is incorrect, feel free to correct it and to shout at max480 on Discord._