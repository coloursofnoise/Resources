## How-To: Audio mods without replacing original sounds

You'll need:
- FMOD Studio **1.10.\*** (**Don't** use FMOD Studio 2.\*, as it is incompatible with Celeste and will break projects made in 1.\*.). You will find it on the [FMOD downloads page](https://www.fmod.com/download) (you need to create an account, but the program is free).
- the Celeste FMOD project: you will also find it on the [FMOD downloads page](https://www.fmod.com/download), in the Learning Resources section. **Make sure to read the EULA.**

_FMOD Studio is compatible with WINE._

Here is a step-by-step guide to create a bank with music you have as sound files:

1. Open the Celeste FMOD project in FMOD Studio: `fmodstudio20000celeste-project/FMOD Studio Celeste Project/celeste_audio.fspro`.
2. On the left panel, switch to the Banks tab, and create a new bank for your mod. You need 1 bank per mod: if you have multiple tracks, you can fit them all in one bank. Name it, for example, `yournickname_mapname`.

![](https://cdn.discordapp.com/attachments/445236692136230943/714571482231210024/unknown.png)

3. Select File > Import Audio Files... then browse to your sound/song. This brings up a new "Audio Bin" window. You'll want to right click on your song, then select "Create New Event":

![image](https://cdn.discordapp.com/attachments/445236692136230943/714572284194455603/unknown.png)

Choose "2D Event", then close the Audio Bin window.

4. On the left panel, switch to the Events tab: you'll find your sound/song there. Preferably drag it into a directory with your nickname and rename it so that the name doesn't contain symbols / spaces / etc.

5. Assign your song/sound to your bank:

![image](https://cdn.discordapp.com/attachments/445236692136230943/714573969512071289/unknown.png)

6. Re-route your new event to the right bus:

    - Open the mixer window.  
    ![](https://cdn.discordapp.com/attachments/429775352295063563/476487647892602892/unknown.png)

    - Right-click your event and reroute the event to the mains group. Don't create a new group.  
    ![](https://cdn.discordapp.com/attachments/429775352295063563/476488253382590464/unknown.png)

    - You can now close the mixer window.

7. Add the fade parameter to your music:

    - Add the shared fade parameter by clicking the (+) tab.  
    ![](https://cdn.discordapp.com/attachments/445236692136230943/714576338199117824/unknown.png)

    - Add automation to the master volume in the fade parameter tab.  
    ![](https://cdn.discordapp.com/attachments/445236692136230943/714576523293884476/unknown.png)

    - Add two points at the 2 edges of the graph: -∞ dB to 0.00 dB  
    ![](https://cdn.discordapp.com/attachments/429775260108324865/478316724907671552/unknown.png)

    - You now have a "fade" cursor on top of the screen, adjusting now will control the music volume. This is what music fade triggers use to adjust the music volume as well.
    ![](https://cdn.discordapp.com/attachments/445236692136230943/714577386758340688/unknown.png)

8. Make your music loop:

    - Right click the black logic track above your audio track, and select "Add Loop Region". 
    ![](https://cdn.discordapp.com/attachments/445236692136230943/714577912963268698/unknown.png)

    - Extend the loop region to however you see fit.

    ![](https://cdn.discordapp.com/attachments/462498749097443330/547105130441605160/loop.gif)

9. Hit File > Build. When this is done, you will find your bank in `fmodstudio20000celeste-project/FMOD Studio Celeste Project/Build/Desktop`. Take **only** the .bank file you created (**don't** take Master Bank.bank, sfx.bank, etc... those are the vanilla banks) and copy it to `Mods/yourmod/Audio`.

9. **Generate the GUIDs.txt**:

![](https://cdn.discordapp.com/attachments/429775260108324865/473619203174301706/unknown.png)

Once generated, you'll find it in `fmodstudio20000celeste-project/FMOD Studio Celeste Project/Build/GUIDs.txt`. Copy it in `Mods/yourmod/Audio` and rename it to `yourbankname.guids.txt`:

![](https://cdn.discordapp.com/attachments/445236692136230943/714582075646279860/unknown.png)

10. In Ahorn, you can use your music by typing its event name manually. For example, if you have this in the Events tab:

![](https://cdn.discordapp.com/attachments/445236692136230943/714582221805060228/unknown.png)

You can use this in Ahorn:

![](https://cdn.discordapp.com/attachments/445236692136230943/714583243806212157/unknown.png)

If you have any further questions regarding audio mods, ask for help in the #modding_help channel on the Discord server.

**Don't modify and share modified music, sfx, ui and master banks.**
