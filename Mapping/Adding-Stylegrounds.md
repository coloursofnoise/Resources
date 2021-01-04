# What are Stylegrounds?

**Stylegrounds** are backgrounds and effects you can add to your map. 
This tutorial explains the _entire_ Stylegrounds menu and how you are able to add your own backgrounds to your mod.

Jump to the [Effects Reference](#effects-reference)

# The Stylegrounds menu

The Stylegrounds menu is divided into two sections, **Parallax** and **Effect**.

## Parallax

The **Parallax** section may seem complicated at first, but it's actually quite easy to use and get used to.
Below is an image of what it looks like, followed by explanations of each of the parameters in order.
![Parallax Window](https://user-images.githubusercontent.com/64371989/80315026-5c177580-87f5-11ea-96fa-82edf32c95d8.png)

### Texture

In this parameter, you pick the actual image file that the parallax will use. Typically, you should only use background textures from the vanilla game (bgs/[number]) or ones you've inserted into your own mod (more on that below), as using backgrounds from other mods will add unnecessary dependencies. There also four other backgrounds that you can freely use at the bottom of the list: _purplesunset_, _darkswamp_, _mist_ and _northernlights_.

### Only

This and the following parameter are where you pick the rooms your background will appear in. The internal room names that appear on the left in the main Ahorn window should be used, separated by commas but _not_ spaces if you want multiple (for example, "a1,b1,b2"). The * can be used as a character stand-in, allowing you to include multiple rooms at once (for example, "a-*" will count every room that begins with "a-").

### Exclude

This follows the same format as the Only parameter, but it force-excludes rooms rather than including them. Anything placed in this parameter will have priority over commands from the Only parameter.

### Tag

This is a pretty important section if you wish to code. More about it in the Effect section of this tutorial.

### Flag & Not Flag

If you use the Flag trigger, you can make this background appear using that trigger instead of it just appearing. You can put literally anything you ant in there, but it's very important to make it unique, so to do that, you can just add your username in the flag name. **Leave this section empty if you don't plan on using Flag triggers.**

You can use the Flag trigger and the flag you set in the Not Flag section to make the background disappear.
**Leave this section empty if you don't plan on using Flag triggers.**

### Blend Mode

This decides in what way your background will blend with the other effects and backgrounds. **additive** will add the colors of the image to any images below it, which is typically unwanted unless there is nothing but black below the image. **alphablend** will instead attempt to blend the layer colors together, which is more useful for adding transparency.

### Colour

Here you pick what color to tint your background image, in hexadecimal. Typically you won't want to change this from FFFFFF, as lower values will subtract color from the image.

### X & Y

These parameters determine the starting position of the background image. X is horizontal, Y is vertical, positive values translate the image right/down, and negative values translate the image left/up.

### Scroll X & Y

These parameters define the multiplier at which your background image scrolls relative to the screen. 0 locks it in place, and 1 causes it to scroll at the same rate as the gameplay layer, so you'll likely want something in between.

### Speed X & Y

These parameters set the speed at which the background image will scroll _on its own_, in pixels per second. Again, positive values mean the image will scroll right/down, and negative values make it scroll left/up.

### Alpha

How transparent the image is, with 1 being opaque, and 0 completely invisible. Unless you want a translucent background image, set this to 1.

### Fade In Checkbox

If ticked, the background will go from being transparent to the Alpha you set when you enter or leave the room it's in.

### Flip X & Y Checkboxes

If ticked, these will flip the background image horizontally and vertically, respectively.

### Foreground Checkbox

If ticked, your image will appear in front of the gameplay layer. For background images, this should obviously be unticked, but it can be used for effects like mist in either the foreground or background. If you tick this, be sure to set the alpha value low so the gameplay is visible!

### Instant In and Out Checkboxes

If Instant In is ticked, the background will be loaded during the transition between two rooms.
If Instant Out is ticked, the background will disappear during the transition between two rooms.

### Loop X & Y

If Loop X is ticked, the background will loop horizontally.
If Loop Y is ticked, the background will loop vertically.

## Effect

The **Effect** section is pretty small and very easy to learn. Below is an image of what it looks like, followed by explanations of each of the parameters in order.![Effect Window](https://user-images.githubusercontent.com/64371989/80316399-dba94280-87fd-11ea-9b8d-66ba9a42e55d.png)

### Name

The effect you want to add.

### Rooms, Exclude, Flag, Not Flag and Foreground Checkbox

These are identical to the parameters of the same names in the Parallax tab.

### Tag

Same as the Tag section in the Parallax tab.
If you pick the black hole effect and put **blackhole** in the Tag section, the black hole will appear in the background whenever the player touches a Moon Glitch Background Trigger.

# How to insert custom backgrounds

Let's say your custom background is called **mybackground.png**.

To add your custom background, you must first have a proper mod structure, you can find the tutorial for that [here](Mod-Structure).

The file structure should look like this:

Mods > yourmod > Graphics > Atlases > Gameplay > bgs > uniquefoldername > mybackground.png

If you add a new background image, it will appear in the list in Ahorn immediately. If you make an update to the image, however, it won't appear in the window until you restart Ahorn.

# Effects Reference
:information_source: Some effects take up the entire screen, effectively neutralizing any stylegrounds behind them. To put a styleground in front of an effect, set the styleground to foreground, update, then set it back to background.  
:information_source: Several settings may reset to default values on pressing add, and should be set after adding the effect

### Blackhole: 
The black hole in farewell.  
Use with the `blackhole strength trigger` to achieve the pink black hole with more particles used in Reconciliation.  
Shows wind but should not be the only indicator of wind.  
Takes up the whole screen.

### BossStarfield: 
The background for the badeline bossfight in Reflection.  
Particles move horizontally across the screen if the room's width is less than or equal to its height; otherwise, the particles move primarily vertically.  
Takes up the whole screen.

### CoreStarsFG: 
White particles from the screen wrap bit at the end of Core.

### Godrays: 
Red diamonds move down the screen.  
Used in Reflection.

### Heatwave: 
Provides dynamic particle and mist effects for both the `hot` and `cold` modes in Core.  
The core mode metadata setting must be something other than `none` for this to show.

### MirrorFG: 
A red particle effect used in the Mirror Temple's mirror section.

### NorthernLights: 
The aurora borealis seen in the very beginning of Reflection.  
Takes up the whole screen.

### DreamStars: 
Green squares rise from the bottom of the screen.  
Unused ingame.

### Petals: 
Pink petals at the end of Reflection.

### Planets: 
The pink and green starfish in the background during the first few checkpoints of Farewell. The amount field starts out waaay too high for most rooms, resulting in overlapping starfish; Lower this down to at most single digits for most rooms.  
:information_source: The size field shows only the options big or small; however, this can be replaced with any set of numbered stylegrounds from the root bgs/10. this means you can set size to things like blackhole/particles for the  long pink particles from the blackhole effect, or planets/small/planets/big for actual planets (unused ingame).  
:information_source: if this effect is just above a styleground with blend mode set to additive, this effect will also be set to have additive blend mode.

### Rain: 
The rain at the start of Farewell.

### ReflectionFG: 
Exactly the same as [MirrorFG](#mirrorfg) but a pinkish red color.

### SnowFG: 
White/blue particles fly across the screen.  
Used in Forsaken City and Celestial Resort along with [SnowBG](#snowbg).

### SnowBG: 
Same as above, but using darker blue colors.

### Stardust: 
Pink & green particles in farewell, move with the wind.

### Starfield: 
The moving ribbon of stars used in the first part of farewell.

### Stars: 
Star background in Old Site.  
If the `dreaming` tag in map metadata is set to true, the stars will fall down the screen as in the majority of Old Site. Otherwise, the stars will be stationary as in the Awake checkpoint.  
Takes up the whole screen.

### Tentacles: 
Tentacles like those in Reflection.  
Setting the side field to down or up will crash the game. This may be useful for emulating something like last screen of the Badeline bossfight in Reflection, where the tentacles move smoothly.  
This effect is not used ingame - the entity is used instead.

### Windsnow: 
Used to indicate wind in Golden Ridge.