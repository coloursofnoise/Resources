## Creating a custom tileset

### Step 1

* Go to your Celeste folder -> Content -> Graphics
* Copy the `ForegroundTiles.xml` file
* Go back to your Celeste folder, and go to Mods -> YourModFolder -> Graphics
* Create a new folder there (for example `Xaphan`)
* Paste the `ForegroundTiles.xml` file in that new folder

### Step 2

Make a copy of a tileset template, then edit it with any image editor to make your tileset.

#### Using the improved template by 0x0ade

![template](https://i.imgur.com/jUq838l.png)

To set up this template, open the `ForegroundTiles.xml` file you just copied. Just below `<Data>` at the beginning of the file, copy-paste the entirety of [this XML file](https://gist.github.com/0x0ade/3beb5eb3008f3f25be0b3204d1ee585a).

This XML refers to the `subfolder/betterTemplate` tileset. For it not to crash, copy the template into `Mods/yourmod/Graphics/Atlases/Gameplay/tilesets/subfolder/betterTemplate.png`.

#### Using the vanilla template

You can find this template in [the graphics dump](https://drive.google.com/file/d/1ITwCI2uJ7YflAG0OwBR4uOUEJBjwTCet/view), in `Graphics/Atlases/Gameplay/tilesets/template.png`.

Here is an annotated version of this template:

![annotated vanilla template](https://cdn.discordapp.com/attachments/663507492529111057/664207894480289792/unknown.png)

### Step 3

At the end of the `ForegroundTiles.xml` file, just before the `</Data>` line, add the following line:
```xml
<Tileset id="w" copy="y" path="name" sound="8"/>
```
* Replace `w` by the id you want, that is not one already used (so do not use 1, 3 to 9, a to o, y and z). **This id has to be 1 character long.**
* Replace `y` with `z` if using the vanilla template.
* Replace `name` by the name you want to call your tileset. Remember that name, you will need it later.
* Replace `8` by whatever sound you want (see bottom of page for the list).

Then, save and close the file.

### Step 4
* Go back to your Graphics folder (the one in your mod folder) -> Atlases -> Gameplay
* Create a `tilesets` folder
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

0. null
1. asphalt
2. car
3. dirt
4. snow
5. wood
6. bridge
7. girder
8. brick
9. traffic block
10. (unused)
11. dreamblock inactive
12. dreamblock active
13. resort wood
14. resort roof
15. resort platforms
16. resort basement
17. resort laundry
18. resort boxes
19. resort books
20. resort forcefield
21. resort clutterswitch
22. resort elevator
23. cliffside snow
24. (unused)
25. cliffside grass
26. (unused)
27. cliffside whiteblock
28. gondola
29. (unused)
30. (unused)
31. (unused)
32. glass
33. grass
34. (unused)
35. cassette block
36. core ice
37. core rock
38. (unused)
39. (unused)
40. glitch
41. (unused)
42. internet café
43. cloud
44. moon