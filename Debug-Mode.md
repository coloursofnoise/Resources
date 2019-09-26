Enabling Debug Mode gives you access to some debug functions hidden in the game. You get some hotkeys useful when making mods/maps, a debug save and an in-game level viewer allowing you to teleport around.

## Keys available during gameplay

* F5: Reload active level
* F6: Open debug map ("level editor"), allows you to teleport around
* Ctrl+F5: Reload the entire game. This is the equivalent of hitting Save & Quit, then closing Celeste, opening it again and loading the save file.

## Keys available in the debug map

This debug map is especially useful to teleport around in the game.

* Right click on a room: teleport to it
* Ctrl + Right click on a room: teleport to it **losing your current session** (like collected strawberries)
* Shift + Right click on a room: teleport to a specific point in the room, rather than to the closest spawn point. (Yes, even in walls.)
* Mouse wheel: zoom in and out
* Move around with the keys you use for movement, or by holding the mouse wheel, or by holding Space and using the left mouse button
* Ctrl+Space resets zoom and position to default

You can also "edit" levels, but the save function is gone, so you won't be able to play them afterwards. You can still play around with it though:
* You can drag rooms around
* F+Left mouse button creates a filler room, F+Right mouse button removes one. You can resize them with the mouse
* Ctrl+A selects everything
* Ctrl+Z is Undo, Ctrl+Y is Redo (~~crashes the game though~~)
* Keys 1 to 7 change the rooms' colors
* F1 or Ctrl+S are supposed to save but don't
* Holding Q shows you the strawberry order, in the format `checkpointId:order`

## The Debug Save

Debug mode also gives access to a `~DEBUG~` option in the main menu: this is the debug save. Some specific rules are applied to this save:

* Everything is unlocked by default.
* When you start a level, all your collected strawberries for that level are reset.