### Ok, what the heck is ghostnet?
Ghostnet is a mod for Celeste (it'd be weird if it wasn't) created by 0x0ade. It allows for multiplayer, and you can host and join servers and even create permanent ones.  
If stuff breaks, and everything you read here doesn't help you, just ping @leo60228#0480 (between 8AM-7:30PM EST) or @0x0ade#1584 (between 12PM(?)-1AM CEST) in #modding_help or #modding_general.

### How do I install GhostNet?
1. Download the [Everest API](https://everestapi.github.io/)  
2. Download [GhostNet](https://gamebanana.com/gamefiles/6801)  
3. If you installed with the 1 click installer, skip this. Otherwise, put the zip inside of your Mods folder in Celeste's data.  

### How do I join a server?
1. Load up Celeste after doing everything mentioned previously.
2. Go into Mod Settings,  and down to GhostNet. Set Name to whatever you want to be known as. The server should be preset to `celeste.0x0ade.ga`. If you're just planning on playing on the official server, leave this as it is. If you want to play on a friend's server, set this to their IP (and if they're not on port 2782 add :####, #### being the port they chose). ~~Other servers include `ghostnet.leo60228.space`~~ (now the official server).
3. Switch Connected to ON. If it works, congrats! If it doesn't, keep reading!

### How do I host a server?
0. Port forward 2782 in your router. This is something I can't really help you with, so just google how to do so.
1. Load up Celeste w/ GhostNet
2. Connect to "localhost". This will start a server on your computer! If you disconnect or your game crashes, the server will die with it, so be warned.
3. If you want others to connect (I assume you do), tell them to connect to your IP as the server. You can find your ip by googling "what is my ip".

### ⚠ Quick note:
Sometimes the Ghostnet server for some reason or another doesn't like the latest version of ghostnet, and occasionally ghostnet gets updated multiple times in a day, so be wary of this. If I choose to roll back to a different version of Ghostnet, download links will be provided in #modding_general's pins. I'll also tag everyone with the `ghostnetter` role, so if you would like those updates make sure to do `?rank ghostnetter` in #roles!

# Ghostnet FAQ 
If your ghostnet is broken, see this.

### Why isn't GhostNet showing up?
This could be for a number of reasons. If Everest is working (you should see the Everest version on the CELESTE screen and a mod options menu) then you probably just need to reinstall GhostNet (delete .zip and download it yourself). If Everest is not working, reinstall both.

### Why can't I connect to the official server?
This is primarily for a couple of reasons. The server is hosted using an AWS Spot instance, meaning that the price of the server is variable (and often 80%+ cheaper). For example, at peak AWS usage (different from server usage!), the price of the server may go above $6/month ($0.0112/hour), at which point the server gets shut down automatically. It'll turn on again when the price goes back down. I don't currently have a monitoring solution, but me or 0x0ade can tell you if this happens.

This could also be for a different reason - sometimes your GhostNet version is very far behind. Make sure you've updated to the latest version (as of writing 1.3.14) of GhostNet. 

Sometimes, certain users have issues connecting to dahlukeh's network. The reason is currently unknown, but you can try a different server.

### Why are other players invisible?
This could be one of two things. If you can send messages to each other, see A. If you cannot, see B.

A. If you can send messages to each other, it may mean that your network is broken. First, ask the owner of the server to restart it, which may fix the problem. If it doesn't, this problem may only occur with the official server, in which case you can use a different one. If it's still broken, go into `Celeste/ModSettings/GhostNetMod.yaml` and change `SendUFramesInMStream` to true. After this, restart your game. **Be warned this may damage your router and slow down your game. Be sure to turn it off after testing.** The reason isn't currently known, but it may be due to high latency, which TCP is better at handling.

B. If you can **not** send messages to each other, it means the server is broken. Message the owner of the server (in the case of the official one, see the contact info at the top) and ask them to restart their server.

### Why are there clones of me and/or other players?
This is a very minor bug with Ghostnet that usually only happens on servers with a lot of traffic and after a few days of uptime. These clones do nothing and should not interfere, but they can be removed with a server restart as well. Don't ping me about these.

### Why do some people have rainbow hair?
They've got the Fabeline mod installed. It's a pretty... fabulous mod <img alt="thonkerguns" src="https://cdn.discordapp.com/emojis/370633336202330112.png?v=1" height="16"> ([get it here](https://gamebanana.com/skins/163152))

### Why doesn't my own server work?
Make sure your ports are forwarded. Some routers will not port forward unless you hit an add button and then an apply button.  
Also, make sure your firewall isn't blocking it. If the server actually crashes (assuming it's ghostnet doing it and/or you have headless enabled) ping me.

### How can I see where other players are?
Hit `Tab` on keyboard, `View` on Xbox One, `Back` on Xbox 360.

### Different problem, crash, or nothing works?
Ping either @leo60228 or @0x0ade and we'll help you out to the best of our ability.