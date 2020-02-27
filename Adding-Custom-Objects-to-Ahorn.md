[Ahorn](https://github.com/CelestialCartographers/Ahorn) is a visual level maker and editor for Celeste, based on the 
[Maple](https://github.com/CelestialCartographers/Maple) wrapper for celeste, written in Julia.  
This tutorial will explain how to integrate your custom Entities and Triggers with Ahorn, in order to access and place them from within the editor.

## Contents
- [**Setup**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#setup)
- [**Defining**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom-Objects-to-Ahorn#defining)
- [**Placing**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom_Objects-to-Ahorn#placing)
  - [Placement](https://github.com/EverestAPI/Resources/wiki/Adding-Custom_Objects-to-Ahorn#placement)
  - [Selection](https://github.com/EverestAPI/Resources/wiki/Adding-Custom_Objects-to-Ahorn#selection)
- [**Rendering**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom_Objects-to-Ahorn#rendering)
- [**Examples**](https://github.com/EverestAPI/Resources/wiki/Adding-Custom_Objects-to-Ahorn#examples)
  - [All you technically need](https://github.com/EverestAPI/Resources/wiki/Adding-Custom_Objects-to-Ahorn#all-you-technically-need)

## Setup
Every distinct entity or trigger that you want to add to Ahorn needs to be defined in a `.jl` Julia language file within the `Ahorn` subfolder of your mod folder.
Within the `Ahorn` folder, entities must be placed in an `entities` folder, and triggers in `triggers`. Additionally, a `lang` folder can be used to provide tooltips for various options.

Every `.jl` file needs to start with the following code:
```julia
module YourModule
using ..Ahorn, Maple
```
This, similarly to C#, defines a "namespace" for your entity/trigger, and imports the Ahorn and Maple libraries for use.

## Defining
Defining a custom entity or trigger for ahorn will always look similar to the following:
```julia
@mapdef Entity "YourMod/YourEntity" YourEntity(x::Integer, y::Integer,
   attr1::String="default1, attr2::String="default2")
```
or
```julia
@mapdef Trigger "YourMod/YourTrigger" YourTrigger(x::Integer, y::Integer, 
   width::Integer=Maple.defaultTriggerWidth, height::Integer=Maple.defaultTriggerHeight)
```
The string (in quotes) should be the name of your [Custom Entity](https://github.com/EverestAPI/Resources/wiki/Your-First-Code-Mod#creating-custom-entities-and-triggers).

The Entity/Trigger constructor can take any number of arguments, which are then accessible from the EntityData object that is passed to your C# object's constructor.
Depending on the Type of the argument, it will automatically be displayed in the configuration panel for your entity/trigger within Ahorn.


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
`func` in most cases will be YourEntity/YourTrigger, and `placement` will be one of "point"(default), "rectangle", or "line", depending on which best suits your needs.  
`data` allows for placement-specific attributes to be added to the EntityData,
and `finalizer` allows for adding a function that is run only when the entity is placed, or the preview is updated.

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

Many more examples of various custom Entity and Trigger files can be found in the [Sprint Collab 2020 repo](https://github.com/EverestAPI/SpringCollab2020/tree/master/Ahorn).

For questions and feedback, please contact @coloursofnoise on the Celeste [Discord](https://discord.gg/6qjaePQ).