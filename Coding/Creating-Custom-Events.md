This is a guide on how to define a custom event in a code mod. If you are not familiar with the C# language, or do not have prior experience 
in making code mods for Celeste, [Lua Cutscenes](https://gamebanana.com/gamefiles/10788) may be a more suitable option.  
If you are interested in making code mods but don't know how, read [Your First Code Mod](Your-First-Code-Mod) to get started.


## Contents
- [**EventTrigger**](#EventTrigger)
- [**OnCustomEvent**](#OnCustomEvent)
- [**CustomEvent**](#CustomEvent-Attribute)
- [**CutsceneEntity**](#CutsceneEntity)
  - [**CutsceneNode**](#CutsceneNode)


## `EventTrigger`
In order to use any sort of custom event, an `EventTrigger` needs to be placed somewhere in the level.
Event Triggers work the same way as any other `Trigger`, and are activated when the player enters their hitbox.

The `event` data field is the ID of the event that will be triggered.
Event IDs should be unique, and should include the mod name or a nickname that is unlikely to be reused by another mod.

If an Event Trigger is placed on the edge of a screen, it may be necessary to set the `onSpawn` field to true in order to trigger the event immediately upon entering the screen.


## `OnCustomEvent`
Hooking [`EventTrigger.OnCustomEvent`](Everest-Events#EventTrigger) provides a way to execute nearly any action when an EventTrigger is entered.
Simply check that the eventID matches the desired event, and return `true` if it does, to notify the game that an appropriate event has been found.

:warning: While this can be a convenient way to test code, it is only recommended if there are no other predefined options.  
For example, an `EventTrigger` could be used to set level flags, or end a level, but if no other behaviour is desired, a `FlagTrigger` or `CompleteAreaTrigger` is a better alternative.


## `[CustomEvent]` Attribute
To create a custom entity that will be automatically added when the appropriate [`EventTrigger`](#EventTrigger) has been entered, create a class that extends `Monocle.Entity` and annotate it with the `[CustomEvent]` attribute
so that the game can detect it when it loads a map:
```cs
[CustomEvent("mymodname/myevent")]
class MyEvent : Entity { ... }
```

You have to define a constructor for the game to be able to build your event. The allowed signatures for this constructor are, in order of precedence:
* `public MyEvent(EventTrigger trigger, Player player, string eventID)`
* `public MyEvent()` 

You can also give a custom event multiple IDs (useful for backwards compatibility):
```cs
[CustomEvent("mymodname/myevent", "mynewmodname/myevent")]
```
or have different IDs call different static generator methods for your entity:
```cs
[CustomEvent(
    "mymodname/myeventup = LoadUp",
    "mymodname/myeventdown = LoadDown"
)]
public class MyEvent : Entity {

    public static Entity LoadUp(EventTrigger trigger, Player player, string eventID)
        => new MyEvent(player, eventID, Directions.Up);
    public static Entity LoadDown(EventTrigger trigger, Player player, string eventID)
        => new MyEvent(player, eventID, Directions.Down);

    [...]
}
```
If no generator method is specified in the CustomEvent ID, Everest will look for a generator method named `Load`.

:information_source: Note that a generator method, if provided, will take precedence over any defined constructors. 


## `CutsceneEntity`
One major use of Event Triggers is in triggering cutscenes, which is done by adding a `CustsceneEntity` to the Level.
This can be done using either of the methods described above.

`CutsceneEntity` is an abstract class that contains two required methods:

* `OnBegin(Level level)` should be used to set up the cutscene, and to add a new [`Coroutine`](Monocle-Reference#Coroutine) to execute the cutscene within.  
* `OnEnd(Level level)` should be used to clean up after the coroutine has finished. If necessary, the `WasSkipped` field should be checked in case the cutscene was ended prematurely.

`EndCutscene(Level level, bool removeSelf)` should be called at the end of the *coroutine*, to let the level know it has completed.


### `CutsceneNode`
Cutscene nodes are named points that can be placed in a level, and are used for reference from within a cutscene.  
They can be retrieved using `CutsceneNode.Find(string name)`.