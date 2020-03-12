Everest provides a number of events that can be subscribed to from within your code mod. 
This guide lists each event, the methods within Celeste that raise it, and any additional notes on it.

To subscribe to an event, use the following format:  
```c#
Everest.Events.Level.OnLoadLevel += Your_OnLoadLevel_Method;
```
where `Your_OnLoadLevel_Method` is a method with arguments matching those listed in this guide:  
```c#
private void Your_OnLoadLevel_Method(Level level, Player.IntroTypes playerIntro, bool isFromLoader){

}
```

# Event Types
- [Celeste](#Celeste)
- [Main Menu](#MainMenu)
- [Level](#Level)
- [Player](#Player)
- [Input](#Input)
- [Journal](#Journal)
- [Decal](#Decal)


# Events
## Celeste
Event | Raised By | Notes
--- | --- | ---
`OnExiting`() | Celeste.Celeste.OnExiting | Called after the main gameloop has finished running in Microsoft.Xna.Framework.Game.Run
`OnShutdown`() | Celeste.Celeste.Main | Called just before the Main method exits


## MainMenu
Event | Raised By | Notes
--- | --- | ---
`OnCreateButtons`(OuiMainMenu menu, List<MenuButton> buttons) | Celeste.OuiMainMenu.Added<br>Celeste.OuiMainMenu.RebuildMainAndTitle<br>Celeste.Settings.Reload | Used for adding new MenuButtons to the OuiMainMenu<br>Ex: [Everest.CoreModule](https://github.com/EverestAPI/Everest/blob/be193a4e29a8f9d94971a5997d5caad08c5494bd/Celeste.Mod.mm/Mod/Core/CoreModule.cs#L159)
 

## Level
Event | Raised By | Notes
--- | --- | ---
`OnPause`(Level level, int startIndex, bool minimal, bool quickReset) | Celeste.Level.Pause
`OnCreatePauseMenuButtons`(Level level, TextMenu menu, bool minimal) | Celeste.Level.Pause
`OnTransitionTo`(Level level, LevelData next, Vector2 direction) | Celeste.Level.TransitionTo
`OnLoadEntity`(Level level, LevelData levelData, Vector2 offset, EntityData entityData) | Celeste.Level.LoadCustomEntity
`OnLoadBackdrop`(MapData map, BinaryPacker.Element child, BinaryPacker.Element above) | Celeste.Mapdata.LoadCustomBackdrop
`OnLoadLevel`(Level level, Player.IntroTypes playerIntro, bool isFromLoader) | Celeste.Level.LoadLevel
`OnEnter`(Session session, bool fromSaveData) | Celeste.LevelEnter.Go | As of Everest 1436, is called on ctrl+f5
`OnExit`(Level level, LevelExit exit, LevelExit.Mode mode, Session session, HiresSnow snow) | Celeste.LevelExit.LevelExit
`OnComplete`(Level level) | Celeste.Level.RegisterAreaComplete


## Player
Event | Raised By | Notes
--- | --- | ---
`OnSpawn`(Player player) | Celeste.Player.Added
`OnDie`(Player player) | Celeste.Player.Die


## Input
Event | Raised By | Notes
--- | --- | ---
`OnInitialize` | Celeste.Input.Initialize
`OnDeregister` | Celeste.Input.Deregister


## Journal
Event | Raised By | Notes
--- | --- | ---
`OnEnter`(OuiJournal journal, Oui from) | Celeste.OuiJournal.Enter


## Decal
Event | Raised By | Notes
--- | --- | ---
`OnHandleDecalRegistry`(Decal decal, DecalRegistry.DecalInfo decalInfo) | Celeste.Decal.Added
   
---

The source code for all events can be found [here](https://github.com/EverestAPI/Everest/blob/master/Celeste.Mod.mm/Mod/Everest/Everest.Events.cs).    
For questions and feedback, please contact @coloursofnoise on the Celeste [Discord](https://discord.gg/6qjaePQ).