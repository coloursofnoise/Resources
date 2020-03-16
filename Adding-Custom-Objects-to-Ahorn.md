[Ahorn](https://github.com/CelestialCartographers/Ahorn) is a visual level maker and editor for Celeste, based on the 
[Maple](https://github.com/CelestialCartographers/Maple) wrapper, written in Julia.  
This tutorial will explain how to integrate your custom Entities and Triggers with Ahorn, in order to access and place them from within the editor.

## Contents
- [**Setup**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#setup)
- [**Defining**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#defining)
- [**Placing**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#placing)
  - [Placement](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#placement)
  - [Adding dropdown options](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#adding-dropdown-options)
  - [Selection](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#selection)
- [**Rendering**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#rendering)
- [**Examples**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#examples)
  - [All you technically need](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#all-you-technically-need)

## Setup
Every distinct entity or trigger that you want to add to Ahorn needs to be defined in a `.jl` Julia language file within the `Ahorn` subfolder of your mod folder.
Within the `Ahorn` folder, entities must be placed in an `entities` folder, and triggers in `triggers`. Additionally, a `lang` folder can be used to provide [tooltips](https://github.com/EverestAPI/SpringCollab2020/blob/master/Ahorn/lang/en_gb.lang) for various options.

Every `.jl` file needs to start with the following code:
```julia
module YourModnameYourEntity
using ..Ahorn, Maple
```
This, similarly to C#, defines a "namespace" for your entity/trigger, and imports the Ahorn and Maple libraries for use.

Naming your module `YourModnameYourEntity` ensures that your module name will be unique across all mods. For example, [the Bubble Push Field entity in Spring Collab 2020](https://github.com/EverestAPI/SpringCollab2020/blob/master/Ahorn/entities/bubblePushField.jl) has a module named `SpringCollab2020BubblePushField`.

## Defining
Defining a custom entity or trigger for Ahorn will always look similar to the following:
```julia
@mapdef Entity "YourMod/YourEntity" YourEntity(x::Integer, y::Integer,
   attr1::String="default1", attr2::String="default2")
```
or
```julia
@mapdef Trigger "YourMod/YourTrigger" YourTrigger(x::Integer, y::Integer, 
   width::Integer=Maple.defaultTriggerWidth, height::Integer=Maple.defaultTriggerHeight)
```
The string (in quotes) should be the name of your [Custom Entity](https://github.com/EverestAPI/Resources/wiki/Your-First-Code-Mod#creating-custom-entities-and-triggers).

The Entity/Trigger constructor can take any number of arguments, which are then accessible from the EntityData object that is passed to your C# object's constructor.
Depending on the Type of the argument, it will automatically be displayed in the configuration panel for your entity/trigger within Ahorn.

**Note:** if one of your attributes is a float (`Number`), be sure to give it a float default value as well. That is, instead of using `foo::Number=2`, use `foo::Number=2.0`.

## Placing
### Placement
Ahorn gets any placeable entities and triggers from the `placements` constant; an `Ahorn.PlacementDict`, which is a series of `String`=>`Ahorn.EntityPlacement` pairs.
The `String` is what will show up in the Ahorn selection menu, and the `EntityPlacement` is a struct containing the information on the entity/trigger.

An `EntityPlacement` struct can be created using the `Ahorn.EntityPlacement` *function*, which takes four arguments:
```julia
# Required
func::Union{Function, Type},
# Optional
placement::String,
data::Dict{String, Any},
finalizer::Union{Function, Nothing}
```
- `func` in most cases will be YourEntity or YourTrigger.
- `placement` will be one of "point"(default), "rectangle", or "line", depending on which best suits your needs.  
- `data` allows for placement-specific attributes to be added to the EntityData. This is useful if you want to have multiple placements with different "default values" for your entity. For example, [Ahorn uses this to allow placing moon berries and winged strawberries directly](https://github.com/CelestialCartographers/Ahorn/blob/master/src/entities/strawberry.jl#L12).
- `finalizer` allows for adding a function that is run only when the entity is placed, or the preview is updated.

Ex:
```julia
const placements = Ahorn.PlacementDict(
   "Your Entity (AhornDemo)" => Ahorn.EntityPlacement(
      YourEntity,
      "point",
      Dict{String, Any}(
         "attr1" => "foo"
      ),
      function(entity)
         entity.data["attr2"] = "bar"
      end
   )
)
```

### Adding dropdown options
In order to define dropdown menus for some attributes, you can define `Ahorn.editingOptions` for your entity (simplified example from [Jump Throughs in Ahorn](https://github.com/CelestialCartographers/Ahorn/blob/master/src/entities/jumpthru.jl#L21)):
```julia
Ahorn.editingOptions(entity::Maple.JumpThru) = Dict{String, Any}(
  "texture" => String["wood", "dream", "temple", "templeB"],
  "surfaceIndex" => Dict{String, Int}(
    "Default" => -1,
    "Null" => 0,
    "Asphalt" => 1,
    "Car" => 2,
    "Dirt" => 3
  )
)
```

This makes the "texture" attribute a dropdown where you can select "wood", "dream", "temple" or "templeB", and where you can still type in custom values. 

The "surfaceIndex" attribute is a dropdown as well, with values "Default", "Null", "Asphalt", "Car" and "Dirt". The difference is that selecting "Dirt" will set the "surfaceIndex" attribute to 3. This is a way to show more easily understandable options to the user ("Dirt" is more explicit than "3").

**Note**: Maple already defines some lists for the base game (surface sound IDs, spike directions, position modes for triggers, etc). They are defined [here](https://github.com/CelestialCartographers/Maple/blob/master/src/enums.jl). You can directly use them if needed:
```julia
Ahorn.editingOptions(entity::MyEntity) = Dict{String, Any}(
  "surfaceIndex" => Maple.tileset_sound_ids
)
```

### Selection
Providing additional information to Ahorn on the placement of your entity can be done by overriding the `Ahorn.selection` function.
This function recieves the selected entity, and can be used to return an Ahorn.Rectangle that will be used to draw the selection.

Ex:
```julia
function Ahorn.selection(entity::YourEntity)
   x, y = Ahorn.position(entity)
   width = 10
   height = 10

   return Ahorn.Rectangle(x, y, width, height)
end
```

Other functions that can be overridden to affect the placement of your entity include `Ahorn.minimumSize` and `Ahorn.resizable`.

## Rendering
The main way to set how your entity is displayed within Ahorn is by overriding the `Ahorn.render` function.
This allows you to draw sprites, rectangles, lines, and other graphics through the 
[Cairo](https://github.com/JuliaGraphics/Cairo.jl) graphics library for julia.

Examples:
```julia
sprite = "collectables/strawberry/normal00"
Ahorn.render(ctx::Ahorn.Cairo.CairoContext, entity::YourEntity, room::Maple.Room) = Ahorn.drawSprite(ctx, sprite, 0,0)
```

```julia
function Ahorn.render(ctx::Ahorn.Cairo.CairoContext, entity::YourEntity, room::Maple.Room)
    x = Int(get(entity.data, "x", 0))
    y = Int(get(entity.data, "y", 0))

    width = Int(get(entity.data, "width", 32))
    height = Int(get(entity.data, "height", 32))

    Ahorn.drawRectangle(ctx, 0, 0, width, height)
end
```

A .zip file containing all graphics currently in the base game can be found [here](https://github.com/EverestAPI/Resources/wiki/Useful-links#dumped-graphics).


## Examples
### All you technically need:
```julia
module YourModule
using ..Ahorn, Maple

@mapdef Entity "YourMod/YourEntity" YourEntity(x::Integer, y::Integer)

const placements = Ahorn.PlacementDict(
   "Your Entity (AhornDemo)" => Ahorn.EntityPlacement(
      YourEntity
   )
)
```

Many more examples of various custom Entity and Trigger files can be found in the [Spring Collab 2020 repo](https://github.com/EverestAPI/SpringCollab2020/tree/master/Ahorn).

For questions and feedback, please contact @coloursofnoise on the Celeste [Discord](https://discord.gg/6qjaePQ).