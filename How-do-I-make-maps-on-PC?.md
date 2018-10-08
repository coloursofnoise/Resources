To make maps, first make sure you've done everything in [[How do I install mods on PC?]]. Next, you'll need Ahorn. For up-to-date Ahorn documentation, including installation, see https://github.com/CelestialCartographers/Ahorn.

## Map-Making FAQ
### How do I save maps?
Control and S.

### How do I delete a room?
Alt and Delete.

### How do I make a room?/Why is my screen blank?
Click Room at the top, and then Add.

### How do I automate boring tasks?
If you know how to program, use [Maple](https://github.com/CelestialCartographers/Maple). Ahorn will likely not have a GUI macro system, but Maple is quite simple for programmars.

### How often are collab maps?
There isn't a set schedule, but generally every 3-6 months. Don't complain if there isn't one.

### How do I add room transitions?
Add one player entity per room entrance / exit.

### How do I add a B side to my own map?
YourMap.bin + YourMap-B.bin

### Why doesn't my golden berry appear? / Why doesn't my C side appear?
You'll need to collect each heart in every A and B side _in the levelset,_ or use the debug save.

### What does the "Only" field mean when adding stylegrounds in Ahorn?
It defines in which rooms it'll appear, accepting the following format: `a-1,b-2,c-*` (or just `*` for "all rooms")

### How do I add my own decals in Ahorn?
Ahorn will find it if you place it in `Celeste/Mods/YourMod/Graphics/Atlases/Gameplay/decals/author/decal.png`  
Filenames ending with numbers will be used as animation frames by Celeste; Ahorn hides all of these frames besides the first frame (00) so the decal list is not cluttered.  
If it doesn't show up in your decals list, even after refreshing it, try to restart Ahorn.