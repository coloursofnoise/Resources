# What are Stylegrounds?

**Stylegrounds** are backgrounds and effects you can add to your map. 
This tutorial explains the _entire_ Stylegrounds menu and how you are able to add your own backgrounds to your mod.

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

To add your custom background, you must first have a proper mod structure, you can find the tutorial for that [here](https://github.com/EverestAPI/Resources/wiki/Mod-Structure).

The file structure should look like this:

Mods > yourmod > Graphics > Atlases > Gameplay > bgs > uniquefoldername > mybackground.png

If you add a new background image, it will appear in the list in Ahorn immediately. If you make an update to the image, however, it won't appear in the window until you restart Ahorn.