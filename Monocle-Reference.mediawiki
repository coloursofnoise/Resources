The [Monocle Engine](https://bitbucket.org/MattThorson/monocle-engine/src) is an open source game engine, developed by Matt Thorson, 
that is based on the [MonoGame Framework](https://www.monogame.net/).  
It is based on the [TowerFall Ascension](http://www.towerfall-game.com/) core engine, and has since been used as the base for Celeste.

This guide will detail the basic game loop of the engine, as well as how different game elements fit together.  
The (incomplete) reference that follows is in no particular order, however they are loosely arranged into categories. 

:information_source: Note that this guide is written to give context to Celeste modding, and may not be fully applicable to other games that use the Monocle engine.

## Contents
- [**Function**](#Function)
- [**Structure**](#Structure)
- [**Reference**](#Reference) <!--markdown is a nightmare sometimes-->
  - [**Engine**](#Engine) <!-- Structures -->
  - [**Scene**](#Scene)
  - [**Tracker**](#Tracker)
    - [**Tracked Attribute**](#Tracked)
    - [**TrackedAs Attribute**](#TrackedAs) :warning: **Everest only**
  - [**Pooler**](#Pooler)
    - [**Pooled Attribute**](#Pooled)
  - [**Atlas**](#Atlas)
  - [**Camera**](#Camera)
  - [**BitTag**](#BitTag)
  - [**Coroutine**](#Coroutine) <!-- Functional -->
  - [**Alarm**](#Alarm)
  - [**Wiggler**](#Wiggler) <!-- Visual -->
  - [**Shaker**](#Shaker)
  - [**ParticleSystem**](#ParticleSystem)
    - [**Particle**](#Particle)
    - [**ParticleType**](#ParticleType)
    - [**ParticleEmitter**](#ParticleEmitter)
<!--
## Structure
Engine => Scene => Entity => Component

## Function
-->
<!--
## [Engine]()
`DeltaTime`
`RawDeltaTime`
-->
## [Tracker](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Util/Tracker.cs)
The `Tracker` class provides an efficient way of accessing select entities and components that are present in a scene.


:information_source: [Modified by Everest](https://github.com/EverestAPI/Everest/blob/master/Celeste.Mod.mm/Patches/Monocle/Tracker.cs) 
to include support for [`[TrackedAs]`](#TrackedAs) Attribute.

### [`[Tracked]`](https://bitbucket.org/MattThorson/monocle-engine/src/85205ffbfe927b41f5dfe85fdb3f09f42770ff1a/Monocle/Util/Tracker.cs#lines-389)
Marks an entity or component to be added to the [`Tracker`](#Tracker).
If `Inherited` is true, all classes that extend this one will also be tracked.

### [`[TrackedAs]`](https://github.com/EverestAPI/Everest/blob/master/Celeste.Mod.mm/Patches/Monocle/Tracker.cs) 
**:warning: This feature was added by Everest.**

When applied on an entity, this attribute makes the entity get tracked as another, already tracked entity.
This can be used to track a subclass of an entity with the [Tracked] tag that does not support inheritance.

:warning: While this can theoretically be used to track any entity/component as another one, it should be noted that some code may depend
on the objects returned being of the tracked type.

## [Pooler](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Util/Pooler.cs)


### [`[Pooled]`](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Util/Pooler.cs#lines-63)

## [BitTag](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Util/BitTag.cs)
The `BitTag` class allows for up to 32<!-- (limited by the size of an int)--> bit flags to be added to the program as needed, without needing to worry
about conflics.

## [Coroutine](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Components/Logic/Coroutine.cs)
A coroutine is a [Component](#Component) that, once added to an [Entity](#Entity) will update alongside the entity and step through an IEnumerator object.
It makes use of [Iteration Methods](https://docs.microsoft.com/en-us/dotnet/csharp/iterators#enumeration-sources-with-iterator-methods)
, where every time the coroutine is updated, it calls `MoveNext` on the IEnumerator.

Using a `yield return` statement in the method will determine how often the code is run, with two possible return types:
- Returning an `int` or `float` value will wait the specified number of seconds before trying to continue.
- Returning a `null` value will wait for the next update to continue.

Using a `yield break` statement will cause the coroutine to end when the statement is reached.

:information_source: [Modified by Everest](https://github.com/EverestAPI/Everest/blob/master/Celeste.Mod.mm/Patches/Monocle/Coroutine.cs) 
to add `Jump()` to skip the wait timer.

## [Alarm](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Components/Logic/Alarm.cs)


## [Wiggler](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Components/Logic/Wiggler.cs)

## [Shaker](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Components/Logic/Shaker.cs)
```csharp
Shaker(float time, bool removeOnFinish, Action<Vector2> onShake = null) // Starts on
Shaker(bool on = true, Action<Vector2> onShake = null)
```
Every time a Shaker is updated, it updates the the X and Y values of the Vector2 held in `Value` are randomized to be -1, 0, or 1, 
with a weight of 1/2 to be 0. The Vector2 is then passed to the `onShake` delegate.

### [ShakerList](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Components/Logic/ShakerList.cs)
```csharp
ShakerList(int length, float time, bool removeOnFinish, Action<Vector2[]> onShake = null) // Starts on
ShakerList(int length, bool on = true, Action<Vector2[]> onShake = null)
```
`ShakerList` provides a more concise way to manipulate multiple vectors than adding numerous Shakers to an entity.
The `length` parameter determines the number of vectors that are stored in `Values`, which will also be passed to the `onShake` delegate.

## [ParticleSystem](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Particles/ParticleSystem.cs)
```csharp
ParticleSystem(int depth, int maxParticles)
```
A ParticleSystem is an entity that provides a way to only display a maximum number of [particles](#Particle) on screen at any moment, 
removing the risk of overloading the game by trying to simulate too many particles at once.

To add a particle to the system, either pass it to the `Add(Particle particle)` method, 
or use one of the many `Emit(ParticleType particleType, ...)` methods to create them from a [ParticleType](#ParticleType) template.

:information_source: Each level in Celeste contains three ParticleSystems at different depths for background, foreground, and general particles.

### [Particle](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Particles/Particle.cs)
Particles are structs that contain information on an individual particle, as well as methods for updating and rendering it.
In order to simulate a particle, it needs to have a ParticleType associated with it, which is done by passing it to a [ParticleType](#ParticleType)'s `Create` method.

### [ParticleType](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Particles/ParticleType.cs)
```csharp
ParticleType() // Create a new ParticleType with default-initialized fields.
ParticleType(ParticleType copyFrom) // Create a copy of the copyFrom ParticleType.
```
A ParticleType represents a template from which [particles](#Particle) can be created.

ParticleTypes, once created, are stored in the static `ParticleType.AllTypes` field.

When creating a ParticleType, some of the following information may be useful:  

The `Direction` field is an angle (in radians) where 0 is down, moving counter clockwise as the angle increases.  
The direction will be modified by +- (`DirectionRange` / 2).

If `ScaleOut` is true, the particle size will cube out over its lifetime.

`Size` determines the scale of the texture, +- (`SizeRange` / 2).

If `SourceChoose` is set, the particle will use a texture from its choices.
Else, if `Source` is set, the particle will use its texture.
Else, the particle will use the texture stored in `Draw.Particle`.

The particle will spin at a rate chosen randomly from `SpeedMin` to `SpeedMax`, where positive is counter-clockwise, and negative is clockwise. :warning: UNTESTED
If `SpinFlippedChance` is true, the spin direction has a 50% chance of being flipped.

If `UseActualDeltaTime` is true, the particle will be updated based on `Engine.RawDeltaTime` instead of `Engine.DeltaTime`.

The `ParticleType` class contains a few enums that describe different particle behaviours:
```csharp
pubic enum ColorModes {
   Static, // Particle color will be set to `Color`.  
   Choose, // Particle color will be randomly chosen from `Color` and `Color2`.  
   Blink, // Particle color will be swap between `Color` and `Color2` every second.  
   Fade // Particle color will fade from `Color` to `Color2` from start to end of life.  
}
```
```csharp
public enum FadeModes {
   None, // Particle will not fade.  
   Linear, // Particle will fade linearly from start to end of life.  
   Late, // Particle will fade linearly starting when the particle has 1/4 life remaining.  
   InAndOut // Particle will fade in for first quarter, and fade out for last quarter of life.  
}
```
```csharp
public enum RotationModes {
   None, // Particle will start with the default orientation.  
   Random, // Particle will start rotated at a random angle.  
   SameAsDirection // Particle will always be rotated towards its direction of travel.  
}
```
### [ParticleEmitter](https://bitbucket.org/MattThorson/monocle-engine/src/default/Monocle/Components/Graphics/ParticleEmitter.cs)
```csharp
ParticleEmitter(ParticleSystem system, ParticleType type, Entity track, Vector2 position, Vector2 range, float direction, int amount, float interval)
```
A ParticleEmitter is a component that, once added, will emit `amount` particles every `interval` seconds, for as long as it is active.
Calling `Simulate(float duration)` will emit particles based on how many intervals would have elapsed in `duration`.
`SimulateCycle()` will emit exactly one interval's worth of particles.
