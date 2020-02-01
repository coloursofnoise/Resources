# Table of contents

<div class="table-of-contents">

*   [Table of contents](#table-of-contents)
*   [Game mechanics](#game-mechanics)
    *   [Player (Spawn Point)](#player-spawn-point)
    *   [Jump Throughs](#jump-throughs)
    *   [Spikes](#spikes)
    *   [Strawberries](#strawberries)
    *   [Strawberry Blockfield](#strawberry-blockfield)
    *   [Golden Strawberries](#golden-strawberries)
    *   [Invisible Barriers](#invisible-barriers)
    *   [Springs](#springs)
    *   [Crumble Blocks](#crumble-blocks)
    *   [Falling Blocks](#falling-blocks)
    *   [Exit Blocks](#exit-blocks)
    *   [Zip Movers / Traffic Blocks](#zip-movers--traffic-blocks)
    *   [Refills](#refills)
    *   [Refills (Two Dashes)](#refills-two-dashes)
    *   [Cassette](#cassette)
    *   [Cassette Blocks](#cassette-blocks)
    *   [Dash Blocks](#dash-blocks)
    *   [Fake Walls](#fake-walls)
    *   [Fake Blocks](#fake-blocks)
    *   [Cover-Up Walls](#cover-up-walls)
    *   [Crystal Hearts](#crystal-hearts)
    *   [Space Jam/Dream Blocks](#space-jamdream-blocks)
    *   [Badeline Chasers](#badeline-chasers)
    *   [Chaser Barriers](#chaser-barriers)
    *   [Touch Switch](#touch-switch)
    *   [Switch Gate](#switch-gate)
    *   [Crystal Spinners/Dust Bunnies](#crystal-spinners-dust-bunnies)
    *   [Water](#water)
    *   [Spinning/Moving Blades/Dust Bunnies/Stars](#spinningmoving-bladesdust-bunniesstars)
    *   [Keys](#keys)
    *   [Locked Doors](#locked-doors)
    *   [Sinking Platforms](#sinking-platforms)
    *   [Moving Platforms](#moving-platforms)
    *   [Trigger Spikes / Dust](#trigger-spikes--dust)
    *   [Clutter Blocks, Cabinets, Doors, and Switches](#clutter-blocks-cabinets-doors-and-switches)
    *   [Oshiro Boss](#oshiro-boss)
    *   [Clouds and Fragile Clouds](#clouds-and-fragile-clouds)
    *   [Boosters (Green/Red)](#boosters-greenred)
    *   [Move Blocks](#move-blocks)
    *   [Wind](#wind)
    *   [Swap Blocks](#swap-blocks)
    *   [Dash Switches:](#dash-switches)
    *   [Temple Gates](#temple-gates)
    *   [Temple Cracked Blocks](#temple-cracked-blocks)
    *   [Seekers](#seekers)
    *   [Seeker Barriers](#seeker-barriers)
    *   [Condition Blocks](#condition-blocks)
    *   [Theo Crystals](#theo-crystals)
    *   [Starjump Blocks](#starjump-blocks)
    *   [Kevins/Crush Blocks](#kevinscrush-blocks)
    *   [Feathers](#feathers)
    *   [Bumpers](#bumpers)
    *   [Badeline Boss](#badeline-boss)
    *   [Moving Block](#moving-block)
    *   [Badeline Boost](#badeline-boost)
    *   [Summit Checkpoint](#summit-checkpoint)
    *   [Wall Boosters / Ice Walls](#wall-boosters--ice-walls)
    *   [Bounce Blocks](#bounce-blocks)
    *   [Fireballs / Ice Balls](#fireballs--ice-balls)
    *   [Core Mode Toggles](#core-mode-toggles)
    *   [Fire Barriers](#fire-barriers)
    *   [Ice Blocks](#ice-blocks)
    *   [Rising Lava/Ice](#rising-lavaice)
    *   [Sandwich Lava/Ice](#sandwich-lava-ice)
    *   [Other Entities:](#other-entities)
*   [Triggers:](#triggers)
    *   [Light Fade](#light-fade)
    *   [Bloom Fade](#bloom-fade)
    *   [Camera Offset](#camera-offset)
    *   [Camera Target](#camera-target)
    *   [Music](#music)
    *   [Music Fade](#music-fade)
    *   [Change Respawn](#change-respawn)
    *   [Respawn Target](#respawn-target)
    *   [Event](#event)
    *   [Golden Berry Collection](#golden-berry-collection)
    *   [Lookout Blockers](#lookout-blockers)
    *   [Oshiro (Spawn/Leave)](#oshiro-spawnleave)
    *   [Refill (Disabled/Enabled)](#refill-disabledenabled)
    *   [Mini textbox](#mini-textbox)
    *   [Wind pattern](#wind-pattern)
    *   [Stop Boost](#stop-boost)
    *   [Snowballs](#snowballs)
    *   [Other Triggers:](#other-triggers)

</div>

# Game mechanics

### Player (Spawn Point)

These entities define where the player will respawn if they die. Upon a screen transition, the game will choose the one closest to the player to be the spawn point.

Change Respawn triggers will change the spawn point to the nearest Player object to the trigger's center, or the nearest one to the trigger's node if one exists. Respawn Target will act the same as a Change Respawn trigger with a node, but will only activate if the player is transitioning.

The current spawn point will not automatically update without a transition or trigger, even if the player passes through a Player object. The game will not let the player enter a room if it does not have a Player object inside of it.

### Jump Throughs

These platforms found throughout the game enable the player to cross through its bottom and land on top safely. Used commonly for upwards screen transitions, aerial spikes, and one-way passages. If the player is crushed against it by a moving solid (like a Kevin or Falling Block), the player will fall through instead of dying. You can also clip through them if landing on them with a feather on the same frame you exit the feather state.

### Spikes

One of the most common obstacles in the game. Used for covering otherwise safe ground or walls. Their hitboxes extend 3 pixels from the base, meaning the tips don't kill the player. If you are moving in the same direction the spikes are facing, they will not kill you either. Despite them having different sprites for different chapters, their hitboxes are all the same. They attach to moving entities.

### Strawberries

Your regular fun but useless collectibles. If winged, it flies upward on dash, but it can still be collected while it is flying away. After grabbing a strawberry, you have to land on "safe ground" (FG tiles, most stationary solid objects, or water) for at least 9 frames to collect it.

If you add nodes to them, strawberry seeds will appear. If you touch the ground for more than 9 frames, or jump or dash while on the ground, you will lose any seeds you are carrying. (You can, however, touch the ground and then walk off within 9 frames to keep them.) If all seeds are collected together, the strawberry itself will appear, and remain until collected, even if the player dies.

### Strawberry Blockfield

If the player is touching one of these, they will not collect any strawberries, even if they are standing on otherwise safe ground.

### Golden Strawberries

These work almost the same as strawberries in the sense of being useless collectibles. However, these ones are usually located above the player when the chapter starts (given they have previously cleared it at least once before), and can only be collected with a Golden Strawberry Collection trigger, usually found at the end of a level. If the player dies with one, they will be returned to where the strawberry was collected, resetting the level timer if it was placed in the first room.

If Winged, it will try to fly away when the player dashes, like regular strawberries. If it's Winged No Dash, the golden strawberry will only spawn if the player hasn't dashed at all during the entire level. If used, it's typically found at the end of a level, like in vanilla Forsaken City A.

### Invisible Barriers

Just what they sound like: they block the player, as they are solid, but they are invisible. Often used in vanilla just offscreen to block off backtracking (such as in the Badeline fight). They are also used to prevent unintended routes, such as blocking the player from using a demodash to skip the "Search" checkpoint of Mirror Temple and get to Theo early.

### Springs

When the player interacts with these, they lose all momentum they previously had and bounce with a set speed and direction. The bounce can be interrupted with a dash and is slightly influenced by the player's directional inputs. They attach to moving entities.

### Crumble Blocks

These platforms begin to crumble as soon as you interact with them (whether landing or grabbing). If you land on them, they disappear after 0.6 seconds (36 frames) or immediately after jumping, dashing, or sliding off. If you grab its side, it will always disappear after a timeout of 1 second, time during which you can still jump on or off it. They regenerate after 2 seconds.

### Falling Blocks

These blocks, as their name implies, fall upon interaction. If you land on top or hold on to its side, it falls after 0.6 seconds (36 frames), and if you let go or fall off, it falls immediately with a speed of 160 pps. They can break Dash Blocks, and keep falling until offscreen, or until they collide with Foreground tiles or other solid entities. If what they landed on moves or falls from under them, they will continue falling. One can also disable "climb fall" so that it can only by activated from the top or other entities such as Kevins. It can also be used for Badeline Boss, where they fall only after Badeline is hit in a specified node.

### Exit Blocks

These entities become solid if the player is not inside of its hitbox. Commonly used to block off backtracking.

### Zip Movers / Traffic Blocks

These move from their original position to wherever their node is set, marked visually by the zip line, ignoring everything on their way, even Foreground tiles. When activated by grabbing or landing on top, they always take the same time to reach their node (0.5 seconds/30 frames), regardless of the distance; the farther the node is, the faster it'll go. After it reaches its node, there are 0.5 seconds/30 frames of cooldown before it returns to its original position in 2 seconds. It will only move again after it has returned to its original position, after 0.5 seconds/30 frames of cooldown.

### Refills

These crystals refill the player's dash and stamina. If you run out of stamina while still having your dash and touch one, you'll use it, and refill only your stamina. If you dash through one or touch it after having dashed, you'll refill stamina and dash. If you have two dashes, only using one dash will still consume the refill, and using both dashes will refill both dashes, unless the second dash is a temporary one from a two-dash refill. Marking "One use" will make it not reappear after being used until a respawn or a screen transition. They respawn after 2.5 seconds.

### Refills (Two Dashes)

These act very similar to regular refill crystals, but they will give you a temporary second dash if the player only has one maximum dash. If the player has two maximum dashes, they act identically to regular refills.

### Cassette

These entities are what is used to gate a B side of a level. Upon collection, the game will stop, play a cutscene, and then move the player through the nodes until it reaches the last one, where the bubble pops, and the player is free to move. Collecting it will disable all cassette blocks from alternating.

### Cassette Blocks

These blocks pop in and out of the background into solid blocks to the tempo of the music. Any entity attached to it will appear and disappear with the block. There are 4 colors available. The order for appearance is Pink, Blue, Bright Sun, and Malachite. Any spikes attached to them will become the color of the block they are attached to. If two blocks of the same color are next to each other, their appearances and hitboxes will "merge". If the player jumps off of a Cassette Block as it pops in, they will jump even higher than normal.

### Dash Blocks

Blocks that break with a dash or other special conditions. The entities or conditions that can break one are: a player's dash, moving Kevin blocks, falling Falling Blocks, or the player whilst inside of a Booster of either color.

If "Can Dash" is disabled, the player's dash can't break the block anymore, but everything else can. Marking "Permanent" means that the block will remain broken once destroyed, even after a respawn; having it unmarked will make the block reappear after every respawn. "Blending" means that, if it is in contact with Foreground tiles, it will appear to be part of the wall.

### Fake Walls

These entities appear to be solid walls from afar but have no solid hitbox. Once the player enters one, it will disappear, revealing everything under it. It's not possible to stack Fake Walls, as the edge of the others will still show. If it is touching Foreground tiles, it will "merge" with the wall.

### Fake Blocks

Exactly the same as Fake Walls, except that it will not merge when in contact with Foreground tiles. Fake Walls are recommended over Fake Blocks in most instances.

### Cover-Up Walls

Exactly the same as Fake Walls, except that it will not disappear when the player enters one. Used very scarcely in the vanilla game.

### Crystal Hearts

The more serious collectibles. When the player touches it, they will bounce off and gives back dashes. Dashing into it or throwing a Theo Crystal at it will make it shatter, and the player will collect it after a short cutscene, after which the player is frozen in place and the Chapter's Crystal Heart Poem line appears on the screen. The player can still die during this collection cutscene, which will not count as having collected it.

In the vanilla A-sides, Crystal Hearts are usually very hidden or hard to reach. In the vanilla B- and C-sides as well as Core, they are used as the chapter's end. The player can only collect one of them per side of a level, regardless of if there are more placed through the map. In the metadata menu, there is an option to make the collection of a Crystal Heart count as the chapter's end, similar to the Core or B/C-sides.

### Space Jam/Dream Blocks

These are the Blocks that appear all throughout Old Site/Summit 1000M. Although their outlines appear to be moving and flowing, their hitboxes are always the same. They are solid, so the player can climb on and walk on them. When the player dashes into it, they go through in whichever direction they entered until they come out through the other side. The player can go through Foreground tiles in this state, but if they collide with a hitbox that kills, they will still die, and if there are solid tiles where the player comes out, they will be "crushed" and die (unless it's another dream block, in which case they will keep going).

If the player holds the opposite direction they are going and hold grab, when they come out of the block, they will hold onto it (assuming there aren't spikes on the other side), unless it is only one tile wide and the player was dashing horizontally, in which case they will not grab. The player can jump out of dream blocks, and they can also hyper out of them, which consumes the player's dash.

Dream Blocks can be noded, and, if so, the Dream Block will follow the node and move back and forth slowly. Marking "Fast moving" will make it move faster. Marking "One use" will make the Dream Block disappear after the player comes out of it, but since this disappearing lacks an animation, it is rarely used. Setting the inventory to OldSite will freeze the Dream Blocks when the chapter starts, state during which they can't be dashed through and don't move. They will unfreeze when the player activates a Dream Mirror or a trigger that changes the player's inventory.

### Badeline Chasers

They have the same hitbox as the player and follow the player's movement 1.55 seconds behind. If there are more than one, the others follow behind 0.4 seconds before the one in front of it. They ignore otherwise solid entities if they ever cross their paths. Where they are placed only determines where they appear at first; they always move towards where the player started moving.

### Chaser Barriers

These rectangles make it so once a chaser enters through it, it will stop on its tracks, do a "laughing" animation, and disappear after a bit.

### Touch Switch

These Switches are activated by simply touching them or getting near enough. If you collect every single one in a screen, either a Switch Gate will activate or a Temple Gate open up. Seekers and Theo Crystals can activate these as well.

### Switch Gate

These gates move to their node once all Touch Switches have been collected, ignoring anything solid in their way. If set to "Persistent", all Touch Switches remain collected and the Switch Gate in its node, even after a respawn. It always moves to its node in 2 seconds/120 frames.

### Crystal Spinners/Dust Bunnies

These are one of the most common obstacles used, especially from Celestial Resort through Farewell. Their hitboxes look like [this](https://cdn.discordapp.com/attachments/525939879805190154/645421703803174929/unknown.png): they have a main, circular hitbox in the middle that's slightly smaller than the sprite, and a second, rectangular hitbox of 4 pixels of height and 16 of length, across the center.

If 2 Spinners are set close enough, they will connect visually by covering the space between them with special Background sprites which have no hitbox. Their colors can vary, but all their hitboxes are the same, including Dust spinners. Optimal spinner placement is using the grid. It is often preferred that spinners never overlap unless necessary.

If two spinners placed one above the other with grid alignment, the space between the two spinners is just enough (4 pixels) for a player to demodash between the two. If "Attach to solid" is marked, it will move with other moving entities if any. If there is a regular spinner and another next to it with attached marked, they will not connect.

### Water

Though its outline is dynamic, it has an even hitbox. While swimming, the player will ignore all gravity and any other kind of acceleration, all directional inputs having the same speed. If you dash while swimming, you'll immediately refill, even if you dash and exit the water, unless the water is one tile deep. There is no air gauge, so you can stay underwater indefinitely. It ignores gravity, so any water placed in the air will stay there.

### Spinning/Moving Blades/Dust Bunnies/Stars

They follow across a set path, whether it be circular or a straight line back and forth. Their hitbox is the same as that of a spinner, except circular ones lack the second rectangular hitbox. If the center of a circular moving blade is inside of a moving entity, the spinning blade will move with it. Setting to "Dust" or "Star" will only change its appearance.

### Keys

Once you collect one, it will remain with you unless you use it, even if you die. They serve no other purpose than open a Locked Door.

### Locked Doors

These doors can only be opened with a Key, once you get close enough. Once it's opened, it will remain that way, even if you die.

### Sinking Platforms

These platforms will begin to fall as soon as you stand on one. Jump or fall off and it will rise until it reaches its original position or until activated again. If you land and immediately jump off of one while it is rising, you will gain extra vertical momentum.

### Moving Platforms

These platforms move back and forth between its original position and its node, within regular intervals. Standing on it will not change its speed, but it will make it sink around 2 pixels.

### Trigger Spikes / Dust

A surface covered with trigger spikes will become deadly after the player has touched it. At first, it's harmless, but if the player touches it, it gets covered in spikes or dust once the player leaves its hitbox. It is safe as long as the player is standing inside of it, however, since it is not on a timer.

### Clutter Blocks, Cabinets, Doors, and Switches

There are 3 types of clutter blocks, each one with its Clutter Switch. Clutter Blocks on their own serve to block off paths or form platforms.

Once a Clutter Switch is activated, all the clutter blocks tied to it will collect, clearing anything it was blocking. Clutter Switch presses remain until the chapter ends or is reset.

Clutter Cabinets are where all clutter blocks get sucked into once a Clutter Switch is activated.

Clutter Doors are what is used to block the player off a path once a specific Clutter Switch has been activated. In the vanilla, Oshiro opens these up, but only opens the ones you haven't done yet.

### Oshiro Boss

Activated through a trigger, Oshiro spawns on the left side of the screen, and follows the player across the vertical axis. After a period of time (set), it will lock, and charge forwards. During this time, it has a hitbox that kills, but the player can jump on his head, which will immediately neutralize him, and will give a dash back. After it goes offscreen, either after a charge or a jump on top, it will reappear.

In A-sides, there is a pattern for how long it takes to lock and charge after respawning: 1 second, 2 seconds, 3 seconds, 2 seconds, 3 seconds. In B-sides and C-sides, it is always 1 second.

### Clouds and Fragile Clouds

The player can jump on these clouds, and if they press jump, they will get boosted even more. If they are fragile, they are pink, and a single bounce or jumping off will break it, giving dash back in both cases. Fragile Clouds reappear after 2.5 seconds. Regular clouds have a hitbox that is 32 pixels wide; small ones have a hitbox of 26 pixels.

### Boosters (Green/Red)

Often called bubbles because of their appearance, once the player enters one, after a delay of 15 frames or pressing dash, the player will boost forwards in whichever direction they were holding, around the distance of a regular dash (6 tiles), at a speed of 240 pps. During this state, the player can either jump off if directly touching the ground, wallbounce if touching a wall, break Dash Blocks, or (impossible in vanilla, but possible with custom maps) activate Kevins or go through Dream Blocks.

If set to Red, the bubble will keep going indefinitely instead of breaking after 6 tiles, and can even transition through screens, unless the player dies, hits an otherwise solid object, or dashes out. Wind affects the trajectory of these boosters.

### Move Blocks

These blocks start moving in the direction their middle arrow states with a speed of 60 pps. They move at a constant speed. If "Fast Moving" is true, they will instead move at 75 pps. If set to "Steerable", one or two of its sides (those perpendicular to the arrow) can be grabbed or stood on and that way the player can somewhat direct the block (the player can move the block sideways while going up or down, or up and down when going sideways) by using the player's directional inputs.

If it hits a solid object, the player has 9 frames to steer it away in order to keep it going; otherwise, it will collapse after 12 frames. After they collapse, they regenerate at their original position after 3 seconds.

### Wind

Activated by triggers, it pushes the player in the opposite direction depending on the strength. There are 4 directions: right, left, up, and down.

*   **Left:** Normal: 40 pps, Strong: 80 pps

*   **Right:** Normal: 40 pps, Strong: 80 pps, Crazy: 120 pps

*   **Up:** Normal: 40 pps, Space: 60 pps

*   **Down:** Normal: 30 pps

*   **OnOff:** always uses 80 pps (strong). Normal switches every 3 seconds, Fast switches every 2 seconds.

*   **Alternating:** always uses 40 pps (normal). 3 seconds of left wind, 2 seconds of no wind, 3 seconds of right wind, 2 seconds of no wind, repeat.

*   **LeftGemsOnly:** blows left at 40 pps (normal) if the player is holding strawberry seeds

### Swap Blocks

These blocks move from their original position to their node when the player uses their dash. It moves with a speed of 360 pps. It has a timeout of 0.8 seconds, and once it completes this timeout, it will return to its original position (regardless of if it reaches its node or not). Dashing again resets this timeout. If the node of a given swap block is too far away, it's possible that it times out before it reaches the node, meaning it won't reach it unless the player dashes again, resetting the timeout and giving the block time to reach it.

### Dash Switches:

These switches activate once the player dashes into it, or is activated by a Theo Crystal. They open up the nearest closed Temple Gate when activated.

### Temple Gates

These gates have different modes, all which act slightly different. Closebehind makes the Temple Gate close once the player is to the right of it, and remains closed even after respawns. Closebehindalways close the gate once the player is on the right side, but it opens on respawns. NearestSwitch opens when the nearest Dash Switch is activated. TouchSwitches opens when all Touch Switches have been collected (combined with Persistent, it will remain open even after respawns). HoldingTheo turns it yellowish and only opens if a Theo Crystal is near it, and it will close if the Theo Crystal is far from it, which is usually used to prevent the player from reaching the end of a screen without the Theo Crystal (which the game really dislikes).

### Temple Cracked Blocks

These red blocks can only be broken if a Seeker dashes into it. If combined with Persistent, it will remain broken even if the player dies.

### Seekers

The monsters from the mirror. Once they spot the player, they will lock in and charge in. It usually charges in a straight line, but it can curve out if the player moves. If a charging Seeker collides with a Temple Cracked Block, it will break. Seekers can also collect Touch Switches. A Seeker will ignore the player if it is inside of a Seeker Barrier, which Seekers can't cross.

The player can jump on top of these Seekers, which makes them fall some distance, change appearance and become intangible for about 2.65 seconds, after which it returns to normal with a short shockwave which can break nearby Temple Cracked Blocks, propel Theo Crystals, and give a momentum boost to the player. It can be killed by crushing it (but it respawns if the player dies or leaves the screen). If it ever loses sight of the player, it will return to its original position.

### Seeker Barriers

These translucent barriers have a fluid outline but their hitboxes are even. If two or more Seeker Barriers are next to each other they will "merge". As it blocks Seekers from moving through them, it creates safe places for the player. If a Seeker is placed inside of a Seeker Barrier, it will be completely immobile, but it can still be jumped on. Seeker Barriers also cause Jellyfish to disintegrate upon touching it.

### Condition Blocks

These work in a way similar to Exit Blocks, but they only become solid once their condition is met. These conditions can be linked to keys, strawberries, or buttons. The way the condition is set up is `room name:entity id`, and once the game recognizes the specific type of entity with the specified id in the specified room is collected, it becomes solid. In order to prevent softlocks, it's recommended the Condition Block extends over the transition, so it's not already solid when the player transitions, but rather, is inside it, which prevents it from closing until the player exits its hitbox.

### Theo Crystals

The result of Theo entering the mirror, showing how he feels, frozen in place. The player must carry the crystal to the end of the room in order to proceed. Theo is invulnerable to Seekers (which will merely bounce off), spikes and spinners while inside this Crystal. However, if he falls offscreen or is crushed, he dies, which in turn kills the player as well. While holding the Crystal, the player loses the ability to climb up or hold on walls. Theo can also collect Touch Switches, press Dash Switches, and open HoldingTheo Temple Gates.

### Starjump Blocks

Apart from looking cool, they sink a little if you stand on them, unless "Sinks" is set to false. If two are touching each other, they will merge visually, but will still move separately. Overlapping blocks can result in the game crashing. If a Star Climb Controller is present, they will gain a light blue visual effect inside.

### Kevins/Crush Blocks

Even though the code calls them Crush Blocks, everyone calls them Kevin in honor to Kevin from PowerupAudio, which provided the sounds used when they activate. Kevins can have one or both of the two axes of movement active. If the player dashes into one of Kevin's active axes, he will start moving in that direction at 240 pps indefinitely, breaking Dash Blocks and ignoring Spinners, until it collides with something solid. If the Kevin collides with a Falling Block, it will fall. Once it stops, it will attempt to return to its original position following the same path it took to get there. His movement can be interrupted at any point by hitting another of his not already active "enabled" axes or sides, and it will move on that direction.

If "Chillout" is marked, Kevin will start moving upon activation, but once it closes into the nearest solid object, it will start decelerating and will come to a stop, and will remain there; its movement cannot be interrupted. If a Chillout Kevin is longer than 6 tiles in any direction, the game considers it "giant" and becomes hardcoded to only move right, regardless of whether both axes are enabled.

### Feathers

Once the player touches it, they will enter a state where the player will stay in continuous movement until it times out after 2 seconds or the player lands, grabs a wall, dashes out, or dies; touching another one resets the timer. After being collected, it reappears after 3 seconds. The feather is considered one of the hardest mechanics to control consistently (at least for players without much experience) because they take analog inputs for movement. Their movement is influenced by wind.

If shielded, they become enclosed in a bubble, which the player can bounce on, which refills dash, or can dash against to break the shield, and grab the feather. If "One Use" is marked, it will not reappear once it's been used.

### Bumpers

The player can interact with them, which "bumps" the player in the opposite direction they hit it from. They move slightly left and right when idle. If a node is added, it'll move to and from its node periodically. If hit from the sides and one holds the direction they will be boosted into on the frame they interact, they will be boosted further. If the Core mode is none or Cold, it will act as default; if it's Hot, it will change its appearance and kill the player on contact.

### Badeline Boss

It places a Badeline Boss entity wherever the initial mode is set, and it will move to its nodes once the player hits her. Though it has a big hitbox, it will try to move slightly away from the player once they get close. While it moves from node to node, it can break Dash Blocks and can activate Falling Blocks set to Final Boss or Moving Blocks. Each node can have a different attack pattern. The attack pattern is as follows: [todo]

### Moving Block

These blocks move from their original position to their node and back upon being activated by a specific Badeline Boss node. They break once Badeline Boss is hit again.

### Badeline Boost

This is the way Badeline helps out Madeline by literally giving her a boost. If placed individually, it will activate the "final boost", used to transition into the next checkpoint in the Summit vanilla chapters. If it's noded, it will move to the next node once the player activates the one previous to it. These boosts have a set distance, but it can be interrupted with a dash. Final Boosts boost Madeline upwards indefinitely until they either go through a screen transition or hit a Stop Boost trigger. "Lock Camera" makes it so the game will always keep it on the screen once it is in it.

### Summit Checkpoint

In essence, they are glorified mid-screen spawn point markers. Once the player is standing near it, it'll trigger a change of spawn point, so one needs to place spawn points near each one. Two Checkpoints can have the same number, but it has no purpose unless branching paths exist. The number set on their configuration window is what shows in-game. It is recommended to only use these when it is not possible to backtrack, since they can only be activated once.

### Wall Boosters / Ice Walls

When the Core mode is None or Hot, they will act as upward conveyors that automatically move the player up while they are grabbing it.

When the Core mode is set to Cold, or the entity has "Not Core Mode" set, it will act as an icy wall that the player cannot grab onto or climb jump off of (though they can still neutral jump off of it).

### Bounce Blocks

If the Core mode is None or Hot, when the player grabs on or lands on top, it will retract a bit, and "bounce" towards where the player is in relation to its center, marked by the diamond center, giving a boost to the player only if they jump when it's "bouncing", and it will break after this. It will reform after 96 frames (1.6 seconds) unless the player is inside it when it is supposed to reform, in which case it will not reappear until the player exits where it reforms, after which it will reform immediately.

If the core mode is Cold, it will instead start sinking very slowly for about 1.25 seconds before collapsing, and it reforms after 96 frames (1.6 seconds).

### Fireballs / Ice Balls

If the Core mode is Hot or None, they are fireballs that kill the player on contact. If placed normally, it will remain immobile. If noded, it will follow all nodes at a regular speed, and it can cross Foreground tiles. They have a regular circular hitbox that's slightly smaller than its sprite. Multiple fireballs can be set on the same track.

If the Core mode is Cold, or "Not Core Mode" is set, they freeze over, making them Ice Balls, which gain a second horizontal hitbox. Now, the player can jump on top of one, which in turn will make the Ice Ball break, making it disappear. Apart from the top, every other side still kills the player like normal.

### Core Mode Toggles

These double heart-shaped switches change the Core mode from Hot to Cold and/or vice versa. It can be set to only change to Cold, only change to Hot, or both. If it's set to only change to one, it'll disable if it is on that Core mode, even if set by another Switch. If set to both, it will be able to change between the two core modes back and forth, but it can only be used again after its 1 second cooldown has passed. All change the Core Mode immediately, changing all entities affected by Core mode. If "Persistent" is checked, deaths will not return the Core mode back to what it was originally, but rather stay the same.

### Fire Barriers

These barriers become active when the Core mode is Hot only. If the Core mode is none or changed to Cold, they completely disappear. They kill the player on all sides, but they have a solid hitbox inside of their killbox, meaning the player can perform wall jumps or even wallbounces off of it (as long as they are around 1-3 pixels away from the block).

### Ice Blocks

Ice equivalent of a Fire Barrier. Only appears if Core mode is Cold, disappears in all other instances. They can be wall jumped and wallbounced off of as well.

### Rising Lava/Ice

If put in a screen, if the player is not inside a Lava blocker trigger (Everest inclusion), Lava will start rising from the bottom of the screen at a steady pace, which will kill the player on contact (though its hitbox is slightly lower than the lava appears on screen). If the Core mode is set to Ice, it will become ice instead, but otherwise function identically.

If the camera ever pans upwards, the lava will continue rising offscreen. If the screen pans sideways, the lava will move with the screen, as it's not programmed to scroll sideways. All screen of the Core in the vanilla game that uses this have a screen width of 40 tiles, the default.

### Sandwich Lava/Ice

If set to a screen, Lava will appear on the bottom and the top of the screen. The top and the bottom will rise at the same pace as regular rising lava. If the Core mode is set to Cold, the lava will freeze over, and will start descending at a similar pace as rising Ice, but downwards. This basically forces the player to keep moving forward and activating the different Core mode Toggles to avoid the lava rising too high or ice sinking too low.

The camera can pan sideways without a problem, but if the camera pans upwards, the lava/ice will stick to the camera, as it's not programmed to scroll vertically. All screens of the Core in the vanilla game that use this have a screen height of 23 tiles, the default.

## Other Entities:

*   Intro Car
*   Intro Crusher
*   Bonfire
*   Hanging Lamp
*   (More to be added)

# Triggers:

### Light Fade

These triggers will make exactly what their name implies: make the light fade. When setting it up, Light Fade from indicates what level of light fade to force when entering the trigger, and Light Fade to indicates the level when exiting the trigger. Both are based on values from 0 to 1 (including decimals), 0 being full light, and 1 being full darkness. The position mode determines in which order to take the information it's given, meaning that if the position is set backwards relative to how the trigger will be used, it will work incorrectly.

### Bloom Fade

Works the same as Light Fades, but they affect the Bloom instead of the Light.

### Camera Offset

This trigger forces the camera to move a certain amount of space specified, moving it away from the player being in the center. Camera X moves the camera in the X axis and Camera Y in the Y axis. The values can be any number, including decimals or negatives. The ratio of camera movement per value is 1 tile offset per 0.25 value, meaning a value of 1 will move the camera 4 tiles. The camera won't move past a screen's edges. This offset will remain after you exit the trigger until the player dies or transitions.

### Camera Target

This trigger will move the camera towards the top left corner of the node. Lerp strength determines how much the camera will move towards the node, so if it's set to 0, it won't move. It depends on a position mode to work as well. Marking X only or Y only will make the camera only move in the axes marked. The camera offset resets upon leaving the trigger.

### Music

Used to change the music of a screen. If a screen already has music to it (set from the room configuration window), it will change while you're inside it,

### Music Fade

Works the same as a Light Fade, except they affect the music volume instead. Resets if the player dies.

### Change Respawn

Sets the player's spawn point to the closest Player object to the center of the trigger, or the object closest to the node if there is one.

### Respawn Target

Acts like a Change Respawn with a node, but only when the player is transitioning.

### Event

Used for certain vanilla cutscenes.

### Golden Berry Collection

Causes any Golden Berries the player is holding to collect.

### Lookout Blockers

Prevents Watchtowers from scrolling past it.

### Oshiro (Spawn/Leave)

If "State" is set to true, causes an Oshiro Boss to spawn. Otherwise, it will cause an existing Oshiro Boss to leave after it finishes its current charge. If multiple Oshiro Bosses exist, only one will leave.

### Refill (Disabled/Enabled)

If "State" is set to true, touching it will disable the player regaining their dash upon touching ground. Otherwise, it disables this effect.

### Mini textbox

Causes a small text box with the specified dialog ID to appear at the top of the screen. If "Death Count" is set to -1, it will always display; otherwise, it will only play if the player has died the specified number of times in the current room.

"Mode" will determine the conditions for showing the text box: OnPlayerEnter will trigger if the player touches it, OnLevelStart will trigger immediately upon entering the room, and OnTheoEnter will trigger if a Theo Crystal touches it. "Only Once" will make the text box only display once per level; otherwise, it can trigger every time the player dies or the room is entered.

### Wind pattern

These triggers activate whichever wind pattern they have set when the player enters it.

### Stop Boost

These triggers will stop the player from moving upwards after using a final node of a Badeline boost. If the player doesn't screen transition or hit this trigger, she will continue to rise and get stuck offscreen or below anything solid, forcing the player to retry.

### Snowballs

Entering it will either make Snowballs start appearing at regular intervals or stop appearing at all, depending on what it's set to do.

## Other Triggers:

*   Camera Advance Target
*   Alt Music
*   Ambience Param
*   Checkpoint blocker
*   Complete area
*   Credits