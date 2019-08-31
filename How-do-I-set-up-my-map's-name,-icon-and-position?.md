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

You can get the coordinates by enabling debug mode (in Mod Options), and pressing Space. Look around with the mouse and move around with WASD. The coordinates will be displayed on the top left.

* `Idle` defines the camera position during level selection.
* `Select` defines the camera position when you selected the level and looking at checkpoint selection or side selection.
* `Zoom` is the camera position when you zoom into the level after you start.
* `Cursor` is the location of the Madeline cursor on the mountain.
* `State` defines the lighting of the mountain: 0 is night, 1 is Dawn, 2 is day.

