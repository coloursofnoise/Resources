## How-To: Audio mods without replacing original sounds

You'll need FMOD Studio 1.10.* and the Celeste FMOD project. Both can be found on the FMOD downloads page.  
**Make sure to read the EULA.**

1. Assign your events to a **new bank per mod.**  
![](https://cdn.discordapp.com/attachments/429775260108324865/445714977353891843/unknown.png)

2. **Generate the GUIDs.txt** and name it `bankname.guids.txt`  
![](https://cdn.discordapp.com/attachments/429775260108324865/473619203174301706/unknown.png)

3. **Follow the [modstruct tutorial.](https://everestapi.github.io/tutorials/modstruct)**

If you have any further questions regarding audio mods, please ping 0x0ade#1584 on the Discord server.

**Don't modify and share modified music, sfx, ui and master banks.**



## How-To: Route your new audio events to the correct buses

1. Open the mixer window.  
![](https://cdn.discordapp.com/attachments/429775352295063563/476487647892602892/unknown.png)

2. Right-click your event and reroute the event.  
![](https://cdn.discordapp.com/attachments/429775352295063563/476488253382590464/unknown.png)


## How-To: Make music fade

1. Add the shared fade parameter.  
![](https://cdn.discordapp.com/attachments/429775260108324865/478316385169047554/unknown.png)

2. Add automation to the master volume in the fade parameter tab.  
![](https://cdn.discordapp.com/attachments/429775260108324865/478316598013460485/unknown.png)

3. -∞ dB to 0.00 dB  
![](https://cdn.discordapp.com/attachments/429775260108324865/478316724907671552/unknown.png)


