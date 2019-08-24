# Game mechanics
### Player (Spawn Point)
These entities define where the player will respawn if they die. Upon a screen transition, the game will activate the one closest to the player. Change respawn triggers will change the Spawn Point to the nearest one at that point. Respawn Target will change the Spawn Point to the one nearest the top left corner of the node. If there is no change respawn trigger, even if you cross a Spawn Point, it'll not activate. If a room ever doesn't have a Spawn Point inside it, the game will not allow the player to enter it.
### Jump Throughs
These platforms found throughout the game enable the player to cross through its bottom and land on top safely. Used commonly for upwards screen transitions or for aerial spikes. There is an interesting interaction with these that allows you to be crushed by another entity (e.g. Falling Blocks/Kevin) which forces you through the solid side of it, making you fall through instead of dying. You can also clip through them if landing on them with a feather on the same frame you exit the feather state. 
### Spikes
One of the most common obstacles of the game. Used for covering otherwise safe ground or walls. They have a hitbox of 3 pixels in height (if vertical) or width (if horizontal), meaning the tips don't kill the player. If you are moving in the same direction the spikes are facing, they will not kill you either. Despite them having different sprites for different chapters, their hitboxes are all the same. They attach to moving entities.
### Strawberries
Your regular fun but useless collectibles. If winged, it flies away on dash. After grabbing, you have to land on "safe ground" (FG tiles not covered with Strawberry Blockfileds) for at least 9 frames to collect. If you add nodes to them, seeds will appear, which have to be collected without touching the ground (having landed for longer than 9 frames, jumping or dashing after landing, but you can "land" and "slide off" before the 9th frame and keep the seeds). If all are all collected together, the strawberry itself will appear.
### Golden Strawberries
These work almost the same as strawberries in the sense of being useless collectibles. However, these ones that are usually located above the player when the chapter starts (given they have previously cleared it at least once before), and can only collect with a Golden Strawberry Collection trigger, found at the end of a level. If the player ever dies with one, they will be returned to where the strawberry was collected, so the start of the level, reseting the timer. If Winged, it will try to fly away when the player dashes, like regular strawberries. If it's winged no dash, the golden strawberry checks if the player has dashed at all during the entire level, instead of just the screen it's in. If used, it's found at the end of a level, like the Forsaken City A side of the vanilla.
### Invisible Barriers
Just what they sound like: they block the player, as they are solid, but they are invisible. Used rarely in the vanilla, but used to prevent the player from skipping the "Search" checkpoint of the Mirror Temple with a demodash to get to Theo early. 
### Springs
When the player interacts with these, they lose all momentum they previously had and gives a set speed and direction. This speed and direction can be interrupted with a dash and is slightly influenced by the player's directional inputs. They attach to moving entities.
### Crumble Blocks
These platforms begin to crumble as soon as you interact with them (wether landing or grabbing). If you land on them, they disappear after 0.6 seconds (36 frames) or immediately after jumping, dashing, or sliding off. If you grab its side, it will always disappear after a timeout of 1 second, time during which you can still jump on or off it. They regenerate after 2 seconds.
### Falling Blocks
These blocks, as their name implies, fall upon interaction. If you land on top or hold on to its side, it falls after 0.6 seconds (36 frames), and if you let go or fall off, it falls immediately with a speed of 160 pps. They can break Dash Blocks always, and keep falling until offscreen or until they collide with Foreground tiles or other solid entities. If what they landed on moves or falls from under them, they will continue falling. One can also disable "climb fall" so it can only by activated from the top or other entities such as Kevins. It can also be used for Badeline Boss, where they Fall only after Badeline is hit in a specified node.
### Exit Blocks
These entities become solid if the player is not inside of its hitbox. Commonly used to block of backtracking. 
### Zip movers
Otherwise known as Traffic Blocks, these move from their original position to wherever their node is set, marked visually by the zip line, ignoring whatever own on their way, even Foreground tiles. When activated by grabbing or landing on top, they always take the same time to reach their node (0.5 seconds/30 frames), regardless of the distance; the farther the node is, the faster it'll go. After it reaches its node and 0.5 seconds/30 frames of cooldown, it'll return to its original position in 2 seconds, but it can still be grabbed or jumped off of. It will only move again after it has returned to its original position after 0.5 seconds/30 frames of cooldown.
### Refills
These crystals refill the player's dash and stamina. If you run out of stamina while still having your dash and touch one, you'll use it, and refill only your stamina. If you dash into or off of one or touch it after having dashed, you'll refill stamina and dash. If you have two dashes, only using one dash will still consume the refill, and using both dashes will refill both dashes unless the second dash was obtained via a two-dash refill, which gives the player a temporary second dash that can only be used once. Marking "One use" will make it not reappear after being used until a respawn or a screen transition. They respawn after 2.5 seconds.
### Cassette
These entities are what is used to gate a B side of a level. Upon collection, the game will stop, play a cutscene, and then move the player through the nodes until it reaches the last one, where the bubble pops, and the player is free to move. Collecting it will disable all cassette blocks previously alternating.
### Cassette Blocks
These blocks pop in and out of the background into solid blocks to the tempo of the music. Any entity attached to it will appear and disappear with the block. There are 4 colors available, two of which are Everest inclusions. The order for appearance is Pink, Blue, Bright Sun (Everest), and Malachite (Everest). Any default spikes attached to them will become the color of the block they are attached to. If two blocks of the same color are next to each other, their hitboxes will "merge". If the player jumps on a Cassette Block as it pops in, they will jump even higher than normal.
### Dash Blocks
Blocks that break with a dash or other special conditions. All entities or conditions that can break one are a player's dash, moving Kevin blocks, falling Falling Blocks, or the player whilst inside of a booster, regardless of color. If "Can Dash" is disabled, the player's dash alone can't break the block anymore, but everything else can. Marking "Permanent" means that the block will remain broken after being broken one time, even after a respaw; having it unmarked will reappear the block after every respawn. "Blending" means that, if it is in contact with Foreground tiles, it will appear to be part of the wall. 
### Fake Walls
These entities appear to be solid walls from afar but have no solid hitbox. Once the player enters one, it will "disappear", revealing everything under it. It's not possible to stack Fake Walls, as the edge of the others will still show. If it is touching Foreground tiles, it will " merge" with the wall.
### Fake Blocks
Exactly the same as Fake Walls, except that it will not merge when in contact with Foreground tiles. Fake Walls are recommended over Fake Blocks in most instances.
### Cover-Up Walls
Exactly the same as Fake Walls, except that it will not disappear when the player enters one. Used very scarcely in the vanilla game.
### Crystal Hearts
The more serious collectibles. When the player touches it, they will bounce off and gives back dashes. Dashing into it or throwing a Theo Crystal at it will make it shatter, and the player will collect it after a short cutscene, after which the player is frozen in place and the Chapter's Crystal Heart Poem line appears on the screen. The player can still die during this collection cutscene, which will not count as having collected it. These Crystal Hearts, in the vanilla A sides, are usually very hidden or hard to reach. In the vanilla B and C sides, they are used as the chapter's end. The player can only collect one of them per side of a level, regardless of if there are more placed through the map. In the metadata menu, there is an option to make the collection of a Crystal Heart count as the chapter's end, similar to the Core or B/C sides. 
### Space Jam/Dream Blocks
These are the Blocks that appear all throughout Old Site/Summit 1000M. Although their outlines appear to be moving and flowing, their hitboxes are always the same. The player cannot walk through one, it can climb one, and it can dash into it, which makes the player go through in whichever direction they entered until they come out through the other side. The player can go through Foreground tiles in this state, but if they collide with a hitbox that kills, they will still die, and if where the player comes out, it finds Foreground tiles, the player will be "crushed" and die, but if they encounter another Space Jam while coming out of one, they will keep going. If the player holds the opposite direction they are going and hold grab, when they come out of the block, they will hold on to the edge of the block where they came out of, unless the block they went through ended in spikes or the block itself was one tile long, cases where the player will die or just keep going, respectively. The player can jump out of dream blocks, and they can also hyper out of them, which consumes the player's dash. It can also be noded, and, if so, the Dream Block will follow the node and move back and forth slowly. Marking "Fast moving" will make it move faster. Marking "One use" will make the Dream Block disappear after the player comes out of it, but since this disappearing lacks an animation, it is rarely used. Setting the inventory to OldSite will freeze the Dream Blocks when the chapter starts, state during which they can't be dashed through and don't move, and they will unfreeze when the player either activates a Dream Mirror or a custom trigger.
### Badeline Chasers
They have the same hitbox as the player and follow the player's movement 1.55 seconds, and if there are more than one, the others follow behind 0.4 seconds before the one in front. They ignore otherwise solid entities if they ever cross their paths. Where they are placed only determines where they appear at first but always move towards where the player started moving.
### Chaser Barriers
These rectangles make it so once a chaser enters through it, it will stop on its tracks, do a "laughing" animation, and disappear after a bit.
### Touch Switch
These Switches are activated by simply touching them or getting near enough. If you collect every single one in a screen, either a Switch Gate will activate or a Temple Gate open up. Both Seekers and Theo Crystals can activate these as well.
### Switch Gate
These gates move to their node once all Touch Switches have been collected, ignoring anything solid in their way. If set to "Persistent", all Touch Switches remain collected and the Switch Gate in its node, even after a respawn. It always moved to its node in n frames.
### Crystal Spinners/Dust Bunnies
These are one of the most common obstacles used, especially in from the Celestial Resort all the way to Farewell. They have a main, circular hitbox in the middle that's slightly smaller than the sprite, and a second, rectangular hitbox of 4 pixels of height and 8 of length, across the center. If 2 Spinners are set close enough, they will connect on their own and cover the space in between them with special Background sprites that has no hitbox. Their colors can vary, but all their hitboxes are the same, including Dust spinners. Optimal spinner placement is using the grid. It is often preferred that spinners never overlap unless necessary. If two spinners placed one above the other with grid alignment, the space between the two spinners is just enough (4 pixels) for a player to demodash between the two. If "Attach to solid" is marked, it will move with other moving entities if any. If there is a regular spinner and another next to it with attached marked, they will not connect.
### Water
Though its outline is dynamic, it has an even hitbox. While swimming, the player will ignore all gravity and any other kind of acceleration, all directional inputs having the same speed. If you dash while swimming, you'll immediately refill, even if you dash and edit the water, unless the water is one tile deep. There is no air gauge, so you can stay underwater indefinitely. It ignores gravity, so any water placed in the air will stay there.
### Spinning/Moving Blades/Dust Bunnies
They follow across a set path, whether it be circular or a straight line back and forth. Their hitbox is the same as that of a spinner, save that it lacks the second, rectangular hitbox altogether. If the center of a circular moving blade is inside of a moving entity, the spinning blade will move with it. Setting to "Dust" will only change its appearance.
### Keys
Once you collect one, it will remain with you unless you use it, even if you die. They serve no other purpose than open a Locked Door.
### Locked Doors
These doors can only be opened with a Key, once you get close enough. Once it's opened, it will remain that way, even if you die.
### Sinking Platforms
These platforms will begin to fall as soon as you stand on one. Jump or fall off and it will rise until it reaches its original position or until activated again.
### Moving Platforms
These platforms move back and forth between its original position and its node, within regular intervals. Standing on it will not change its speed, but it will make it sink around 2 pixels.
### Dust Floor
This floor or walls or ceiling will become deadly after the player has touched it. At first, it's regular floor, but if you walk across it, wherever you stood gets covered in, in this case, dust spikes. Just standing on it will not activate it, as it's not set under a timer.
### Clutter Blocks, Cabinets, Doors, and Switches
There are 3 types of clutter blocks, each one with its Clutter Switch. Clutter Blocks on their own serve to block off paths or form platforms. Once a Clutter Switch is activated, all the clutter blocks tied to it will collect, clearing anything it was blocking. Clutter Switch presses remain until the chapter ends or is reset. Clutter Cabinets are where all clutter blocks get sucked into once a Clutter Switch is activated. Clutter Doors are what is used to block the player off a path once a specific Clutter Switch has been activated. In the vanilla, Oshiro opens these up, but only opens the ones you haven't done yet.
### Oshiro Boss
Activated through a trigger, Oshiro spawns on the left side of the screen, and follows the player across the vertical axis. After a period of time (set), it will lock, and charge forwards. During this time, it has a hitbox that kills, but the player can jump on his head, which will immediately neutralize him, and will give a dash back. After it reaches the end of the screen either after a charge or a jump on top, it will reappear. It follows a pattern for how long it takes to lock and change. This pattern is: 1 second, 2 seconds, 3 seconds, 2 seconds, 3 seconds.
### Clouds and Fragile Clouds
The player can jump on these clouds, and if they press jump, they will get boosted even more. If they are fragile, they are pink, and a single bounce or jumping off will break it, giving dash back in both cases. Fragile Clouds reappear after 2.5 seconds.
### Boosters (Green/Red)
Often called bubbles because of their appearance, once the player enters one, after a delay of n frames or pressing dash, the player will boost forwards in whichever direction they were holding, around the distance of a regular dash (6 tiles), at a speed of n pps. During this state, the player can either jump off if directly touching the ground, wallbounce if touching a wall, break Dash Blocks, or (impossible in the vanilla, but possible with custom maps) activate Kevins or go through Dream Blocks. If set to Red, the bubble will keep going indefinitely instead of 6 tiles, and can even transition through screens, unless they die, hit an otherwise solid object, or dash out. Wind affects the trajectory of these boosters.
### Move Blocks
These blocks start moving in the direction their middle arrow states with a speed of n pps. They move at a constant speed. If "Fast Moving" is true, it'll be slightly faster than regular ones. If set to "Steerable", one or two of its side (those perpendicular to the arrow) can be grabbed or stood on and that way the player can somewhat direct the block (the player can move the block sideways while going up or down, or up and down when going sideways) by using the player's directional inputs. If they ever collide with anything, they have short moment (n frames) before they collapse. After they collapse, they regenerate at their original position after n seconds.
### Wind
Activated by triggers, it pushes the player in the opposite direction depending on the strength. There are 4 directions: right, left, up, and down. Left has 3 speeds (speeds go here), right has 4 speeds (speeds go here), up and down both have a single speed each (speed goes here).
### Swap Blocks
These blocks move from their original position to their node when the player uses their dash. It moves with a speed of 360 pps. It has a timeout after n seconds, and once it completes this timeout, it will return to its original position (regardless of if it reaches its node or not). Dashing again resets this timeout. If the node of a given swap block is too far away, it's possible that it times out before it reaches the node, meaning it won't reach it unless the player dashes again, resetting the timeout and giving it time to reach it.
### Dash Switches:
These switches activate once the player dashes into it, or is activated by a Theo Crystal. They open up the closest Temple Gate when activated.
### Temple Gates
These gates have different modes, all which act slightly different. Closebehind makes the Temple Gate close once the player is to the right of it, and remains closed even after respawns. Closebehindalways close the gate once the player is on the right side, but it opens on respawns. NearestSwitch opens when the nearest Dash Switch is activated. TouchSwitches opens when all Touch Switches have been collected (combined with Persistent, it will remain open even after respawns. HoldingTheo turns it yellowish and only opens if a Theo Crystal is near it, and it will close if the Theo Crystal is far from it, and it's usually used to prevent the player.to reach the end of a screen without the Theo Crystal (which the game really dislikes).
### Temple Cracked Blocks
These red blocks can only be broken if a Seeker dashes into it. If combined with Persistent, it will remain broken even if the player dies.
### Seekers
These monsters from the mirror, once they spot the player, they will lock in and charge in. It always charges in a straight line, but it can curve out of the player moves. If a charging Seeker collided with a Temple Cracked Block, this will break. Seekers can also collect Touch Switches. A Seeker will ignore the player of this is inside of a Seeker Barrier, which Seekers can't cross. The player can jump on top of these Seekers, which makes them fall some distance, and change appearance and become intangible for n seconds, and after that it returns to normal with a short shockwave which can break nearby Temple Cracked Blocks, propel Theo Crystals, and give a momentum boost to the player. It can only be killed by crushing it (but it respawns once the player does too). If it ever loses sight of the player, it will return to its original position.
### Seekers Barriers
These translucent barriers have a fluid outline but their hitboxes are even. If two or more Seeker Barriers are next to each other they will "merge". They serve no other practical purpose than to block of Seekers and create safe places for the player. If a Seeker is placed inside of a Seeker Barrier, it will remain immobile forever, but it can still be jumped on.
### Condition Blocks
These work in a way similar to Exit Blocks, but they only become solid once their condition is met. These conditions can be linked to keys, strawberries, or buttons. The way the condition is set up is `room name:entity id`, and once the game recognizes the specific type of entity with the specified id in the specified room is collected, it becomes solid. In order to prevent soflocks, it's recomended the Condition Block extends over the transition, so it's not already solid when the player transitions, but rather, is inside it, which prevents it from closing until the player exits its hitbox.
### Theo Crystals
The result of Theo entering the mirror, showing how he feels, frozen in place. Even though Theo is in it, it's as useless as before because the player has to carry it while holding grab and get them both to the end of the screen, because the game really dislikes having Theo on one screen and not on the next (game crashes). Theo is invulnerable to Seekers (which only lock on the player, but if not by one, it will bounce off), spikes and spinners while inside this Crystal, but if he falls offscreen or is crushed, he dies, which in turn kills the player as well. While holding the Crystal, the player loses the ability to climb up or hold on walls. Theo can also collect Touch Switches, press Dash Switches, and open HoldingTheo Temple Gates. 
### Starjump Blocks
Apart from looking cool, they sink a little if you stand on them. If two are touching each other, they will merge and lose the ability to fall down.
### Kevins/Crush Blocks
Even though the code calls them Crush Blocks, everyone calls them Kevin in honor to Kevin from PowerupAudio, which provided the sounds used when they activate. Kevins can have either one of the two axes of movement active or both. If the player dashes into one of Kevin's active axes, he will start moving into that direction indefinitely, breaking Dash Blocks and ignoring Spinners, until it collides with something solid (that if it is a Falling Block, this one will fall). Once it stops, it will attempt to return to its original position following the same path it took to get there. His movement, whether still.moving or returning can be interrupted by hitting another of his not already active "enabled" axes or sides, and it will move on that direction. If "Chillout" is marked, Kevin will start moving upon activation, but once it closes into the nearest solid object, it will start decelerating and will come to a stop, and will remain there; its movement cannot be interrupted. If a Chillout Kevin is longer than 6 tiles in any direction, the game considers it "giant" and becomes hardcoded to only move right, regardless if both axes are enabled.
### Feathers
Once the player touches it, they will enter a state where the player will stay in a continuous movement until it times out after n seconds or the player lands, grabs a wall, dashes out, or dies; touching another one resets the timer. After being collected, it reappears after 3 seconds. The feather is considered one of the hardest mechanics to control consistently (at least for players without much experience) because they take analog inputs for movement. Their movement is influenced by wind. If shielded, they become enclosed in a bubble, which the player can bounce on, which refills dash, or can dash against to break the shield, and grab the feather. If "One Use" is marked, it will not reappear once it's been used.
### Bumpers
The player can interact with them, which "bumps" the player in the opposite direction they hit it from. They move slightly left and right when idle. If a node is added, it'll move to and from its node periodically. If hit from the sides and one holds the direction they will be boosted into on the frame they interact, they will be boosted further. If the Core mode is none or Cold, it will act as default; if it's Hot, it will change its appearance and kill the player on contact.
### Badeline Boss
It places a Badeline Boss entity wherever the initial mode is set, and it will move to its nodes once the player hits her. Though it has a big hitbox, it will try to move slightly away from the player once they get close. While it moves from node to node, it can break Dash Blocks and can activate Falling Blocks set to Final Boss or Moving Blocks. Each node can have a different attack pattern. The attack pattern is as follows:
### Moving Block
These blocks move from their original position to their node and back upon being activated by a specific Badeline Boss node. They break once Badeline Boss is not again.
### Badeline Boost
This is the way Badeline helps out Madeline by literally giving her a boost. If placed individually, it will activate the "final boost", used to transition into the next checkpoint in the Summit vanilla chapters. If it's noded, it will move to the next node once the player activates the one previous to it. These boosts have a set distance, but it can be interrupted with a dash. Final Boosts boost Madeline upwards indefinitely until they either go through a screen transition or hit a Stop Boost trigger. "Lock Camera" makes it so the game will always keep it on the screen once it is in it.
### Summit Checkpoint
In essence, they are glorified mid-screen spawn point markers. Once the player is standing near it, it'll trigger a change of spawn point, so one needs to place spawn points near each one. Two Checkpoints can have the same number, but it has no purpose unless branching paths exist. The number set on their configuration window is what shows in-game. Challenges impossible to backtrack are recommended when using these.
### Wall Boosters
Attaching to walls, they are set in continuous movement upwards. The player can grab on to them, and they will rise even if they don't climb up. If Core mode is none or Hot, they act as default; if it's Cold, they will freeze over, which will make the wall it's covering impossible to hold on or climb. The player can still neutral on them, though.
### Bounce Blocks
Once the player grabs on or lands on top, it will retract a bit, and "bounce" towards where the player is in relation to its center, marked by the diamond center, giving a boost to the player only if they jump when it's "bouncing", and it will break after this. It will reform after 96 frames (1.6 seconds) unless the player is inside it when it is supposed to reform, in which case it will not reappear until the player exits where it reforms, after which it will reform immediately. If Core mode is none or Hot, it will work as default; if it's Cold, it will start falling very slowly and will collapse after n seconds, and it reforms after 96 frames (1.6 seconds).
### Fireballs
Literally, fireballs that kill the player on contact. If placed normally, it will remain immobile. If noded, it will follow all nodes at a regular speed, and it can cross Foreground tiles.  They have a regular circular hitbox that's slightly smaller than its sprite. Multiple fireballs can be set on the same track. If Core mode is none or Hot, they act as default; if it's Cold, they freeze over, making them Ice Balls, which gain a second horizontal hitbox. However, the player can jump on top of one, which in turn will make the Ice Ball break, making it disappear. Apart from the top, every other side still kills the player like normal.
### Core Mode Toggles
These double heart-shaped switches change the Core mode from Hot to Cold and/or vice versa. It can be set to only change to Cold, only change to Hot, or both. If it's set to only change to one, it'll disable if it is on that Core mode, even if set by another Switch. If set to both, it will be able to change between the two core modes back and forth, but it can only be used again after its 1 second cooldown has passed. All change the Core Mode immediately, changing all entities affected by Core mode. If "Persistent" is checked, deaths will not return the Core mode back to what it was originally, but rather stay the same.
### Fire Barriers
These barriers become active when the Core mode is Hot only. If the Core mode is none or changed to Cold, they completely disappear. They kill the player on all sides, but, due to the nature of walls in this game, the player can still perform wall jumps or even wallbounces (as long as they are around 1-3 pixels away from the block).
### Ice Blocks
Ice equivalent of a Fire Barrier. Only appears if Core mode is Cold, disappears in all other instances. They can be wall jumped and wallbounced off of as well.
### Rising Lava
If set to a screen, if the player is not inside a Lava blocker trigger (Everest inclusion), Lava will start rising from the bottom of the screen at a steady pace, which will kill the player on contact (though it's hitbox is slightly lower than the lava appears on screen). If the camera ever pans upwards, the lava will continue rising offscreen. If the screen pans sideways, the lava will move with the screen, as it's not programmed to scroll sideways. If Core mode is none or Hot, it acts as default; if set to Cold, the Lava will freeze over, but continue rising, except only at a slower rate. All screen of the Core in the vanilla game that uses this have a screen width of 40 tiles the default.
### Sandwich Lava
If set to a screen, Lava will appear on the bottom and the top of the screen. The top and the bottom will rise at the same pace as regular rising lava. If the Core mode is set to Cold, the lava will freeze over, and will start descending at a similar pace as rising Ice, but downwards. This basically forces the player to keep moving forward and activating the different Core mode Toggles to avoid the lava being too high or it've being too low and kill them. The camera can pan sideways without a problem, but if the camera land upwards, the lava/Ice will stick to the camera, as it's not programmed to scroll vertically. All screens of the Core in the vanilla game that use this have a screen height of 23 tiles, the default. 

## Other Entities:
* Intro Car
* Intro Crusher
* Bonfire
* Hanging Lamp
* (More to be added)

# Triggers:
### Light Fade
### Bloom Fade
### Camera Offset
### Camera Target
### Music
### Music Fade
### Change Respawn
### Respawn Target
### Event 
### Golden Berry Collection
### Lookout Blockers
### Oshiro (Spawn/Leave)
### Refill (Disabled/Enabled)
### Mini textbox
### Wind pattern
### Stop Boost
### Snowballs

## Other Triggers:
* Camera Advance Target
* Alt Music
* Ambience Param
* Checkpoint blocker
* Complete area
* Credits