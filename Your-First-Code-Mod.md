# Your First Code Mod

----

<div>
<h5>PREREQUISITES</h5>
<p>

- Everest: [Website](https://everestapi.github.io/)
- Visual Studio 2015 or newer. MonoDevelop instructions are different.

</p>
</div>

----

Every Everest code mod starts out as a C# (.NET Framework) class library targeting the .NET Framework 4.5.2 (same as Celeste itself).

## Project setup

----

<div>
<h5>NOTE</h5>
<p>

If you want a more traditional C# project setup, follow the [old advanced project setup instructions](https://github.com/EverestAPI/EverestAPI.github.io/blob/a789878761965db62c4f3c98f2bda58828e307a4/tutorials/firstcodemod.md#project-setup).

</p>
</div>

----

This setup doesn't require NuGet or git, but if you're a Windows user, you'll need to switch to the OpenGL branch. Linux and macOS users are already using FNA. **Everest will relink your mod from FNA to XNA at runtime.**
- In Steam, right-click the game in your library, select "Properties" and select the `opengl` "beta".
- In itch, simply install the Celeste Windows OpenGL version.
- Epic Games is already using FNA

After the update has finished, make sure to reinstall Everest.

- Open your C# IDE (f.e. Visual Studio 2015).
- Create a new project.
- In the top bar, select `.NET Framework 4.5.2`
- In the left bar, select `Installed` > `Visual C#`
- Select the template `Class Library` or `Class Library (.NET Framework)` (**not** `Standard`, `Core`, `Portable`, `Universal Windows`, ...).
- Create your mod in Celeste/Mods

The dialog should look like this:

![1-newproj](https://user-images.githubusercontent.com/1200380/55094149-1a7a3f80-50b6-11e9-89bc-939573f4b578.png)

- Create a new `everest.yaml` text file with the following content:

```yaml
- Name: YourMod
  Version: 1.0.0
  DLL: Code/bin/Debug/YourMod.dll
  Dependencies:
    - Name: Everest
      Version: 1.0.0
```

----

<div>
<h5>NOTE</h5>
<p>

For more info about the mod structure, the `everest.yaml` format, how to add extra content and on how to zip up your mod, [read the mod structure page](https://github.com/EverestAPI/Resources/wiki/Mod-Structure).

</p>
</div>

----

- Right-click your project's "References" and select "Add Reference...", then "Browse..." into your Celeste installation directory and setup your references like on the following screenshot:

![2-refs](https://user-images.githubusercontent.com/1200380/55094153-1bab6c80-50b6-11e9-8135-2d484d589ab4.png)

----

<div>
<h5>IMPORTANT</h5>
<p>

Make sure to select all those references, right-click > "Properties" and set "Copy Local" to "False", or you will accidentally include copies of those files in your mod!

</p>
</div>

----

----

<div>
<h5>IMPORTANT</h5>
<p>

If you want to maintain cross-platform compatibility, make sure to only use .NET Framework system libraries from this list.
- System
- System.Configuration
- System.Core
- System.Data
- System.Drawing (available, but behaves unpredictably)
- System.Runtime.Serialization
- System.Security
- System.Xml
- System.Xml.Linq

This means: Microsoft.CSharp, System.Windows.Anything, System.IO.Compression and other libraries must be removed from your references.  
For an up-to-date list, check the [list of precompiled MonoKickstart libraries](https://github.com/flibitijibibo/MonoKickstart/tree/master/precompiled), as Celeste uses them for Linux / macOS.

</p>
</div>

----

## Module class

Your module class should look similar to the example.

----

<div>
<h5>NOTE</h5>
<p>

This example only shows a subset of Everest's capabilities.  
[**Read the full `EverestModule` documentation here.**](https://everestapi.github.io/api/Celeste.Mod.EverestModule.html)

</p>
</div>

----

```cs
// Example usings.
using Celeste.Mod.UI;
using FMOD.Studio;
using Microsoft.Xna.Framework;
using Monocle;
using Celeste;
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Celeste.Mod.Example {
    public class ExampleModule : EverestModule {

        // Only one alive module instance can exist at any given time.
        public static ExampleModule Instance;

        public ExampleModule() {
            Instance = this;
        }

        // Check the next section for more information about mod settings, save data and session.
        // Those are optional: if you don't need one of those, you can remove it from the module.

        // If you need to store settings:
        public override Type SettingsType => typeof(ExampleModuleSettings);
        public static ExampleModuleSettings Settings => (ExampleSettings) Instance._Settings;

        // If you need to store save data:
        public override Type SaveDataType => typeof(ExampleModuleSaveData);
        public static ExampleModuleSaveData SaveData => (ExampleModuleSaveData) Instance._SaveData;

        // If you need to store session data:
        public override Type SessionType => typeof(ExampleModuleSession);
        public static ExampleModuleSession Session => (ExampleModuleSession) Instance._Session;

        // Set up any hooks, event handlers and your mod in general here.
        // Load runs before Celeste itself has initialized properly.
        public override void Load() {
        }

        // Optional, initialize anything after Celeste has initialized itself properly.
        public override void Initialize() {
        }

        // Optional, do anything requiring either the Celeste or mod content here.
        public override void LoadContent() {
        }

        // Unload the entirety of your mod's content. Free up any native resources.
        public override void Unload() {
        }

    }
}
```

## Mod settings, session and save data

Mods can define several classes to save extra data:
* **Mod settings** (`EverestModuleSettings`): for _global_ data (for example settings). Those can appear in Mod Options, and are saved in `Saves/modsettings-[modname].celeste`.
* **Mod save data** (`EverestModuleSaveData`): for data that is specific to a save file (if the player loads another save, other save data will be used). Can be useful to save stats or the player's progress for example. Saved in `Saves/[savenumber]-modsave-[modname].celeste`.
* **Mod session** (`EverestModuleSession`): for data that is specific to a play session. This is reset each time the player starts a level, so this is reset if the player restarts the chapter, but is saved if they choose to save & quit. Can be useful to save the state of an entity for example. Saved in `Saves/[savenumber]-modsession-[modname].celeste`.

Your settings class should look similar to the example.

Save data and session classes are very similar, but inherit from `EverestModuleSaveData` / `EverestModuleSession` and the `Setting*` attributes are ignored.

----

<div>
<h5>NOTE</h5>
<p>

**All entries must be properties**, unless you're overriding `LoadSettings` and `SaveSettings` / `LoadSaveData` and `SaveSaveData` / `LoadSession` and `SaveSession` to bypass YamlDotNet's restrictions.

This example only shows a subset of Everest's capabilities.  
[**Read the full `EverestModuleSettings` documentation here.**](https://everestapi.github.io/api/Celeste.Mod.EverestModuleSettings.html)

For all settings attributes, search for `Celeste.Mod.Setting` in the Everest API.

</p>
</div>

----

```cs
// Example usings.
using Celeste;
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using YamlDotNet.Serialization;

namespace Celeste.Mod.Example {
    // If no SettingName is applied, it defaults to
    // modoptions_[typename without settings]_title
    // The value is then used to look up the UI text in the dialog files.
    // If no dialog text can be found, Everest shows a prettified mod name instead.
    [SettingName("modoptions_examplemodule_title")]
    public class ExampleModuleSettings : EverestModuleSettings { 

        // SettingName also works on props, defaulting to
        // modoptions_[typename without settings]_[propname]

        // Example ON / OFF property with a default value.
        public bool ExampleSwitch { get; set; } = false;

        [SettingIgnore] // Hide from the options menu, but still load / save it.
        public string ExampleHidden { get; set; } = "";

        [SettingRange(0, 10)] // Allow choosing a value from 0 (inclusive) to 10 (inclusive).
        public int ExampleSlider { get; set; } = 5;

        [SettingRange(0, 10)]
        [SettingInGame(false)] // Only show this in the main menu.
        public int ExampleMainMenuSlider { get; set; } = 5;

        [SettingRange(0, 10)]
        [SettingInGame(true)] // Only show this in the in-game menu.
        public int ExampleInGameSlider { get; set; } = 5;

        [YamlIgnore] // Don't load / save it, but show it in the options menu.
        [SettingNeedsRelaunch] // Tell the user to restart for changes to take effect.
        public bool LaunchInDebugMode {
            get {
                return Settings.Instance.LaunchInDebugMode;
            }
            set {
                Settings.Instance.LaunchInDebugMode = value;
            }
        }

        // Example string property. Selecting it will show a file naming-like menu.
        // Max length defaults to 12 if the attribute is not set.
        [SettingMaxLength(40)]
        public string ExampleString { get; set; } = "test";

        public int SomethingWeird { get; set; } = 42;

        // Custom entry creation methods are always called Create[propname]Entry
        // and offer an alternative to overriding CreateModMenuSection in your module class.
        public void CreateSomethingWeirdEntry(TextMenu menu, bool inGame) {
            // Create your own menu entry here.
            // Maybe you want to create a toggle for an int property?
        }

    }
}
```

## Creating custom entities and triggers

To create a custom entity (objects you can place in a map), you have to make it extend `Entity` and annotate it with `[CustomEntity]` so that the game can detect it when it loads a map:
```cs
[CustomEntity("SpringCollab2020/SidewaysJumpThru")]
class SidewaysJumpThru : Entity { ... }
```

Please note that triggers are entities, so using the `[CustomEntity]` annotation works for them too (just extend `Trigger` instead of `Entity`).

You have to define a constructor for the game to be able to build your entity. The allowed signatures for this constructor are:
* `public MyEntity(Level level, LevelData levelData, Vector2 offset, EntityData data)`
* `public MyEntity(EntityData data, Vector2 offset, EntityID id)`
* `public MyEntity(EntityData data, Vector2 offset)`
* `public MyEntity(Vector2 offset)`

To be able to place your entity in Ahorn, you will also have to create a **Ahorn plugin** for it. There are numerous examples of those on the [Spring Collab 2020 repo](https://github.com/EverestAPI/SpringCollab2020/tree/master/Ahorn). The `entities` and `triggers` folders contain the entity/trigger plugins, and the `lang` folder contains the tooltips for the different options. To make the link between the Ahorn plugin and your entity in code, the parts in bold have to match:

Ahorn plugin:
> @mapdef Trigger "**SpringCollab2020/NoRefillField**" NoRefillField(x::Integer, y::Integer, width::Integer=Maple.defaultTriggerWidth, height::Integer=Maple.defaultTriggerHeight)

Code:
> [CustomEntity("**SpringCollab2020/NoRefillField**")]
> class NoRefillField : Trigger { ... }

Other useful attributes for classes are:

### `[Tracked]`

If you annotate your entity with `[Tracked]`, you will be able to search for it by using `Scene.Tracker.GetEntities<MyEntity>()`. Using this method to look up entities of a certain type is more efficient than using, for example, `Scene.Entities.OfType<MyEntity>()`.

This attribute has a parameter, defaulting to false, determining if children classes should be included in the search results as well. This means that if we have a class defined as:
```cs
public class MyChildEntity : MyEntity { ... }
```

`Scene.Tracker.GetEntities<MyEntity>()` will return:
- all MyEntity objects in the scene if MyEntity is annotated with `[Tracked]`
- all MyEntity **and MyChildEntity** objects if MyEntity is annotated with `[Tracked(true)]`

## Executing code when specific events occur

You can use Everest events to execute some actions when an event such as a new level starting, etc. happens.

Here are the events you can listen to:
- Everest.Events.Celeste.OnExiting
- Everest.Events.Celeste.OnShutdown
- Everest.Events.Input.OnInitialize
- Everest.Events.Input.OnDeregister
- Everest.Events.Journal.OnEnter
- Everest.Events.Level.OnComplete
- Everest.Events.Level.OnCreatePauseMenuButtons
- Everest.Events.Level.OnEnter
- Everest.Events.Level.OnExit
- Everest.Events.Level.OnLoadBackdrop
- Everest.Events.Level.OnLoadEntity
- Everest.Events.Level.OnComplete
- Everest.Events.Level.OnPause
- Everest.Events.Level.OnTransitionTo
- Everest.Events.MainMenu.OnCreateButtons
- Everest.Events.OuiJournal.OnCreateButtons
- Everest.Events.Player.OnDie
- Everest.Events.Player.OnSpawn

For example, to call the `onPlayerSpawn` method when the player spawns, use this:
```cs
Everest.Events.Player.OnSpawn += onPlayerSpawn;
```

## Modifying the game's code

Note: `On.Celeste` and `IL.Celeste` come from `MMHOOK_Celeste.dll`, which is auto-generated by [HookGen](https://github.com/MonoMod/MonoMod/tree/master/MonoMod.RuntimeDetour.HookGen) when Everest is installed. **You need to install Everest on the OpenGL / FNA version of the game to auto-generate a working .dll**, otherwise you'll need the Windows-only and obsolete XNA Framework to even compile your mod.

If you want to modify the game's behaviour, you can check the game's code with [ILSpy](https://github.com/icsharpcode/ILSpy/releases) or [dnSpy](https://github.com/0xd4d/dnSpy/releases). ILSpy gives better decompiled code, and dnSpy provides a debugger.

Once you found the method you want to modify, you can use `On.Celeste` or `IL.Celeste` to do this.

### `On.Celeste` hooks

Those hooks allow to "replace" a method in vanilla with your own method. You can call the original method when/if you want, by using the `orig` parameter passed to the hook.

For example, [Extended Variants](https://github.com/max4805/Everest-ExtendedVariants) use the following to make the game think wall-jumping is always impossible:
```cs
public void Load() {
    On.Celeste.Player.modWallJumpCheck += modPlayerWallJumpCheck;
}

public void Unload() {
    On.Celeste.Player.modWallJumpCheck -= modPlayerWallJumpCheck;
}

private bool modWallJumpCheck(On.Celeste.Player.orig_WallJumpCheck orig, Player self, int dir) {
    if(Settings.DisableWallJumping) {
        // instead of running the vanilla method, return false all the time.
        return false;
    }

    // call the vanilla method by calling the "orig" method.
    return orig(self, dir);
}
```

When `Settings.DisableWallJumping` is true, the vanilla code for `Player.WallJumpCheck()` won't run, and the method will instead always return `false`. Otherwise, the method will behave like vanilla.

### `IL.Celeste` hooks

Those hooks allow modifying the _contents_ of a method. Those are useful when you want to inject or modify code at a specific point in a big method, and don't want to copy-paste the entirety of it in your mod.

**TODO**