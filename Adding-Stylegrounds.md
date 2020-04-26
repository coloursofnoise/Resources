# What are Stylegrounds?

**Stylegrounds** are backgrounds and effects you can add to your map. 
This tutorial explains the _entire_ Stylegrounds menu and how you are able to add your own backgrounds to your mod.

# The Stylegrounds menu

The Stylegrounds menu is divided into two sections, **Parallax** and **Effect**.

## Parallax

The **Parallax** section may seem complicated at first but it's actually quite easy to use and get used to.
Here's what it looks like and I will go in order, explaining what each of these sections do.
![Parallax Window](https://user-images.githubusercontent.com/64371989/80315026-5c177580-87f5-11ea-96fa-82edf32c95d8.png)

### Texture

This is where you pick what your background will look like. Backgrounds that begin with bgs/number are the ones you should use as the ones starting with bgs/nameguysdsides_stylegrounds are from the D-sides Pack and if someone that doesn't have that mod the game will crash. There also four other backgrounds that you can freely use at the bottom of the list: _purplesunset_, _darkswamp_, _mist_ and _northernlights_.

### Only

This is where you pick in which rooms your background will appear. let's say you have three rooms, **a1, a2 and a3**. If you wanted your background to appear in all of those rooms, you'd put _a1,a2,a3_ in the Only section. You can alternatively put in _a*_. The * makes it so that the background appears in every room starting with the letter a. If you put just * then your background will appear in every room.

### Exclude

This is very similar to the Only section. Here go all of the rooms you _don't_ want the background to appear.
Let's say you have rooms **a1, a2, a3, a4 and a5** and you want the background to appear only in **a1 and a2**. You can put _a*_ in the Only section and then put _a3,a4,a5_ in the Exclude section.

### Tag

This is a pretty important section if you wish to code. More about it in the Effect section of this tutorial.

### Flag & Not Flag

If you use the Flag trigger, you can make this background appear using that trigger instead of it just appearing. You can put literally anything you ant in there, but it's very important to make it unique, so to do that, you can just add your username in the flag name. **Leave this section empty if you don't plan on using Flag triggers.**

You can use the Flag trigger and the flag you set in the Not Flag section to make the background disappear.
**Leave this section empty if you don't plan on using Flag triggers.**

### Blend Mode

This decides in what way your background will blend with the other effects and backgrounds.

### Colour

Here you pick the colour of your background. You need to use Hex Colors so putting in _Red_ will not work.

### X & Y

This is used to move the background if you don't like where it is.
If you put _-10_ in the Y section, the background would appear a bit higher in-game.

### Scroll X & Y

This is the section that decides at which speed your background will move Horizontally (X) and Vertically (Y). If you plan to use the city background, setting Scroll Y to 0 would make it not move up and down.

### Speed X & Y

This decides at which speed your background will move _on its own_ Horizontally (X) and Vertically (Y). If Speed X is 1, the background will move to the right, while if Speed X is -1, the background will move left instead.

### Alpha

How transparent the background is, 0 being fully transparent and basically non-existent.

### Fade In Checkbox

If ticked, the background will go from being transparent to the Alpha you set when you enter or leave the room it's in.

### Flip X & Y Checkboxes

If Flip X is ticked, the background will be flipped horizontally.
If Flip Y is ticked, the background will be flipped vertically.

### Foreground Checkbox

If ticked, the background will appear in front of everything instead of the back. You usually want this unticked.

### Instant In and Out Checkboxes

If Instant In is ticked, the background will be loaded during the transition between two rooms.
If Instant Out is ticked, the background will disappear during the transition between two rooms.

### Loop X & Y

If Loop X is ticked, the background will loop horizontally.
If Loop Y is ticked, the background will loop vertically.

## Effect

The **Effect** section is pretty small and very easy to learn. Here's what it looks like and I will go in order, explaining what each of these sections do.![Effect Window](https://user-images.githubusercontent.com/64371989/80316399-dba94280-87fd-11ea-9b8d-66ba9a42e55d.png)

### Name

The effect you want to add.

### Rooms, Exclude, Flag, Not Flag and Foreground Checkbox

Rooms is the same as Only from the parallax tab.
Exclude, Flag, Not Flag and the Foreground Checkbox are the exact same as the ones from the parallax tab.

### Tag

Same as the Tag section in the Parallax tab.
If you pick the black hole effect and put **blackhole** in the Tag section, the black hole will appear in the background whenever the player touches a Moon Glitch Background Trigger.

# How to insert custom backgrounds

Let's say your custom background is called **mybackground.png**.

To add your custom background, you must first have a proper mod structure, you can find the tutorial for that [here](https://github.com/EverestAPI/Resources/wiki/Mod-Structure).

The file structure should look like this:

Mods > yourmod > Graphics > Atlases > Gameplay > bgs > uniquefoldername > mybackground.png

Once your background is in there, it will appear in Ahorn immediately. If you made an update to the image, the update will not appear in Ahorn until you restart it.