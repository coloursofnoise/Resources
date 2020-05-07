This is a guide on how to define a custom Entity or Trigger in a code mod. This is the part that needs to be written in C# 
 in Visual Studio, and then compiled into a .dll file. For information on integrating a _pre-existing_ Entity or Trigger with Ahorn for use in maps, please see [here](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn).

## Contents
* [Attributes](#creating-custom-entities-and-triggers)
  * [[CustomEntity]](#customentity)
  * [[Tracked]](#tracked)
  * [[TrackedAs]](#trackedas)
  * [[RegisterStrawberry]](#registerstrawberry)  
<br/>

### `[CustomEntity]`
To create a custom entity (objects you can place in a map), create a class that extends `Monocle.Entity` and annotate it with `[CustomEntity]` so that the game can detect it when it loads a map:
```cs
[CustomEntity("SpringCollab2020/SidewaysJumpThru")]
class SidewaysJumpThru : Entity { ... }
```

Triggers are simply an extension of the  Entity class, so using the `[CustomEntity]` annotation works for them too (just extend `Monocle.Trigger` instead of `Entity`).

You have to define a constructor for the game to be able to build your entity. The allowed signatures for this constructor are, in order of precedence:
* `public MyEntity(EntityData data, Vector2 offset, EntityID id)`
* `public MyEntity(EntityData data, Vector2 offset)`
* `public MyEntity(Vector2 offset)`
* `public MyEntity()` 

<br></br>

To be able to place your entity in Ahorn, you will also have to create an [**Ahorn plugin**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn) for it. There are numerous examples of those on the [Spring Collab 2020 repo](https://github.com/EverestAPI/SpringCollab2020/tree/master/Ahorn). The `entities` and `triggers` folders contain the entity/trigger plugins, and the `lang` folder contains the tooltips for the different options. To make the link between the Ahorn plugin and your entity in code, the parts in bold have to match:

Ahorn plugin:
> @mapdef Trigger "**SpringCollab2020/NoRefillField**" NoRefillField(x::Integer, y::Integer, width::Integer=Maple.defaultTriggerWidth, height::Integer=Maple.defaultTriggerHeight)

Code:
> [CustomEntity("**SpringCollab2020/NoRefillField**")]
> class NoRefillField : Trigger { ... }

<br></br>

You can also give a custom entity multiple IDs (useful for backwards compatibility):
```cs
[CustomEntity("ExtendedVariantTrigger", "ExtendedVariantMode/ExtendedVariantTrigger")]
```
or have different IDs call different static generator methods for your entity:
```cs
[CustomEntity(
    "triggerSpikesOriginalUp = LoadUp",
    "triggerSpikesOriginalDown = LoadDown"
)]
public class TriggerSpikesOriginal : Entity {

    public static Entity LoadUp(Level level, LevelData levelData, Vector2 offset, EntityData entityData)
        => new TriggerSpikesOriginal(entityData, offset, Directions.Up);
    public static Entity LoadDown(Level level, LevelData levelData, Vector2 offset, EntityData entityData)
        => new TriggerSpikesOriginal(entityData, offset, Directions.Down);

    [...]
}
```
If no generator method is specified in the CustomEntity ID, Everest will look for a generator method named `Load`.

ℹ️ Note that a generator method, if provided, will take precedence over any defined constructors. 

***

Other useful attributes for custom entity classes are:

### `[Tracked]`

If you annotate your entity with `[Tracked]`, you will be able to search for it by using `Scene.Tracker.GetEntities<MyEntity>()`. Using this method to look up entities of a certain type is more efficient than using, for example, `Scene.Entities.OfType<MyEntity>()`.

This attribute has a parameter, defaulting to false, determining if child classes should be included in the search results as well. This means that if we have a class defined as:
```cs
public class MyChildEntity : MyEntity { ... }
```

`Scene.Tracker.GetEntities<MyEntity>()` will return:
- all MyEntity objects in the scene if MyEntity is annotated with `[Tracked]`
- all MyEntity **and MyChildEntity** objects if MyEntity is annotated with `[Tracked(true)]`  

### `[TrackedAs]`

If you annotate your entity with `[TrackedAs(type)]`, it will be tracked in the same way as the type you specify. For example:

```cs
[TrackedAs(typeof(Water))]
public class MyWater : Water { ... }
```

This means "MyWater should be tracked exactly the same way as Water is". That way:
- `CollideCheck<Water>()` will also check collisions with MyWater, making Madeline able to swim in your custom water
- `Scene.Tracker.GetEntities<Water>()` also returns `MyWater` entities, etc.

[Used here in Spring Collab 2020](https://github.com/EverestAPI/SpringCollab2020/blob/master/Entities/FlagToggleWater.cs).

This is useful when developing an entity extending a tracked vanilla one, when the vanilla one has `[Tracked(false)]` making children not tracked by default.

### `[RegisterStrawberry]`

This attribute can be placed on any class that extends Strawberry or implements IStrawberry. It allows custom strawberries to be taken into account correctly in the total strawberry count, or in the strawberry tracker in the pause menu for example.

This attribute is used like this:
```cs
[CustomEntity("SpringCollab2020/CassetteFriendlyStrawberry")]
[RegisterStrawberry(true, false)]
class CassetteFriendlyStrawberry : Strawberry { ... }
```
This has 2 parameters:
- **isTracked**: whether the strawberry should be counted in the maximum berry count, and should show up on the checkpoint card / the pause menu tracker. Its checkpoint ID and order will be auto-assigned by Everest in this case.
- **blocksNormalCollection**: whether the berry has specific collection rules, like golden berries for example. In this case, it will allow berries behind it in the "berry train" to be collected.

For example, in vanilla:
- red berries are tracked and do not block normal collection
- golden berries are untracked and block normal collection
- the moon berry is untracked and does not block normal collection 

If your custom berry doesn't extend `Strawberry` and you want to have seeds behaving normally, you can have your custom berry implement `IStrawberrySeeded`, then use the `GenericStrawberrySeed` class instead of vanilla strawberry seeds. See [Glass Berry](https://github.com/EverestAPI/SpringCollab2020/blob/master/Entities/GlassBerry.cs) for an example.