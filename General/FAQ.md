## Sections:
- [**Playing Mods**](#playing-mods)
- [**Making Maps**](#making-maps)
- [**Making Code Mods**](#making-code-mods)


## Playing Mods

### Where do I Start?
Install [Olympus](https://everestapi.github.io/#installing-everest) (the installer and mod manager) and [Everest](https://everestapi.github.io/) (the mod loader).

### Where do I get mods?
Most people host their mods on [GameBanana](https://gamebanana.com/games/6460), but you can also find finished and work-in-progress mods posted in the `#modding_showcase` and `#modding_wip` channels of the [Celeste Discord](https://discord.gg/6qjaePQ).

### Can I mod my Nintendo Switch?
No. See [here](Nintendo-Switch-Modding) for more information.

### Which PC versions can be modded?
At the time of writing, the Steam, Epic Games, and itch.io versions **can** be modded. The only PC version that **cannot** be modded is from the Microsoft Store, as part of the Xbox Game Pass.  
For more information see [this post](https://discord.com/channels/403698615446536203/683777712115941407/774671383828496514) from the [Celeste Discord](https://discord.gg/6qjaePQ) (Paraphrased here):
>- **The game is encrypted** on a per-user license basis, meaning **no mods without cracking the game, even to just replace maps or text**.
>- It is built using the [Universal Windows Platform](https://docs.microsoft.com/en-us/windows/uwp/get-started/universal-application-platform-guide) and [.NET Native](https://docs.microsoft.com/en-us/dotnet/framework/net-native/net-native-and-compilation), meaning **the mod loader would have to be completely rewritten**.
>- In short, **UWP Celeste is as locked down as the Xbox version. Neither the Celeste devs nor the Modding Community can change this**.

### How can I backup my savedata?
Make a copy of the `Saves` folder.  
For the platform-specific location of this folder, look [here](https://www.pcgamingwiki.com/wiki/Celeste#Save_game_data_location).


## Making Maps

### What do you use to make maps?
[Ahorn](https://github.com/CelestialCartographers/Ahorn/blob/master/README.md), the community made map making program. It is a visual editor, with full support for modded entities.  
Ahorn can be installed through [Olympus](https://everestapi.github.io/#olympus) (recommended), or manually by following the instructions on the [README page](https://github.com/CelestialCartographers/Ahorn/blob/master/README.md).

### How do I play my custom map?
Once you have Everest installed, you can play your map simply by saving the `.bin` file from Ahorn into the Mods folder inside your Celeste install folder.  
*However*, it is recommended to follow the [Mod Structure](Mod-Structure) guide, since it allows you to do things like add custom assets, change your map's name in-game, and much more.

### Why do I have to include my nickname and modname in my folders?
While Celeste loads, Everest merges all custom assets with the ones from the base game. When it does, *it does not keep track of the mod that the assets came from*.  
This means that if two mods have a file in the same location *relative to the mod folder*, one will overwrite the other. This also applies to vanilla assets, and it is heavily discouraged to overwrite vanilla assets (textures, maps, dialog, etc) because it can be difficult to pin down which mod is overwriting them.  
:information_source: Some files are handled specially by Everest, and conflicting ones will be merged together rather than overwritten. This includes dialog files and top-level spritebanks.

### How do I change/add/configure ______ for my map?
Check the [Mod Structure](Mod-Structure) and [Map Metadata](Map-Metadata) pages, your question will likely be answered there. 

### What is ______ called in Ahorn?
See the list of [base-game Entities](Entity-and-Trigger-Documentation) for the commonly used names (The Celeste Fandom wiki is unreliable).

### How do I add a background to my map?
Read the [Stylegrounds](Adding-Stylegrounds) guide.

### How do I add custom _____ to my map?
1. Check for a wiki page that covers it (check the sidebar too!):  
   [Dialog](Adding-Custom-Dialogue), [Tilesets](Custom-Tilesets), [Portraits](Custom-Portraits), [Music/Audio](Adding-Custom-Audio)
2. Make sure to check the [Mod Structure](Mod-Structure) and [Map Metadata](Map-Metadata) pages too
3. Look for an existing [custom entity](https://max480-random-stuff.appspot.com/celeste/custom-entity-catalog) that does what you want
4. Ask in the `#modding_help` channel on the [Celeste Discord](https://discord.gg/6qjaePQ)

### What are "Flags"?
In short, a session flag is something that can be enabled or disabled.  
When starting a level, all flags start disabled and can be turned on/off with flag triggers, some custom entities, and within [Lua Cutscenes](https://gamebanana.com/gamefiles/10788).  
Flags are particularly useful for two things: 
1. When you enable a flag it stays enabled until the player exits or restarts your level so you can use it to make something happen only once.
2. Many things react to flags being enabled or disabled, like flag switch gates or stylegrounds, which makes it possible to easily create new interactions between different helpers.

The easiest to play around with flags is with the Lever and Lamp from the Pandora's Box mod. By setting the flag property of both entities to the same thing, you can toggle the session flag by flipping the lever, and the lamp will react accordingly.

## Making Code Mods

### What are you using to look inside Celeste's code?
There are many different [decompilers](https://en.wikipedia.org/wiki/Decompiler) that can be used to look at Celeste's code, commonly used are [dnSpy](https://github.com/dnSpy/dnSpy) and [ILSpy](https://github.com/icsharpcode/ILSpy).

### What are you using to modify Celeste's code?
While dnSpy lets you modify Celeste's code directly, it's not really a feasible way to distribute mods to others.  
Everest uses [MonoMod](https://github.com/MonoMod/MonoMod), which allows methods to be "hooked", or detoured, at runtime. If you do find something that _must_ be patched by Everest, ask for help in the `#modding_help` channel on the Discord server.

### How do I start making code mods?
See the tutorial [here](your-first-code-mod). This page assumes an existing knowledge of the C# programming language. 