The TextMenu is a UI element that displays a scrolling list of items on the screen.
Examples in Celeste can be found on the Options screen, Pause screen, and more.

## Reference
- [**TextMenu (Celeste)**](#textmenu)
   - [**Item**](#item)
      - [**Button**](#button)
      - [**Header**](#header)
      - [**SubHeader**](#subheader)
      - [**Option\<T\>**](#optiont)
         - [**OnOff**](#onoff)
         - [**Slider**](#slider)
- [**TextMenuExt (Everest)**](#textmenuext)
   - [**ButtonExt**](#buttonext)
   - [**SubHeaderExt**](#subheaderext)
   - [**EaseSubHeaderExt**](#easesubheaderext)
   - [**HeaderImage**](#headerimage)
   - [**IntSlider**](#intslider)
   - [**SubMenu**](#submenu)
   - [**OptionSubMenu**](#optionsubmenu)

# TextMenu
`TextMenu` is the class that defines the container for all items, as well as holding all the vanilla item classes.  
Items can be added to a menu using `Add(TextMenu.Item item)`, or inserted and removed using the respective methods.  

If `TextMenu.AutoScroll` is enabled (on by default), the items in the textmenu will automatically move to keep the selected item on screen.  
Changing `TextMenu.InnerContent` will set whether items are displayed centered or aligned to the left.
Note that [some items](#optiont) will set InnerContent to Two Columns (aligned left) because they make use of both columns.

To change the selection of the textmenu in code, `TextMenu.Selection` can be set
to the index of the desired item (which can be retrieved using `IndexOf(TextMenu.Item item)`).  
If the menu contains at least one selectable item, `FirstSelection()` will set the selection to the first one.

## Item
`TextMenu.Item` is an abstract parent class for all TextMenu items.  
It exposes some methods to add Actions that are executed when an event happens.

ex:
```csharp
item.Enter(
   ()=> Logger.Log("ItemTest", "Item is the current selection")
);
item.Leave(
   ()=>Logger.Log("ItemTest", "Item is no longer the current selection")
);
item.Pressed(
   ()=>Logger.Log("ItemTest", "MenuConfirm pressed on item")
);
item.AltPressed(
   ()=>Logger.Log("ItemTest", "MenuJournal pressed on item")
);
```
These methods can be chained for ease of use.  

Although it does not extend the Entity class, it makes use of similar methods such as `Render` and `Update`.

## Button
A labelled button that can execute an action when pressed.
```csharp
menu.Add(new TextMenu.Button("ButtonLabel").Pressed(()=>Logger.Log("BtnText", "Button was pressed")));
```

## Header
A large text header.
```csharp
menu.Add(new TextMenu.Header("Title"));
```
## SubHeader
A small text subheader.
```csharp
menu.Add(new TextMenu.SubHeader("SubTitle"));
```

## Option\<T\>
A generic class for creating a multi-option selector where `<T>` is the type of the the underlying value.  
`Option.Add(string label, T value, bool selected = false)` can be used to add values to the selector, 
where `label` is the option that is displayed, `value` is the underlying value, and `selected` determines whether this option should start selected.

`Option.Change(Action<T> action)` can be used to set the action that is executed when the selected value is changed.

### OnOff
A subclass of `Option<bool>` for an On/Off selector.
### Slider
A subclass of `Option<int>` for a range selector, takes a function of int to string for its values, along with a min and max value. 


# TextMenuExt
A static class that contains any items and extensions added by Everest.

## ButtonExt
A more configurable [Button](#button), with an optional icon.
```csharp
menu.Add(new TextMenuExt.Button("Label", "icon/path/here"));
```

## SubHeaderExt
A more configurable [SubHeader](#subheader), with an optional icon.
## EaseInSubHeaderExt
A SubHeader that can be "eased" in and out of view by toggling `FadeVisible`.

## HeaderImage
A large image.

## IntSlider
A Range selector for integer values only, but able to handle much larger ranges.  
⚠️ _This class extends [TextMenu.Item](#item) **not** [TextMenu.Option\<T\>](#optiont)_

## SubMenu
Creates an expandable submenu that contains other TextMenu.Items.  
Setting `enterOnSelect` to true will cause the menu to automatically expand when it is selected.
```csharp
new TextMenuExt.SubMenu(string label, bool enterOnSelect);
```

It includes methods to add, insert, and remove items from the submenu:
```csharp
//Create an item
TextMenu.Button button = new TextMenu.Button("Press Me!");
//Append the item to the end of the submenu
submenu.Add(button);
//Remove the item from the submenu
submenu.Remove(button);
//Insert the item to the beginning of the submenu
submenu.Insert(0, button);
```

Which can be chained for ease of use:
```csharp
menu.Add(new TextMenuExt.SubMenu("SubMenu", false).Add(
      new TextMenu.Button("Press Me!")
   ).Add(
      new TextMenu.OnOff("OnOffItem", true)
   ).Add(
      new TextMenuExt.IntSlider("These are cool too!", 0, 1)
   )
);
```


## OptionSubMenu
Creates a list of Submenus that can be swapped between similarly to a Slider.
```csharp
new TextMenuExt.OptionSubMenu(string label);
```

Submenus can be added by supplying a label, and a list of items
```csharp
//Create a list of items
List<TextMenu.Item> items{
   new TextMenu.Button("Button"),
   new TextMenu.OnOff("OnOff")
}
submenu.Add("Menu1", items);
```

Which can be chained for ease of use:
```csharp
menu.Add(new TextMenuExt.OptionSubMenu("OptionSubMenu").Add(
      "Option0", null
   ).Add(
      "Option1", new List<TextMenu.Item>
      {
         new TextMenu.Button("Menu1Item0")
      }
   ).Add(
      "Option2", new List<TextMenu.Item>
      {
         new TextMenu.Button("Menu2Item0"),
         new TextMenu.OnOff("Menu2Item1", true)
      }
   ).Add(
      "Option3", new List<TextMenu.Item>
      {
         new TextMenu.Button("Menu3Item0"),
         new TextMenu.OnOff("Menu3Item1", true),
         new TextMenuExt.IntSlider("Menu3Item2", 0, 1),
      }
   )
);
```

⚠️ _This class extends [TextMenu.Item](#item) **not** [TextMenuExt.SubMenu](#submenu)_