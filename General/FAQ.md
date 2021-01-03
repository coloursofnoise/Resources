### What are you using to look inside Celeste's code?
dnSpy. But please avoid using the dnSpy editor. Try to detour methods at runtime, and if something _must_ be patched, ask for help in the #modding_help channel on the Discord server.

### How can I mod my Nintendo Switch?
See [here](Nintendo-Switch-Modding) for information.

### How do you do code blocks?
\`\`\`cs  
CODE HERE  
\`\`\`  
Replace cs (csharp) with yaml, julia, ...

### Why does Celeste crash with `OutOfMemoryException`?
You've got too many mods (including maps) installed, and your poor PC can't handle them all at once. Try blacklisting or uninstalling some of them.
* To blacklist a mod, go to the Mods folder next to Celeste.exe, and add the name of the zip/folder in the `blacklist.txt` file. For example, if you want Everest to skip over `CrystalValley.zip` and `Dadbod.zip`, just put those in `blacklist.txt`:
```
CrystalValley.zip
Dadbod.zip
```
* To uninstall a mod, just go to the Mods folder next to Celeste.exe, and delete the mod's zip/folder.

If you are out of luck or don't have much RAM, you can make Everest only load textures when they are required. _Please note this can cause issues._ For that, open `Saves/modsettings-Everest.celeste` in a text editor (f.e. Notepad) and change `LazyLoading_Yes_I_Know_This_Can_Cause_Bugs` from `false` to `true`.

### The Everest Installer is displaying an empty version list! How do I fix this?

Try getting the last Everest Installer version [here](https://gamebanana.com/tools/download/6449). 

The update servers have changed in March 2019, so if you got an old version of the installer, it will still try to connect to the old servers, and those do not work anymore.

### Problems with running or installing Ahorn
[Check this page for detailed information](Ahorn-Installation-Help)