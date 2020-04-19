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
- [**Attributes**](#attributes)
  - [**SettingName**](#SettingName)
  - [**SettingSubText**](#SettingSubText)
  - [**SettingNeedsRelauch**](#SettingNeedsRelauch)
  - [**SettingRange**](#SettingRange)
  - [**SettingMaxLength**](#SettingMaxLength)
  - [**SettingInGame**](#SettingInGame)
  - [**SettingIgnore**](#SettingIgnore)
  - [**YamlIgnore**](#YamlIgnore)
- [**Custom Entries**](#custom-entries)

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
string => TextMenu.Button  
```
Using a string property will generate a TextMenu.Button which, when pressed, will open up a text entry screen similar to File Naming.  
The [SettingMaxLength](#SettingMaxLength) attribute can be used to set the maximum possible length of the string (defaults to 12 characters).  

!This property will not display on the in-game pause menu.


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
Adding the `SettingRange` attribute to an [**Integer**](#Integer) property will allow that property to be displayed as a slider.  
The range of the slider is set using `min` and `max` (inclusive).  
If `largeRange` is true, the option will be a TextMenuExt.IntSlider, which is functionally the same, but better suited for larger ranges (upwards of 50 values).

## SettingMaxLength
```csharp
[SettingMaxLength(int max)]
```
Adding the `SettingMaxLength` attribute to a [**String**](#String) property will set the maximum possible length of the string to `max` (defaults to 12 characters).  

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
[YamlDotNet.Serialization.YamlIgnore]
```
Adding the `YamlIgnore` attribute to a property will prevent the setting from being saved into the modsettings file.

# Custom Entries
TODO: Add Create{PropertyName}Entry Guide