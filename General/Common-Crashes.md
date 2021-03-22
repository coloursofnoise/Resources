# What should I do when Celeste crashes?
**_DON'T PANIC_**

Read the first line of the error (after the timestamp). It should contain one of two things:

### `Yo, I heard you like Everest so I put Everest in your Everest{...}`:
As the rest of the error says, Everest has encountered an issue that couldn't be handled by normal means. Follow the instructions [below](#reporting-issues) to report this issue and get help.

### `System.{ERRORNAME}Exception: {Description of the error}`:
Something has gone wrong, but Everest at least knows what it is. 
As a user, first read through the following list of common errors for something matching or similar to the `{ERRORNAME}` or description of the error displayed in the log, and follow the instructions provided.  
If the particular error is not in the list, no fix is provided, or the fix does not work, then proceed to the instructions [below](#reporting-issues) to report the issue.

---
<br/>

## `OutOfMemoryException`
You've got too many mods (including maps) installed, and your poor PC can't handle them all at once. Try blacklisting or uninstalling some of them.  
* To disable a mod while Celeste is running, open the `Mod Options` menu from the main menu and select the option to `Enable or Disable Mods`.
* If you are unable to start Celeste, go to the Mods folder next to Celeste.exe, and add the name of the zip/folder in the `blacklist.txt` file. For example, if you want Everest to skip over `CrystalValley.zip` and `Dadbod.zip`, just put those in `blacklist.txt`:
```
CrystalValley.zip
Dadbod.zip
```
  :information_source: *The mod you are trying to blacklist may already be in `blacklist.txt` with a `#` before it. Simply removing the `#` will cause the mod to be blacklisted.*
* To uninstall a mod, just go to the Mods folder next to Celeste.exe, and delete the mod's zip/folder.

If you are out of luck or don't have much RAM, you can make Everest only load textures when they are required. _Please note this can cause issues._ For that, open `Saves/modsettings-Everest.celeste` in a text editor (f.e. Notepad) and change `LazyLoading_Yes_I_Know_This_Can_Cause_Bugs` from `false` to `true`.


## `IOException: Too Many Open Files`
Celeste has too many files open.  
When installing mods, it is not necessary to extract them, as Everest will read the .zip files automatically. This is actually preferrable, because it means that your operating system will only see each mod as one file, rather than potentially hundreds.  
Make sure downloaded mods are in .zip files, especially as some systems/browsers will automatically try to unzip them.


## `Ionic.Zip.BadCrcException`
Something went wrong while downloading a mod.  
Somehow one of your mod zips got corrupted, and will need to be reinstalled.  
If you have an idea of which one it may be (if you downloaded one recently, or if you can check your `log.txt` for the last loaded mod), then delete it from your Mods folder and redownload it.


## `Exception: FMOD Failed: ERR_EVENT_ALREADY_LOADED`
Two FMOD banks define the same event.  
If you aren't actively using FMOD, this error is usually caused by having more than one copy of the same mod (and therefore the same audio bank) loaded at the same time.  
Check your Mods folder carefully for duplicate mods and remove them.

## `Exception: FMOD Failed: ERR_INVALID_HANDLE`
Something went wrong with the sound engine used by Celeste.  
Possible fixes are:
- Unplug/replug your speakers/headphones
- Try a different set of speakers/headphones
- Restart your audio drivers
- Update your audio drivers


## `Steam not found!`
Ensure that Steam is running, restart it if necessary.

<br/>

# Reporting Issues
There are two ways of reporting issues:

### Discord (preferred)
- Join the Mt Celeste Climbers Association Discord:  
[![Discord Invite](https://raw.githubusercontent.com/EverestAPI/Everest/dev/github/invite.png)](https://discord.gg/6qjaePQ)
- Report your issue in the `#modding_help` channel, following the [checklist](#reporting-checklist).
- Wait patiently for someone to help you.

### GitHub (only for issues with Everest itself, not with mods)
- Create a New Issue on the [main Everest GitHub](https://github.com/EverestAPI/Everest/issues).
- Use a *descriptive title* (not just "Crash plz help").
- Follow the [checklist](#reporting-checklist) to report your issue.

<br/>

---
## Reporting Checklist
- **Describe what you were doing** before you encountered the error.
- If it was working previously, **list any changes you made** to your game since then.
- Include **what you have done already** to try to fix it.
- **Attach the `error_log.txt` and `log.txt`** (both located in your Celeste folder).  
 If you got the Catastrophic Error warning, then only the `log.txt` is needed.  
 :warning: *If you have restarted your game since the crash, your `log.txt` will have been reset.* Everest will automatically store past logs in the `LogHistory` folder, which is also in your Celeste folder.
- If this is an error you believe to be specific to a mod, **notify the mod author** if possible.