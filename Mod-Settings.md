To save settings associated with your mod, you can make use of the `EverestModuleSettings` class, which will automatically generate options that can be found in the ModOptions menu.

First create a class that extends `EverestModuleSettings` and add the following to your **`EverestModule`** class.
```csharp
public override Type SettingsType => typeof(ExampleModuleSettings);
public static ExampleModuleSettings Settings => (ExampleModuleSettings) Instance._Settings;
```

Now add any number of [**Properties**](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties) to your Settings class. Options will be generated based on the property [type](#property-types) and [attributes](#attributes).  

Settings will be saved to and loaded from `Saves/modsettings-[modname].celeste`.

## Property Reference
- [**Property Types**](#property-types)
  - [**Boolean**](#Boolean)
  - [**Integer**](#Integer)
  - [**Enum**](#Enum)
  - [**String**](#String)
  - [**ButtonBinding**](#ButtonBinding)
- [**Attributes**](#attributes)
  - [**SettingName**](#SettingName)
  - [**SettingSubText**](#SettingSubText)
  - [**SettingNeedsRelauch**](#SettingNeedsRelauch)
  - [**SettingRange**](#SettingRange)
  - [**SettingNumberInput**](#SettingNumberInput)
  - [**SettingMaxLength**](#SettingMaxLength)
  - [**DefaultButtonBinding**](#DefaultButtonBinding)
  - [**SettingInGame**](#SettingInGame)
  - [**SettingIgnore**](#SettingIgnore)
  - [**YamlIgnore**](#YamlIgnore)
- [**Custom Entries**](#custom-entries)
  - [**Making a custom entry for a property**](#making-a-custom-entry-for-a-property)
  - [**Creating a Mod Options submenu**](#creating-a-mod-options-submenu)
  - [**Making a custom Mod Options section**](#making-a-custom-mod-options-section)

# Property Types
ModSettings options are automatically generated based on the type of each property in your EverestModuleSettings class.

## Boolean
```csharp
bool => TextMenu.OnOff 
``` 
Using a `boolean` property will generate a TextMenu.OnOff item, which can be toggled using left/right or confirm.

## Integer
```csharp
[SettingRange(int min, int max)]  
int => TextMenu.Slider  
[SettingRange(int min, int max, bool largeRange)]  
int => TextMenuExt.IntSlider 
``` 
Using an `int` property with the [SettingRange](#SettingRange) attribute will generate a TextMenu.Slider item, which can go from `min` to `max` using left/right.  
Setting `largeRange` to `true` will generate a TextMenuExt.IntSlider, which is optimized for larger ranges (upwards of 50 values).

## Enum
```csharp
Enum => TextMenu.Slider  
```
Using an `Enum` type property will generate a TextMenu.Slider item using the values of the enum type, ordered by an integer cast.

## String
```csharp
string => TextMenu.Button => OuiTextEntry
```
Using a string property will generate a TextMenu.Button which, when pressed, will open up a text entry screen similar to File Naming.  
The [SettingMaxLength](#SettingMaxLength) attribute can be used to set the maximum possible length of the string (defaults to 12 characters).  

⚠️ _This property will not display on the in-game pause menu._

## ButtonBinding
```csharp
ButtonBinding => TextMenu.Button => ModuleSettingsButtonConfigUI/ModuleSettingsKeyboardConfigUI
```
Using a ButtonBinding property will generate two TextMenu.Buttons which will open up a ButtonConfigUI and KeyboardConfigUI, respectively.
The [DefaultButtonBinding](#DefaultButtonBinding) attribute can be used to set the default bindings.  

Once added, the ButtonBinding property can then be used similarly to any `Input`.  
For example:
```csharp
public override void Update(){
   if (Settings.CustomButtonBinding.Pressed)
      // Do something
}
```


# Attributes

## SettingName
```csharp
[SettingName(string name)]  
```
Adding the `SettingName` attribute to a property will set the name of the option to the dialog id assiociated with `name`.  
If `SettingName` is not added, or the dialog id does not exist, the name of the option will be the property name with spaces before capital letters.

## SettingSubText
```csharp
[SettingSubText(string description)]  
```
Adding the `SettingSubText` attribute to a property will add a description that will show when the option is selected.  
If `description` is a dialog id, the associated dialog will be displayed.

## SettingNeedsRelauch
```csharp
[SettingNeedsRelaunch]
```
Adding the `SettingNeedsRelauch` attribute to a property will show a warning that a relaunch is required for changes to take effect.

## SettingRange
```csharp
[SettingRange(int min, int max)]  
[SettingRange(int min, int max, bool largeRange)]  
```
Adding the `SettingRange` attribute to an [Integer](#Integer) property will allow that property to be displayed as a slider.  
The range of the slider is set using `min` and `max` (inclusive).  
If `largeRange` is true, the option will be a TextMenuExt.IntSlider, which is functionally the same, but better suited for larger ranges (upwards of 50 values).

## SettingNumberInput
```csharp
[SettingNumberInput(bool allowNegatives, int maxLength)]
```
Adding the `SettingNumberInput` attribute to an [Integer](#Integer) or Float property will create a button to open a number entry screen.  
`maxLength` (default 12) sets the number of digits allowed.

## SettingMaxLength
```csharp
[SettingMaxLength(int max)]
```
Adding the `SettingMaxLength` attribute to a [String](#String) property will set the maximum possible length of the string to `max` (defaults to 12 characters).  

## DefaultButtonBinding
```csharp
[DefaultButtonBinding(Buttons button, Keys key)]
```
Adding the `DefaultButtonBinding` attribute to a [ButtonBinding](#ButtonBinding) property will set the default button and key associated with the setting to the supplied values. 
The `ForceDefaultButton` and `ForceDefaultKey` properties can be set in order to ensure that the specified input is always bound.

ℹ️ The `Buttons` and `Keys` Enumeration types come from the `Microsoft.Xna.Framework.Input` namespace.

## SettingInGame
```csharp
[SettingInGame(bool inGame)]
```
Adding the `SettingInGame` attribute to a property will set whether the option is displayed in the in-game pause menu

## SettingIgnore
```csharp
[SettingIgnore]
```
Adding the `SettingIgnore` attribute to a property will prevent the option from being displayed in the ModOptions menu.

## YamlIgnore
```csharp
[YamlIgnore]
```
Adding the `YamlIgnore` attribute to a property will prevent the setting from being saved into the modsettings file.

ℹ️ This attribute comes from the `YamlDotNet.Serialization` namespace.

# Custom Entries

## Making a custom entry for a property

If your setting does not fit any case above and you need to write your own code to make it appear in Mod Options, you can do so by implementing a method called `Create{PropertyName}Entry`:

```cs
public void CreateSomethingEntry(TextMenu menu, bool inGame)
```

This method will be called by Everest when the option should be added to the menu. It should add an option to the given `menu`. `inGame` will be `true` if the player accessed mod options from the pause menu, or `false` if they accessed it from the main menu.

For example:

```cs
public int ToggleBetween40And50 { get; set; } = 40;

public void CreateToggleBetween40And50Entry(TextMenu menu, bool inGame) {
    menu.Add(new TextMenu.OnOff("Should Be 50", ToggleBetween40And50 == 50)
        .Change(enabled => ToggleBetween40And50 = (enabled ? 50 : 40)));
}
```

This code creates an on/off switch for an integer option. If the switch is off, `ToggleBetween40And50` is set to 40, and if the switch is on, `ToggleBetween40And50` is set to 50.

## Creating a Mod Options submenu

You can create a Mod Options submenu by creating a class like this:
```cs
using Celeste.Mod.UI;

namespace Celeste.Mod.Example {
    class OuiExampleSubmenu : OuiGenericMenu, OuiModOptions.ISubmenu {
        public override string MenuName => "SUBMENU EXAMPLE";

        protected override void addOptionsToMenu(TextMenu menu) {
            menu.Add(new TextMenu.OnOff("Some toggle", false)
                .Change(newValue => Logger.Log("OuiExampleSubmenu", $"The value changed to {newValue}")));
        }
    }
}
```

This will create a menu looking like this:

![Submenu screenshot](https://cdn.discordapp.com/attachments/445236692136230943/701768339126747216/unknown.png)

After that, you have to create a button in Mod Options to access this screen. You can do so by adding this to your settings class:

```cs
[YamlIgnore]
public int SubmenuExample { get; set; } = 0;

public void CreateSubmenuExampleEntry(TextMenu menu, bool inGame) {
    if (!inGame) {
        menu.Add(new TextMenu.Button("Submenu Example")
            .Pressed(() => OuiGenericMenu.Goto<OuiExampleSubmenu>(overworld => overworld.Goto<OuiModOptions>(), new object[0])));
    }
}
```

The first parameter of `OuiGenericMenu.Goto` is a delegate called to go back to the parent menu (in this case, Mod Options). The second parameter is an arbitrary parameter array you'll be able to access from your submenu with the `parameters` local variable.

⚠️ This doesn't work for in-game submenus (hence the `!inGame` check in the example code). If you need an in-game submenu, ask max480#4596 on Discord, Extended Variants has those.

## Making a custom Mod Options section

If the above is not enough for your needs, you can decide to build the whole Mod Options section for your mod by yourself. To do that, override the `CreateModMenuSection` method in your EverestModule class (**not** your settings class):

```cs
public override void CreateModMenuSection(TextMenu menu, bool inGame, EventInstance snapshot) {
    // your own section creation logic
}
```

⚠️ _Since, by doing that, you are handling menu creation by yourself, all `Setting*` attributes will stop working._