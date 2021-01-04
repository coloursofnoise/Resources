# Table of contents

* [Getting started for mapping](#getting-started-for-mapping)
* [Getting started for code modding](#getting-started-for-code-modding)
* [Adding content to your mod](#adding-content-to-your-mod)
  * [Adding More Maps](#adding-more-maps)
  * [Adding Dialogue](#adding-dialogue)
  * [Adding Graphics](#adding-graphics)
  * [Adding Custom Audio](#adding-custom-audio)
  * [Adding Custom Tutorial Ghosts](#adding-custom-tutorial-ghosts)
* [Using Helper Mods](#using-helper-mods)
* [Packaging your mod for publishing](#packaging-your-mod-for-publishing)
* [Optional Dependencies for everest.yaml (advanced)](#optional-dependencies-for-everestyaml-advanced)
* [Complete Reference](#complete-reference)
  * [Formats](#formats)
  * [File Layout](#file-layout)
  * [Metadata](#metadata)
* [Examples](#examples)
  * [Code Mod](#code-mod)
  * [Level Mod](#level-mod)

# Mod Structure

* * *

<div>

##### PREREQUISITES

*   Everest: [Website](https://everestapi.github.io/)
*   Zipping software, f.e. 7zip: [Website](http://7-zip.org/)

</div>

* * *

## Getting started for mapping

To get started and playtest your map quickly, you can just save your map as a bin file in your Mods folder next to Celeste (`Mods/mymap.bin`). It will appear as "uncategorized" in-game.

But you will need to get a folder structure for your mod as soon as:
- you want to publish your map, and want to package it in a zip
- or, you need to have custom dialogue, graphics, audio, etc.

To do that:
- create a directory named after your mod in the Mods folder, for example `Mods/yourmod`
- drop your map inside it, in `Mods/yourmod/Maps/yournickname/campaignname/1-yourmap.bin`
  - a "campaign" is a group of maps in chapter select. For example, vanilla Celeste is a campaign with 11 chapters (counting Prologue and Epilogue).
  - the `1-` prefix in the bin name will be useful if you want to make a campaign with multiple chapters.
- create the `Mods/yourmod/Dialog` directory (:warning: not Dialogue) and create a file named English.txt in it. Add those lines to it:
```
yournickname_campaignname= Your Campaign Name
yournickname_campaignname_1_yourmap= Your Map Name
```
Now, your map should show up in-game in its own category, and have the name you defined in your English.txt. If this doesn't work, double-check the file isn't actually called English.txt.txt. For this, check this box to see the actual file name:

![hide file extensions](https://cdn.discordapp.com/attachments/445236692136230943/709705613692895302/windows_10_file_name_extensions_checkbox.png)

- create an everest.yaml file at `Mods/yourmod/everest.yaml`. Here is how it should look like:
```yaml
- Name: YourModName
  Version: 1.0.0
  Dependencies:
    - Name: Everest
      Version: 1.2330.0
```
Replace 1375 with the version of Everest you're using, and YourModName with your mod name (it should be unique, and you should not change it once your map is published).

You are now ready to go and you will be able to add more folders / files to `Mods/yourmod` when you will need to!

## Getting started for code modding

_This page covers mod structure for code mods. To get started with code modding itself, check [Your First Code Mod](Your-First-Code-Mod)._

Once you compiled your mod, you should get a DLL (often in a `bin/Debug/net452` folder or similar). In terms of mod structure, all you need to do is:
- create a `Mods/yourmod` folder
- have the DLL somewhere inside it
- create an everest.yaml file (`Mods/yourmod/everest.yaml`) looking like this:
```yaml
- Name: YourModName
  Version: 1.0.0
  DLL: Code/mymod.dll
  Dependencies:
    - Name: Everest
      Version: 1.2330.0
```
Replace:
- 1375 with the version of Everest you're using
- YourModName with your mod name (it should be unique, and you should not change it once your map is published)
- `Code/mymod.dll` with the path to your mod's DLL (for example, here, Everest would expect the DLL to be in `Mods/yourmod/Code/mymod.dll`).

If you are making a helper, **pay particular attention to the version number**, since your mod is going to be used as a dependency: Everest uses [semantic versioning](https://semver.org/). It means that version numbers are on the format MAJOR.MINOR (or MAJOR.MINOR.PATCH), and that **changing MAJOR means you made a change that would break mods depending on your helper**, which you usually don't want.

So, if a mod depends on YourMod 1.3:
- installing YourMod 1.0 won't work
- installing YourMod 1.3 will work (of course)
- installing YourMod 1.6 will work
- **installing YourMod 2.0 won't work**. The user will have to get YourMod 1.x instead.

## Adding content to your mod

### Adding More Maps

**If you want to make another chapter for your campaign**, just save the map bin in `Mods/yourmodname/Maps/yourname/yourcampaignname` next to your existing chapter. They will appear next to each other in chapter select.

**If you want to make a B-Side or C-Side for `1-mymap.bin`**, save the map bin next to it, and name it `1-mymap-B.bin` or `1-mymap-C.bin`.

### Adding Dialogue

To add dialogue, just edit `Mods/yourmod/Dialog/English.txt` and add more lines to it:
```
yourmodname_campaignname_dialogid=
	[MADELINE left normal]
	Yay it works!
```
Keep in mind that all your dialog IDs should start with `yourmodname_campaignname_` to be sure they are unique.

You can also add more languages (for example, `Mods/yourmod/Dialog/French.txt`). If a language does not exist, the game will use English instead.

For more details about how dialogue works, refer to [Adding Custom Dialogue](Adding-Custom-Dialogue).  
For a reference for adding custom portraits, see [here](Custom-Portraits)

### Adding Graphics

All custom graphics go to `Mods/yourmod/Graphics`. For example,
- if you want to add decals, drop them in `Mods/yourmod/Graphics/Atlases/Gameplay/decals/yourmodname/campaignname/decal.png`. The decal's dimensions should be multiples of 16.
- if you want to add stylegrounds, drop them in `Mods/yourmod/Graphics/Atlases/Gameplay/bgs/yourmodname/campaignname/bg.png`
- to add Everest custom NPC textures, drop the frames in `Mods/yourmod/Graphics/Atlases/Gameplay/characters/yourmodname/campaignname/animXX.png` then use `yourmodname/campaignname/anim` in the NPC's properties.
- to add a custom icon to your map, drop it in `Mods/yourmod/Graphics/Atlases/Gui/areas/yourmodname/campaignname/mymapicon.png` and set the "title banner icon" to `areas/yourmodname/campaignname/mymapicon` in your map's metadata in Ahorn.

**You should always have your mod name and campaign name in the path to prevent conflicts.**

If you are code modding, you can access those textures in code as well: check [Adding Sprites](Adding-Sprites) for more details.

### Adding Custom Audio

_Check the [Audio: How Tos](Adding-Custom-Audio) to learn how to make a custom bank file._

Once you built a bank with your custom audio, drop the .bank and .guids.txt file to the `Mods/yourmod/Audio` directory: `Mods/yourmod/Audio/yourmodname_campaignname.bank` and `.guids.txt`. Everest will load the bank, and you will be able to use events in it as background music in Ahorn, or in code mods.

### Adding Custom Tutorial Ghosts

You can record a tutorial with, for example, [Kayden's Commands](https://gamebanana.com/gamefiles/10271). Open the debug console, type `start_rec`, do the action to record, then type `stop_rec`. You'll find the result in `Content/Tutorials/CustomPlaybacks/latestCustomRecording.bin`.

Move this file to `Mods/yourmod/Tutorials/yourname/campaignname/tutorial.bin`. Then, place a "player playback" and set its tutorial to `yourname/campaignname/tutorial`. The ghost will now replay the action you recorded!

## Using Helper Mods

When making maps, you can use helper mods: you can find the list [on GameBanana, under the Game files category](https://gamebanana.com/gamefiles/games/6460). Just install one of them as you would install any other mod and restart Ahorn to access the entities/triggers it provides.

When you use something from a helper, you must _add a dependency_ to this helper, to be sure that people that play your map also have it installed. To do that:
- open the helper's zip, and open its everest.yaml. You should see something like this:
```yaml
- Name: FrostHelper
  Version: 1.17.6
  DLL: Code/FrostTempleHelper/bin/Debug/FrostTempleHelper.dll
  Dependencies:
    - Name: Everest
      Version: 1.1375.0
```
- pick the two first `Name` and `Version` lines.
- open your own everest.yaml, and add those two lines under `Dependencies`. It should now look like this:
```yaml
- Name: YourModName
  Version: 1.0.0
  Dependencies:
    - Name: Everest
      Version: 1.1375.0
    - Name: FrostHelper
      Version: 1.17.6
```
**Be sure that all lines in Dependencies are aligned correctly** and add/remove spaces if this is not the case. YAML is very picky about that.

If you want to check that you added the dependency correctly, simply remove the helper zip from your Mods folder. When you start up the game, Everest should tell you it is missing, and offer you to install it in Mod Options.

## Packaging your mod for publishing

To get the zip to be published on GameBanana, just go to `Mods/yourmodname`, select everything and compress it (for example `Send to > Compressed folder` on Windows, or `7-Zip > Add to yourmodname.zip` if you have 7-Zip installed). **Be sure to make a zip archive (not a rar or a 7z one)**.

When you open your zip, you should see `Dialog`, `Maps` and `everest.yaml` right away, without needing to open another folder.

If you did that correctly, publish the zip on GameBanana, and a "Everest 1-click installer" button should appear after a bit!

## Optional Dependencies for everest.yaml (advanced)

Optional dependencies are helpful in two cases:
- You want your mod to load after another mod if it is installed, but you don't want to force the user to have that mod (like a regular dependency would). This is for example useful if you have a skin mod that reskins vanilla and the Spring Collab: you want your skin to load after the Spring Collab to override its textures, but you don't want to force the player to download the Spring Collab if they just want to play vanilla.
- You want to prevent your mod from loading if another mod is present, but outdated (useful in case you know both mods are incompatible).

For example, if you have a mod called `TestMod123` and know it will crash if a Randomizer version lower than 1.4.0 is installed, you can write:
```yaml
- Name: TestMod123
  Version: 1.0.0
  Dependencies:
    - Name: Everest
      Version: 1.2002.0
  OptionalDependencies:
    - Name: Randomizer
      Version: 1.4.0
```

- If `Randomizer` 1.4.0 is installed, `TestMod123` will load right after it.
- If `Randomizer` is not installed, `TestMod123` **will load anyway**.
- If `Randomizer` 1.3.0 is installed, `TestMod123` will **not** load. The main menu will display "1 mod failed to load", and the "Install missing dependencies" button will update `Randomizer`.

_Optional Dependencies were added in Everest 2002._

## Complete Reference

### Formats

**Everest currently supports the following formats:**

*   Mod `.zip`s: Best used when using other's mods or when uploading your mod somewhere.
*   Mod subdirectories: Best used for prototyping mods on your own machine.

A mod can't contain "submods", unless a code mod loads the "submods" dynamically.

All files in a mod `.zip` must be on the top level (root) and visible when just opening the `.zip` file. `YourMod.zip` shouldn't contain another `YourMod` folder.

* * *

<div>

##### NOTE

A code mod can dynamically load external mod content and mod assemblies.  
Dynamically loaded mods aren't restricted by the above formats, but rather by how the "supporting" mod loads them.  
The following file layout still applies to dynamically loaded mods.

</div>

* * *

### File Layout

Mods can contain custom content, both overrides / replacements (when supported) and new content. The content paths match the originals as close as possible. Paths are case sensitive.

Mods must contain a [`everest.yaml` metadata file.](#metadata)

**The following content mappings are supported out of the box:**

*   `Graphics/Atlases/*.png`: Replace or add textures.
    *   Supports `.meta` definition files.
    *   `Graphics/Atlases/Gui/title.png`
        *   Atlas: `Gui`
        *   Texture: `title`
    *   `Graphics/Atlases/Gameplay/scenery/sign.png`
        *   Atlas: `Gameplay`
        *   Texture: `scenery/sign`
*   `Maps/*.bin`: Add new maps.
    *   Supports `.meta` definition files.
    *   Replacing vanilla maps not supported.
    *   `Maps/Author/LevelSet/1-Name.bin`
        *   Default SID (String ID): `Author/LevelSet/1-Name`
        *   Default LevelSet: `Author/LevelSet`
        *   Default Name: `1-Name`
*   `Dialog/*.txt`: Add new texts.
    *   Only contains the texts belonging to the mod.
    *   Multiple mods are allowed to occupy the same path. F.e. two mods can contain their own `Dialog/English.txt` files.
    *   Replacing existing texts not supported.
    *   `Dialog/English.txt` is always used when a dialog key cannot be found in another language.
*   `Audio/*.bank` + `Audio/*.guids.txt`: Add new FMOD audio banks containing custom / replacement events.
    *   Works with new banks created in the [Celeste FMOD project](https://www.fmod.com/download#demos)
    *   Requires manually exported `GUIDs.txt`, renamed to `your bank name.guids.txt`
    *   To replace the game's events, assign any modified events to your new mod bank. Please avoid overriding the game's original banks.

**With a few exceptions, each file path can only be occupied by one file.**

*   If mod #1 contains `Graphics/Atlases/Gui/title.png` and `Graphics/Atlases/Gui/title.meta.yaml`, it overrides the texture shipped with Celeste.
*   If an additional mod #2 contains `Graphics/Atlases/Gui/title.png`, it overrides the texture shipped with #1\. The meta definitions of #1 still apply.

All "supported" mod content can be loaded with the usual Celeste methods. For example, a texture in an atlas can be accessed with the matching atlas.

All "unsupported" mod content can be loaded by codemods via [`Everest.Content.Get*` (usage)](/api/Celeste.Mod.Everest.Content.html#Celeste_Mod_Everest_Content_Get_System_String_System_Boolean_).

For content inside of `.zip`s and subdirectories, all mod content is directly contained in the `.zip` / subdirectory. For example, the mod `.zip` should directly contain a `Maps` directory. The `Maps` directory should not be in a `Content` subdirectory.

For content in form of embedded resources inside of `.dlls`, all mod content requires a `Content\` path prefix Embedded resources normally don't have logical file paths in the traditional sense - the C# compiler mangles the filepath into something C#-friendly. **To fix content embedded into .dlls, set a logical name for all `Content\` `<EmbeddedResource>`s in your `.csproj`:**

    <EmbeddedResource Include="Content\Dialog\English.txt">
      <LogicalName>Content\Dialog\English.txt</LogicalName>
    </EmbeddedResource>

Additionally, for embedded resources, the C# compiler requires filepaths with `\` as the directory separator, but the content is accessed with `/` as the directory separator. **Everest replaces all `\` symbols with `/` symbols in embedded resource paths at runtime.**

### Metadata

The `everest.yaml` file in your mod contains a list of all "module" names (ID), version, (optional) DLL paths and any dependencies.

If you've got no mod DLLs, leave that field out. If you've got multiple modules in separate DLLs, list them separately.

**The version should match the [semver (semantic versioning) format](https://semver.org/):**

*   The MAJOR version must match to prevent breakages caused by API changes (f.e. API removals).
*   The MINOR version must rise with each backwards-compatible API change (f.e. API additions). If the mod depends on a new version but an older version is installed, the mod won't load.
*   The PATCH version is also checked: if the mod depends on a new version but an older version is installed, the mod won't load.

Adding a dependency to a mod with version `0.0.*` ignores the above checks at your own risk.

## Examples

### Code Mod

**File list:**

*   `everest.yaml`
*   `GhostMod.dll`
*   `GhostNetMod.dll`

**Embedded resources:**

*   `Content\Dialog\English.txt`: Mod option texts.

**Metadata:**

    - Name: GhostMod
      Version: 1.2.1
      DLL: GhostMod.dll
      Dependencies:
        - Name: Everest
          Version: 1.0.0

    - Name: GhostNetMod
      Version: 1.3.4
      DLL: GhostNetMod.dll
      Dependencies:
        - Name: Everest
          Version: 1.0.0
        - Name: GhostMod
          Version: 1.2.1

*   The mod will load with Everest `1.0+.*`, meaning `1.0.*`, `1.1.*`, `1.2.*`, ...
*   The mod won't load with Everest older than `1.0.0`.
*   The mod won't load with Everest `2.*.*`, `3.*.*`, `4.*.*` or similar. The API has changed in a way that could break the mod.

### Level Mod

**File list:**

*   `everest.yaml`
*   `Dialog/English.txt`: LevelSet and chapter names.
*   `Maps/Cruor/Mario11/Cruor-Secret.bin`: A-side map binary.
*   `Maps/Cruor/Mario11/Cruor-Secret.meta.yaml`: Chapter metadata. Always the `.meta` of the A-side binary.
*   `Maps/Cruor/Mario11/Cruor-Secret-B.bin`: B-side map binary. The A-side / chapter `.meta` links to this.
*   `Graphics/Atlases/Gui/areas/Cruor/Mario11/secret.png`, `secret_back.png`: The chapter selection screen icon and its backside (when flipping).
*   `Graphics/Atlases/Gameplay/decals/Cruor/Mario11/*.png`: Any decals used by the A-side or B-side map `.bin`s.
*   `Graphics/Atlases/Ending-Cruor-Secret-1/*.png`, ...: Chapter completion screen textures. The chapter `.meta` links to this.