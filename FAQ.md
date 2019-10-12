### What are you using to look inside Celeste's code?
dnSpy. But please avoid using the dnSpy editor. Try to detour methods at runtime, and if something _must_ be patched, ask for help in the #modding_help channel on the Discord server.

### How do you do code blocks?
\`\`\`cs  
CODE HERE  
\`\`\`  
Replace cs (csharp) with yaml, julia, ...

### Why does Celeste crash with `OutOfMemoryException`?
You've got too many mods (including maps) installed, and your poor PC can't handle them all at once.  
Open `ModSettings/Everest.yaml` in a text editor (f.e. Notepad) and change `LazyLoading` from `false` to `true`

### The Everest Installer is displaying an empty version list! How do I fix this?

Try getting the last Everest Installer version [here](https://gamebanana.com/tools/download/6449). 

The update servers have changed in March 2019, so if you got an old version of the installer, it will still try to connect to the old servers, and those do not work anymore.

### Problems with running or installing Ahorn
[Check this page for detailed information](Ahorn-Installation-Help)