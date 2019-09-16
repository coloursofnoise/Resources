## Creating a custom tileset

### Step 1
Make your tileset using any image editor.
Use the dumped graphics (see [[Useful links]]) and use the template in there to help you.

### Step 2
* Go to your Celeste folder -> Content -> Graphics
* Copy the `ForegroundTiles.xml` file
* Go back to your Celeste folder, and go to Mods -> YourModFolder -> Graphics
* Create a new folder there (for example `Xaphan`)
* Paste the `ForegroundTiles.xml` file in that new folder

### Step 3

Open that file. Then, at the end, just before the `</Data>` line, add the following line:
```xml
<Tileset id="y" copy="z" path="name" sound="8"/>
```
* Replace `y` by the id you want, that is not one already used (1, 3 to 9, a to o)
* Replace `name` by the name you want to call your tileset. Remember that name, you will need it later.
* Replace `8` by whatever sound you want (see bottom of page for the list). 

Then, save and close the file.

### Step 4
* Go back to your Graphics folder (the one in your mod folder) -> Atlases -> Gameplay
* Create a `tileset` folder
* Copy your tileset there, and name it the same thing you put in ForegroundTiles.xml (`name` in this exemple)

### Step 5
* Open Ahorn and load your map
* Go to Map -> Metadata
* In the Foreground Tiles field, copy the path to your `ForegroundTiles.xml`: in this tutorial, it is `Graphics/Xaphan/ForegroundTiles.xml` (replace `Xaphan` by the name of the folder you created in step 2)
* Click Update. Save and reload your map.

_Thanks Xaphan for the tutorial!_

## Tileset sound IDs

The following IDs were copied from the Celeste FMOD Studio project.  
They can be found in event:/char/madeline/footstep - thanks to Kevin Regamey from PowerUp Audio!

Entries marked as (unused) don't have any sound associated to them.  
Additionally, ID 20 doesn't have a sound associated to it in the public Celeste FMOD Studio project.

0. null
1. asphalt
2. car
3. dirt
4. soft snow
5. wood walkway
6. (unused)
7. metal girder
8. brick
9. zip movers (traffic blocks)
10. (unused)
11. dreamblock inactive
12. dreamblock active
13. resort wood
14. resort roof
15. resort platforms
16. (unused)
17. resort linens
18. resort boxes
19. resort books
20. resort forcefield
21. resort clutterswitch
22. resort elevator
23. cliffside snow
24. (unused)
25. (unused)
26. (unused)
27. cliffside whiteblock
28. cliffside gondola
29. (unused)
30. (unused)
31. (unused)
32. reflection aurora glass
33. reflection grass
34. (unused)
35. (unused)
36. core ice
37. core rock

_Thanks 0x0ade for the list!_