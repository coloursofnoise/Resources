### What are you using to look inside Celeste's code?
dnSpy. But please avoid using the dnSpy editor. Try to detour methods at runtime, and if something _must_ be patched, ask 0x0ade for help.

### How do you do code blocks?
\`\`\`cs  
CODE HERE  
\`\`\`  
Replace cs (csharp) with yaml, julia, ...

### Why does Celeste crash with `OutOfMemoryException`?
You've got too many mods (including maps) installed, and your poor PC can't handle them all at once.  
Open `ModSettings/Everest.yaml` in a text editor (f.e. Notepad) and change `LazyLoading` from `false` to `true`