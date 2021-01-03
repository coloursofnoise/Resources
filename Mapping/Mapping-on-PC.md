To make maps, first make sure you've done everything in [[How do I install mods on PC?]]. Next, you'll need Ahorn. For up-to-date Ahorn documentation, including installation, see https://github.com/CelestialCartographers/Ahorn.

## Map-Making FAQ
### How do I save maps?
Control and S.

### How do I delete a room?
Alt and Delete.

### How do I make a room?/Why is my screen blank?
Click Room at the top, and then Add.

### How do I automate boring tasks?
If you know how to program, use [Maple](https://github.com/CelestialCartographers/Maple). Ahorn will likely not have a GUI macro system, but Maple is quite simple for programmers.

### How often are collab maps?
There isn't a set schedule, but generally every 3-6 months. Don't complain if there isn't one.

### How do I add room transitions?
Add one player entity per room entrance / exit.

### How do I add a B side to my own map?
YourMap.bin + YourMap-B.bin

### Why doesn't my golden berry appear? / Why doesn't my C side appear?
You'll need to collect each heart in every A and B side _in the levelset_ and complete the side at least once, or use cheat mode.

### How do I use Stylegrounds in Ahorn?
See the Stylegrounds tutorial [here](https://github.com/EverestAPI/Resources/wiki/Adding-Stylegrounds).

### How do I add my own decals in Ahorn?
Ahorn will find it if you place it in `Celeste/Mods/YourMod/Graphics/Atlases/Gameplay/decals/author/decal.png`  
Filenames ending with numbers will be used as animation frames by Celeste; Ahorn hides all of these frames besides the first frame (00) so the decal list is not cluttered.  
If it doesn't show up in your decals list, even after refreshing it, try to restart Ahorn.

### How do I convert my map to a .zip?
.bin maps are not recommended for public distribution, and it is recommended to use a .zip instead. If you would like to convert them automatically, you can use [Postcard](http://postcard.leo60228.space/start).

### How do I add a checkpoint mask onto my custom checkpoints?
[Postcard](http://postcard.leo60228.space/mask) can do this automatically. Simply upload your screenshot, hit submit, and save the new image. Please report issues to @leo60228#0480 on Discord. If this doesn't work, manual instructions are also available.

#### Manual instructions
**Note that these instructions are for the GIMP image editing program (https://www.gimp.org/)**

For starters, download this mask. (using other masks from a graphics dump of Celeste is fine also)
![](https://cdn.discordapp.com/attachments/429775352295063563/554859401651945472/mask.png)


Right click your original image in the layers tab and click Add Layer Mask.

Be sure you have Transfer Layer's Alpha Channel chosen and Invert Mask checkmarked.

Then, right click on the checkpoint mask in the editor and Copy it. (Edit > Copy)

In the layer tab be sure that the black part of the original image is selected. (that's the mask)

Then right click in the editor and paste.

Use a tool like the Rectangle Select tool to get rid of the _floating selection layer_ by clicking anywhere in the editor.

You should now see your image with the checkpoint mask on it.

![](https://cdn.discordapp.com/attachments/429775352295063563/554849542827278346/how2GIMPmask.gif)
