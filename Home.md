Welcome to the Everest resources repository!

Make sure to follow the **pages list on the right side**, or the general FAQ below.

### What are you using to look inside Celeste's code?
dnSpy. But please avoid using the dnSpy editor. Try to detour methods at runtime, and if something _must_ be patched, ask 0x0ade for help.

### How do you do code blocks?
\`\`\`cs  
CODE HERE  
\`\`\`  
Replace cs (csharp) with yaml, julia, ...

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

### Why does Celeste crash with `OutOfMemoryException`?
You've got too many mods (including maps) installed, and your poor PC can't handle them all at once.  
Open `ModSettings/Everest.yaml` in a text editor (f.e. Notepad) and change `LazyLoading` from `false` to `true`