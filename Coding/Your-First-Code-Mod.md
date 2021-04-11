## Table of Contents

* [Project setup](#project-setup)
* [Module class](#module-class)
* [Mod settings, session and save data](#mod-settings-session-and-save-data)
* [Executing code when specific events occur](#executing-code-when-specific-events-occur)
* [Modifying the game's code](#modifying-the-games-code)
  * [On.Celeste hooks](#onceleste-hooks)
  * [IL.Celeste hooks](#ilceleste-hooks)
  * [Hooking coroutines](#hooking-coroutines)
* [Accessing private fields or methods](#accessing-private-fields-or-methods)
  * [Private fields / properties](#private-fields--properties)
  * [Private methods](#private-methods)


## Project setup

----

<div>
<h5>PREREQUISITES</h5>
<p>

- Everest: [Website](https://everestapi.github.io/)
- Visual Studio 2015 or newer. You need to have the .NET Framework 4.5.2 targeting pack installed. You can use [this vsconfig file](https://cdn.discordapp.com/attachments/445236692136230943/698269484653215844/celeste.vsconfig) and import it in Visual Studio Installer (More > Import configuration) to install the requirements.

MonoDevelop instructions are different.

</p>
</div>

----

Every Everest code mod starts out as a C# (.NET Framework) class library targeting the .NET Framework 4.5.2 (same as Celeste itself).

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

For more info about the mod structure, the `everest.yaml` format, how to add extra content and on how to zip up your mod, [read the mod structure page](Mod-Structure).

</p>
</div>

----

- Right-click your project's "References" and select "Add Reference...", then "Browse..." into your Celeste installation directory and setup your references like on the following screenshot (add the relevant references and remove extra ones that got added automatically):

![2-refs](https://user-images.githubusercontent.com/1200380/55094153-1bab6c80-50b6-11e9-8135-2d484d589ab4.png)

You'll find most of those references as dlls in your Celeste installation directory. "Celeste" is Celeste.exe itself.

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

For your mod to load, you **have** to create a class extending `EverestModule` in your project. (You can leave `Load()` and `Unload()` methods empty if you don't need them though.)

Your module class should look similar to the example.

----

<div>
<h5>NOTE</h5>
<p>

This example only shows a subset of Everest's capabilities.  
[**See `ExampleMod/ExampleModule` for more of what Everest can do.**](https://github.com/EverestAPI/ExampleMod/blob/master/ExampleModule.cs)

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
        public static ExampleModuleSettings Settings => (ExampleModuleSettings) Instance._Settings;

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
        public override void LoadContent(bool firstLoad) {
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
[**See `ExampleMod/ExampleModuleSettings` for more of what Everest can do.**](https://github.com/EverestAPI/ExampleMod/blob/master/ExampleModuleSettings.cs)

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

## Executing code when specific events occur

You can use Everest events to execute some actions when an event such as a new level starting, etc. happens. You'll find a full list of Everest events in [this page](Everest-Events).

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
    On.Celeste.Player.WallJumpCheck += modPlayerWallJumpCheck;
}

public void Unload() {
    On.Celeste.Player.WallJumpCheck -= modPlayerWallJumpCheck;
}

private bool modPlayerWallJumpCheck(On.Celeste.Player.orig_WallJumpCheck orig, Player self, int dir) {
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

When you add an IL hook to a method, the hook is immediately called with an `ILContext` object. For example:
```cs
IL.Celeste.Player.DashBegin += modDashLength;

private void modDashLength(ILContext il) { ... }
```

This object allows you to modify the _IL code_ for the method directly, and the way you want. CIL stands for [Common Intermediate Language](https://en.wikipedia.org/wiki/Common_Intermediate_Language), and is a lower-level language. For instance, this code:
```cs
if (SaveData.Instance.Assists.SuperDashing) {
    dashAttackTimer += 0.15f;
}
```
translates to:
```
IL_009f: ldsfld class Celeste.SaveData Celeste.SaveData::Instance   <= load SaveData.Instance
IL_00a4: ldflda valuetype Celeste.Assists Celeste.SaveData::Assists <= load the Assists field in it
IL_00a9: ldfld bool Celeste.Assists::SuperDashing                   <= load the SuperDashing field in it
IL_00ae: brfalse.s IL_00c2                              <= if this is false, jump over the contents of the if

IL_00b0: ldarg.0                                        <= load "this"
IL_00b1: ldarg.0                                        <= load "this" again
IL_00b2: ldfld float32 Celeste.Player::dashAttackTimer  <= load the dashAttackTimer in this
IL_00b7: ldc.r4 0.15                                    <= load 0.15 to the stack
IL_00bc: add                                    <= this adds the 2 latest loaded things, so dashAttackTimer + 0.15
IL_00bd: stfld float32 Celeste.Player::dashAttackTimer  <= save the result to dashAttackTimer

IL_00c2: [...]
```

[You can find a list of all existing instructions here.](https://en.wikipedia.org/wiki/List_of_CIL_instructions)  
A reference for what Operand type corresponds to each OpCode can be downloaded [here](https://github.com/EverestAPI/Resources/files/4774310/MonoCecilOpCodes.txt),
as described [here](https://stackoverflow.com/a/7215711)

In ILSpy and dnSpy, you can view the IL code by using this combo box on the top-left:
![ILSpy screenshot for the combobox allowing to switch between IL and C#](https://user-images.githubusercontent.com/52103563/75152044-6b504900-5708-11ea-8f00-b42d02946a39.png)

In dnSpy, you can also right-click a line of code to view its IL equivalent.

IL hooks allow you to add, remove or modify those IL instructions. For example:

```cs
private void modDashLength(ILContext il) {
    ILCursor cursor = new ILCursor(il);

    // jump where 0.3 or 0.15f are loaded (those are dash times)
    while (cursor.TryGotoNext(MoveType.After, instr => instr.MatchLdcR4(0.3f) || instr.MatchLdcR4(0.15f))) {
        Logger.Log("ExtendedVariantMode/DashLength", $"Applying dash length to constant at {cursor.Index} in CIL code for {cursor.Method.FullName}");

        cursor.EmitDelegate<Func<float>>(determineDashLengthFactor);
        cursor.Emit(OpCodes.Mul);
    }
}

private static float determineDashLengthFactor() {
    return Settings.DashLength / 10f;
}
```

This code looks up for every `ldc.r4 0.3` or `ldc.r4 0.15` in the code (that is, each time 0.3f and 0.15f are used), and multiply them with the value returned by `determineDashLengthFactor()`.

Here is a what the IL code looks like before patching:
```
dashAttackTimer = 0.3f;
=>
ldarg.0
ldc.r4 0.3
stfld float32 Celeste.Player::dashAttackTimer
```
and here is a simplified view of what the code looks like after patching:
```
ldarg.0
ldc.r4 0.3
call float32 determineDashLengthFactor()
mul                               <= multiplies 0.3 and the result from determineDashLengthFactor()
stfld float32 Celeste.Player::dashAttackTimer
=>
dashAttackTimer = 0.3f * determineDashLengthFactor();
```
The dash attack timer (determining dash length) is now multiplied with an arbitrary factor, pulled from mod settings.

[Extended Variants](https://github.com/max4805/Everest-ExtendedVariants/tree/master/ExtendedVariantMode/Variants) rely a lot on IL hooks, to slightly alter game mechanics (like gravity and maximum fall speed, for example), so it has a lot of examples of these.

**Please note that IL code is slightly different between the XNA and FNA versions, at least on Steam**. Testing IL hooks against both versions is highly recommended.

### Hooking coroutines

Coroutines are methods returning `IEnumerator` and containing `yield return xxx` in them. Their name usually ends with "Routine".

- When `yield return [number]` is called, the coroutine pauses for this amount of time (in seconds).
- When `yield return null` is called, the coroutine pauses for one frame.

Hooking them behaves particularly:

#### On.* Hooks

In order to run the vanilla coroutine in your hook, you need to use `yield return orig(self)`:

```cs
private static IEnumerator onFileSelectLeave(On.Celeste.OuiFileSelect.orig_Leave orig, OuiFileSelect self, Oui next) {
    yield return orig(self, next);

    Logger.Log("TestMod", "I left file select!");
}
```

ℹ️ _To be able to use `yield return orig(self)`, you need to depend on Everest 2563 or later in your everest.yaml._

#### IL.* hooks

The actual code of the coroutine is not in the method itself. For example, the IL code for `Player.DashCoroutine()` is:
```
IL_0000: ldc.i4.0
IL_0001: newobj instance void Celeste.Player/'<DashCoroutine>d__423'::.ctor(int32)
IL_0006: dup
IL_0007: ldarg.0
IL_0008: stfld class Celeste.Player Celeste.Player/'<DashCoroutine>d__423'::'<>4__this'
IL_000d: ret
```

⬆️ This is not the actual code for the method, this only instantiates a `Celeste.Player/'<DashCoroutine>d__423'` object and returns it. This is what `IL.Celeste.Player.DashCoroutine += ...` will hook, so using that will lead to unexpected results.

The code you see in the C# view in ILSpy is actually located in `Celeste.Player/'<DashCoroutine>d__423'::MoveNext()`, so if you want to IL hook it, this is the method you want to hook.

You can do so by building an IL hook manually:
```cs
ILHook dashCoroutineHook = new ILHook(
    typeof(Player).GetMethod("DashCoroutine", BindingFlags.NonPublic | BindingFlags.Instance).GetStateMachineTarget(),
    modDashSpeed);
```
`GetStateMachineTarget()` is what allows to turn `Celeste.Player::DashCoroutine()` into `Celeste.Player/'<DashCoroutine>d__423'::MoveNext()`.

To undo this IL hook, you can do:
```
dashCoroutineHook.Dispose();
```

Note that building an IL hook manually is also useful to hook orig_* methods and other methods that are not made available through `IL.Celeste.*`.

## Accessing private fields or methods

### Private fields / properties

In order to access a private field or property in a class, you can use [DynData](https://github.com/MonoMod/MonoMod/blob/master/MonoMod.Utils/DynData.cs). For that, build a DynData object, passing it the object you want the access the fields of:
```cs
DynData<StrawberrySeed> strawberrySeedData = new DynData<StrawberrySeed>(someStrawberrySeedObject);
```
You can also omit the `someStrawberrySeedObject` parameter if you want to access a static field/property.

After doing that, you can access and set the fields you want on `someStrawberrySeedObject` by doing this:
```cs
Sprite vanillaSprite = strawberrySeedData.Get<Sprite>("sprite"); // gets someStrawberrySeedObject.sprite
strawberrySeedData["sprite"] = modSprite;    // changes someStrawberrySeedObject.sprite
selfStrawberrySeed.Set("sprite", modSprite); // same
```

DynData can also be used to **"attach" data to any object**. This is done by simply writing to a field that doesn't actually exist in the object (`strawberrySeedData["nonExistentField"] = 42`). You can then get this field back with `strawberrySeedData.Get<int>("nonExistentField")`. This can be used, for example, to save some data in a hook on an entity, and get it back later when the hook is executed again / in another hook.

### Private methods

In order to call a private method, you'll have to get a reference to it (this is referred to as "reflection"):
```cs
private static MethodInfo strawberryOnDash = typeof(Strawberry).GetMethod("OnDash", BindingFlags.Instance | BindingFlags.NonPublic);
```
The "Instance" flag means the method is not static, and should be replaced with "Static" if this is not the case.

**For performance, it is recommended to get the `MethodInfo` once, and reuse it each time it is required**. Putting it as a static field in a class is a way to do this.

To invoke the method, use:
```cs
strawberryOnDash.Invoke(this, new object[] { dir });
```

This is equivalent to calling `this.OnDash(dir)`.