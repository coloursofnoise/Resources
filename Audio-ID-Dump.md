## All sounds currently in the game.
`Audio.Play("soundID");` to play a sound.  
`Audio.SetParameter(EventInstance instance, string param, float value);` where instance is the return value of `Play()` to set or change a parameter.  
`Audio.Stop(EventInstance instance, bool allowFadeout = true);` to stop playing the sound.


## Sound Banks:
<details>
<summary>Master</summary>
<pre>
event:/game/04_cliffside/whiteblock_fallthru
event:/ui/world_map/whoosh/1000ms_back
event:/ui/world_map/whoosh/1000ms_forward
event:/ui/world_map/whoosh/400ms_back
event:/ui/world_map/whoosh/400ms_forward
event:/ui/world_map/whoosh/600ms_back
event:/ui/world_map/whoosh/600ms_forward
event:/ui/world_map/whoosh/700ms_back
event:/ui/world_map/whoosh/700ms_forward
event:/ui/world_map/whoosh/900ms_back
event:/ui/world_map/whoosh/900ms_forward
snapshot:/assist_game_speed/assist_speed_50
snapshot:/assist_game_speed/assist_speed_60
snapshot:/assist_game_speed/assist_speed_70
snapshot:/assist_game_speed/assist_speed_80
snapshot:/assist_game_speed/assist_speed_90
snapshot:/berry_cooperation/1000s_down
snapshot:/berry_cooperation/2000s_down
snapshot:/berry_cooperation/3000s_down
snapshot:/berry_cooperation/4000s_down
snapshot:/berry_cooperation/5000s_down
snapshot:/boss_pitch_sfx
snapshot:/char_granny_laughs_down
snapshot:/dialogue_in_progress
snapshot:/env_allamb_down
snapshot:/env_worldmap_down
snapshot:/game_00_prologue_amb_down
snapshot:/game_00_prologue_amb_off
snapshot:/game_00_verb
snapshot:/game_01_birdbros_finish
snapshot:/game_02_dreammemorial_fade
snapshot:/game_03_clutterswitch_moment
snapshot:/game_03_oshirofreakout
snapshot:/game_03_pico8room
snapshot:/game_04_gondolafeather_main
snapshot:/game_04_gondolafeather_verb
snapshot:/game_05_eyedeath
snapshot:/game_05_eyedistance
snapshot:/game_05_mus_pulse_controller
snapshot:/game_05_torch_arp
snapshot:/game_10_BIR_music_part01
snapshot:/game_10_BIR_music_part02
snapshot:/game_10_BIR_sfx
snapshot:/game_10_BIRd_wings_silenced
snapshot:/game_10_amb_voidspiral_active
snapshot:/game_10_cafe_computer_active
snapshot:/game_10_final_boost
snapshot:/game_10_glitch_active
snapshot:/game_10_golden_room_flavour
snapshot:/game_10_goldenroom_death_fix
snapshot:/game_10_granny_clouds_dialogue
snapshot:/game_10_in_space
snapshot:/game_10_inside_cafe
snapshot:/game_10_kevinpc_sendcontrol
snapshot:/game_10_kevinpc_verbtransition
snapshot:/game_gen_crystalheart
snapshot:/game_gen_large_berry_get
snapshot:/mus_cassette_amb_down
snapshot:/mus_lvl1_verbtransition
snapshot:/music_all_mute
snapshot:/music_mains_mute
snapshot:/music_reflection_secret
snapshot:/music_secretrevealed
snapshot:/pause_menu
snapshot:/underwater
snapshot:/variant_speed/variant_speed_120
snapshot:/variant_speed/variant_speed_140
snapshot:/variant_speed/variant_speed_160
</pre>
</details>
<details>
<summary>Music</summary>
<pre>
event:/music/cassette/01_forsaken_city
   fade min:0 max:1 default:1 GAME_CONTROLLED
   sixteenth_note min:1 max:257 default:1 GAME_CONTROLLED
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
event:/music/cassette/02_old_site
   sixteenth_note min:1 max:257 default:1 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
event:/music/cassette/03_resort
   sixteenth_note min:1 max:257 default:1 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
event:/music/cassette/04_cliffside
   sixteenth_note min:1 max:257 default:1 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
event:/music/cassette/05_mirror_temple
   fade min:0 max:1 default:1 GAME_CONTROLLED
   sixteenth_note min:1 max:257 default:1 GAME_CONTROLLED
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
event:/music/cassette/06_reflection
   sixteenth_note min:1 max:257 default:1 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
event:/music/cassette/07_summit
   fade min:0 max:1 default:1 GAME_CONTROLLED
   sixteenth_note min:1 max:257 default:1 GAME_CONTROLLED
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
event:/music/cassette/09_core
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
   sixteenth_note min:1 max:257 default:1 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl0/bridge
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl0/intro
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl0/title_ping
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl1/main
   layer2 min:0 max:1 default:1 GAME_CONTROLLED
   layer3 min:0 max:1 default:1 GAME_CONTROLLED
   end min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
   layer1 min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl1/theo
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl2/awake
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl2/beginning
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl2/chase
   escape min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl2/dreamblock_sting_pt1
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl2/dreamblock_sting_pt2
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl2/evil_madeline
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl2/mirror
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl2/phone_end
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl2/phone_loop
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl3/clean
   progress min:0 max:4 default:1 GAME_CONTROLLED
   escape min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl3/explore
   progress min:1 max:3 default:1 GAME_CONTROLLED
   layer2 min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
   layer1 min:0 max:1 default:0 GAME_CONTROLLED
event:/music/lvl3/intro
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl3/oshiro_chase
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl3/oshiro_theme
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl4/heavy_winds
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl4/main
   fade min:0 max:1 default:1 GAME_CONTROLLED
   layer3 min:0 max:1 default:0 GAME_CONTROLLED
   layer1 min:0 max:1 default:0 GAME_CONTROLLED
   layer2 min:0 max:1 default:0 GAME_CONTROLLED
event:/music/lvl4/minigame
   fade min:0 max:1 default:1 GAME_CONTROLLED
   gondola_idle min:0 max:1 default:0 GAME_CONTROLLED
   calm min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl5/middle_temple
   layer3 min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
   layer4 min:0 max:1 default:0 GAME_CONTROLLED
event:/music/lvl5/mirror
   layer3 min:0 max:1 default:0 GAME_CONTROLLED
   layer1 min:0 max:1 default:1 GAME_CONTROLLED
   eye_distance min:0 max:1 default:1 GAME_CONTROLLED
   layer6 min:0 max:1 default:0 GAME_CONTROLLED
   layer5 min:0 max:1 default:0 GAME_CONTROLLED
   layer2 min:0 max:1 default:0 GAME_CONTROLLED
   layer4 min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl5/mirror_cutscene
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl5/normal
   fade min:0 max:1 default:1 GAME_CONTROLLED
   layer2 min:0 max:1 default:0 GAME_CONTROLLED
   layer1 min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl6/badeline_acoustic
   fade min:0 max:1 default:1 GAME_CONTROLLED
   levelup min:0 max:2 default:0 GAME_CONTROLLED
event:/music/lvl6/badeline_fight
   boss_pitch min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl6/badeline_glitch
   fade min:0 max:1 default:1 GAME_CONTROLLED
   boss_pitch min:0 max:1 default:0 GAME_CONTROLLED
event:/music/lvl6/madeline_and_theo
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl6/main
   fade min:0 max:1 default:1 GAME_CONTROLLED
   layer3 min:0 max:1 default:0 GAME_CONTROLLED
   layer1 min:0 max:1 default:1 GAME_CONTROLLED
   layer2 min:0 max:1 default:0 GAME_CONTROLLED
event:/music/lvl6/secret_room
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl6/starjump
   fade min:0 max:1 default:1 GAME_CONTROLLED
   layer3 min:0 max:1 default:0 GAME_CONTROLLED
   layer2 min:0 max:1 default:0 GAME_CONTROLLED
   layer1 min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl6/the_fall
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl7/final_ascent
   escape min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl7/main
   progress min:0 max:7 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl8/main
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/lvl9/main
   layer2 min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
   progress min:0 max:4 default:0 GAME_CONTROLLED
   layer1 min:0 max:1 default:0 GAME_CONTROLLED
event:/music/menu/complete_area
   fade min:0 max:1 default:1 GAME_CONTROLLED
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/music/menu/complete_bside
   end min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/menu/complete_summit
   end min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/menu/credits
   fade min:0 max:1 default:1 GAME_CONTROLLED
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
event:/music/menu/level_select
   fade min:0 max:1 default:1 GAME_CONTROLLED
   moon min:0 max:1 default:0 GAME_CONTROLLED
event:/music/remix/01_forsaken_city
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/02_old_site
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/03_resort
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/04_cliffside
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/05_mirror_temple
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/06_reflection
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/07_summit
   fade min:0 max:1 default:1 GAME_CONTROLLED
   escape min:0 max:1 default:0 GAME_CONTROLLED
event:/music/remix/09_core
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/music/lvl10/cinematic/end_intro
   fade min:0 max:1 default:1 GAME_CONTROLLED
snapshot:/boss_pitch_sfx
snapshot:/env_allamb_down
snapshot:/env_worldmap_down
snapshot:/game_00_prologue_amb_down
snapshot:/game_00_prologue_amb_off
snapshot:/game_04_gondolafeather_main
snapshot:/game_04_gondolafeather_verb
snapshot:/game_05_eyedistance
snapshot:/mus_cassette_amb_down
snapshot:/mus_lvl1_verbtransition
</pre>
</details>
<details>
<summary>Sfxs</summary>
<pre>
event:/char/badeline/appear
event:/char/badeline/booster_begin
event:/char/badeline/booster_final
event:/char/badeline/booster_reappear
event:/char/badeline/booster_relocate
event:/char/badeline/booster_throw
event:/char/badeline/boss_bullet
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/char/badeline/boss_hug
event:/char/badeline/boss_idle_air
event:/char/badeline/boss_laser_charge
event:/char/badeline/boss_laser_fire
event:/char/badeline/boss_prefight_getup
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/climb_ledge
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/dash_red_left
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/dash_red_right
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/disappear
event:/char/badeline/dreamblock_enter
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/dreamblock_exit
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/dreamblock_travel
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/duck
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/footstep
   surface_index min:0 max:50 default:0 GAME_CONTROLLED
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/grab
   surface_index min:0 max:50 default:0 GAME_CONTROLLED
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/grab_letgo
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/handhold
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
   surface_index min:0 max:50 default:0 GAME_CONTROLLED
event:/char/badeline/jump
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/jump_assisted
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/jump_climb_left
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/jump_climb_right
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/jump_dreamblock
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/jump_special
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/jump_super
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/jump_superslide
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/jump_superwall
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/jump_wall_left
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/jump_wall_right
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/landing
   surface_index min:0 max:50 default:0 GAME_CONTROLLED
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/level_entry
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/maddy_join
event:/char/badeline/maddy_split
event:/char/badeline/stand
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
event:/char/badeline/temple_move_chats
event:/char/badeline/temple_move_first
event:/char/badeline/wallslide
   chaser_count min:0 max:4 default:0 GAME_CONTROLLED
   surface_index min:0 max:50 default:0 GAME_CONTROLLED
event:/char/dialogue/badeline
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
event:/char/dialogue/ex
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
event:/char/dialogue/granny
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
event:/char/dialogue/madeline
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
event:/char/dialogue/madeline_mirror
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
event:/char/dialogue/mom
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
event:/char/dialogue/oshiro
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
event:/char/dialogue/secret_character
event:/char/dialogue/sfx_support/phone_static_ex
event:/char/dialogue/sfx_support/phone_static_mom
event:/char/dialogue/theo
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
event:/char/dialogue/theo_mirror
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
event:/char/granny/cane_tap
event:/char/granny/laugh_firstphrase
   laugh_distance min:350 max:650 default:350 AUTOMATIC_DISTANCE
event:/char/granny/laugh_oneha
   laugh_distance min:350 max:650 default:350 AUTOMATIC_DISTANCE
event:/char/madeline/backpack_drop
event:/char/madeline/campfire_sit
event:/char/madeline/campfire_stand
event:/char/madeline/climb_ledge
event:/char/madeline/core_hair_charged
event:/char/madeline/crystaltheo_lift
event:/char/madeline/crystaltheo_throw
event:/char/madeline/dash_pink_left
event:/char/madeline/dash_pink_right
event:/char/madeline/dash_red_left
event:/char/madeline/dash_red_right
event:/char/madeline/death
event:/char/madeline/dreamblock_enter
event:/char/madeline/dreamblock_exit
event:/char/madeline/dreamblock_travel
event:/char/madeline/duck
event:/char/madeline/footstep
   raining min:0 max:1 default:0 GAME_CONTROLLED
   surface_index min:0 max:50 default:0 GAME_CONTROLLED
event:/char/madeline/grab
   surface_index min:0 max:50 default:0 GAME_CONTROLLED
   raining min:0 max:1 default:0 GAME_CONTROLLED
event:/char/madeline/grab_letgo
event:/char/madeline/handhold
   surface_index min:0 max:50 default:0 GAME_CONTROLLED
   raining min:0 max:1 default:0 GAME_CONTROLLED
event:/char/madeline/idle_crackknuckles
event:/char/madeline/idle_scratch
event:/char/madeline/idle_sneeze
event:/char/madeline/jump
event:/char/madeline/jump_assisted
event:/char/madeline/jump_climb_left
event:/char/madeline/jump_climb_right
event:/char/madeline/jump_dreamblock
event:/char/madeline/jump_special
event:/char/madeline/jump_super
event:/char/madeline/jump_superslide
event:/char/madeline/jump_superwall
event:/char/madeline/jump_wall_left
event:/char/madeline/jump_wall_right
event:/char/madeline/landing
   surface_index min:0 max:50 default:0 GAME_CONTROLLED
   raining min:0 max:1 default:0 GAME_CONTROLLED
event:/char/madeline/mirrortemple_big_landing
event:/char/madeline/predeath
event:/char/madeline/revive
event:/char/madeline/stand
event:/char/madeline/summit_areastart
event:/char/madeline/summit_flytonext
event:/char/madeline/summit_sit
event:/char/madeline/theo_collapse
event:/char/madeline/wallslide
   surface_index min:0 max:50 default:0 GAME_CONTROLLED
event:/char/madeline/water_dash_gen
event:/char/madeline/water_dash_in
event:/char/madeline/water_dash_out
event:/char/madeline/water_in
   deep min:0 max:1 default:0 GAME_CONTROLLED
event:/char/madeline/water_move_general
event:/char/madeline/water_move_shallow
event:/char/madeline/water_out
   deep min:0 max:1 default:0 GAME_CONTROLLED
event:/char/oshiro/boss_charge
event:/char/oshiro/boss_enter_screen
event:/char/oshiro/boss_precharge
event:/char/oshiro/boss_reform
event:/char/oshiro/boss_slam_final
event:/char/oshiro/boss_slam_first
event:/char/oshiro/boss_transform_begin
event:/char/oshiro/boss_transform_burst
event:/char/oshiro/chat_collapse
event:/char/oshiro/chat_get_up
event:/char/oshiro/chat_turn_left
event:/char/oshiro/chat_turn_right
event:/char/oshiro/move_01_0xa_exit
event:/char/oshiro/move_02_03a_exit
event:/char/oshiro/move_03_08a_exit
event:/char/oshiro/move_04_pace_left
event:/char/oshiro/move_04_pace_right
event:/char/oshiro/move_05_09b_exit
event:/char/oshiro/move_06_04d_exit
event:/char/oshiro/move_07_roof00_enter
event:/char/oshiro/move_08_roof07_exit
event:/char/theo/phone_taps_loop
event:/char/theo/resort_ceilingvent_hey
event:/char/theo/resort_ceilingvent_popoff
event:/char/theo/resort_ceilingvent_seeya
event:/char/theo/resort_ceilingvent_shake
event:/char/theo/resort_crawl
   venture_forth min:0 max:1 default:0 GAME_CONTROLLED
event:/char/theo/resort_standtocrawl
event:/char/theo/resort_vent_grab
event:/char/theo/resort_vent_rip
event:/char/theo/resort_vent_tug
event:/char/theo/resort_vent_tumble
event:/char/theo/yolo_fist
event:/classic/pico8_boot
event:/classic/pico8_mus_00
event:/classic/pico8_mus_01
event:/classic/pico8_mus_02
event:/classic/pico8_mus_03
event:/classic/sfx0
event:/classic/sfx1
event:/classic/sfx13
event:/classic/sfx14
event:/classic/sfx15
event:/classic/sfx16
event:/classic/sfx2
event:/classic/sfx23
event:/classic/sfx3
event:/classic/sfx35
event:/classic/sfx37
event:/classic/sfx38
event:/classic/sfx4
event:/classic/sfx5
event:/classic/sfx51
event:/classic/sfx54
event:/classic/sfx55
event:/classic/sfx6
event:/classic/sfx61
event:/classic/sfx62
event:/classic/sfx7
event:/classic/sfx8
event:/classic/sfx9
event:/env/amb/00_prologue
event:/env/amb/01_main
event:/env/amb/02_awake
event:/env/amb/02_dream
event:/env/amb/03_exterior
event:/env/amb/03_interior
   basement min:0 max:1 default:0 GAME_CONTROLLED
event:/env/amb/03_pico8_closeup
event:/env/amb/04_main
   shrine min:0 max:1 default:0 GAME_CONTROLLED
   wind_direction min:-1 max:1 default:0 GAME_CONTROLLED
   strong_wind min:0 max:1 default:0 GAME_CONTROLLED
event:/env/amb/05_interior_dark
event:/env/amb/05_interior_main
event:/env/amb/05_mirror_sequence
event:/env/amb/06_lake
event:/env/amb/06_main
   postboss min:0 max:1 default:0 GAME_CONTROLLED
event:/env/amb/09_main
   has_conveyors min:0 max:1 default:0 GAME_CONTROLLED
   room_state min:0 max:1 default:0 GAME_CONTROLLED
   progress min:0 max:3 default:0 GAME_CONTROLLED
event:/env/amb/worldmap
event:/env/local/02_old_site/phone_lamp
   on min:0 max:1 default:0 GAME_CONTROLLED
event:/env/local/03_resort/broken_window_large
event:/env/local/03_resort/broken_window_small
event:/env/local/03_resort/pico8_machine
   pico8_room min:0 max:700 default:0 AUTOMATIC_DISTANCE
event:/env/local/06_reflection/boss_idle_ground
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/env/local/07_summit/flag_flap
event:/env/local/09_core/conveyor_idle
event:/env/local/09_core/fireballs_idle
event:/env/local/09_core/lavagate_idle
event:/env/local/campfire_loop
event:/env/local/campfire_start
event:/env/local/waterfall_big_in
event:/env/local/waterfall_big_main
event:/env/local/waterfall_small_in_deep
event:/env/local/waterfall_small_in_shallow
event:/env/local/waterfall_small_main
event:/env/state/underwater
event:/game/00_prologue/bridge_rumble_loop
event:/game/00_prologue/bridge_support_break
event:/game/00_prologue/car_down
event:/game/00_prologue/car_up
event:/game/00_prologue/fallblock_first_impact
event:/game/00_prologue/fallblock_first_shake
   release min:0 max:1 default:0 GAME_CONTROLLED
event:/game/00_prologue/intro_vignette
event:/game/01_forsaken_city/birdbros_finish
event:/game/01_forsaken_city/birdbros_fly_loop
event:/game/01_forsaken_city/birdbros_thrust
event:/game/01_forsaken_city/console_blue
event:/game/01_forsaken_city/console_purple
event:/game/01_forsaken_city/console_red
event:/game/01_forsaken_city/console_static_long
event:/game/01_forsaken_city/console_static_loop
event:/game/01_forsaken_city/console_static_short
event:/game/01_forsaken_city/console_white
event:/game/01_forsaken_city/console_yellow
event:/game/01_forsaken_city/fallblock_ice_impact
event:/game/01_forsaken_city/fallblock_ice_shake
event:/game/01_forsaken_city/zip_mover
event:/game/02_old_site/lantern_hit
event:/game/02_old_site/sequence_badeline_intro
event:/game/02_old_site/sequence_mirror
event:/game/02_old_site/sequence_phone_pickup
event:/game/02_old_site/sequence_phone_ring_loop
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/game/02_old_site/sequence_phone_ringtone_loop
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/game/02_old_site/sequence_phone_transform
event:/game/02_old_site/theoselfie_foley
event:/game/02_old_site/theoselfie_photo_filter
event:/game/02_old_site/theoselfie_photo_in
event:/game/02_old_site/theoselfie_photo_out
event:/game/03_resort/clutterswitch_books
event:/game/03_resort/clutterswitch_boxes
event:/game/03_resort/clutterswitch_finish
event:/game/03_resort/clutterswitch_linens
event:/game/03_resort/clutterswitch_return
event:/game/03_resort/deskbell_again
event:/game/03_resort/door_metal_close
event:/game/03_resort/door_metal_open
event:/game/03_resort/door_wood_close
event:/game/03_resort/door_wood_open
event:/game/03_resort/fallblock_wood_impact
event:/game/03_resort/fallblock_wood_shake
event:/game/03_resort/fallblock_wooddistant_impact
event:/game/03_resort/fluff_tendril_emerge
event:/game/03_resort/fluff_tendril_recede
event:/game/03_resort/fluff_tendril_touch
event:/game/03_resort/forcefield_bump
event:/game/03_resort/forcefield_idle_loop
event:/game/03_resort/forcefield_vanish
event:/game/03_resort/key_unlock
event:/game/03_resort/lantern_bump
event:/game/03_resort/memo_in
event:/game/03_resort/memo_out
event:/game/03_resort/platform_horiz_left
event:/game/03_resort/platform_horiz_right
event:/game/03_resort/platform_vert_down_loop
   ducking min:0 max:1 default:0 GAME_CONTROLLED
event:/game/03_resort/platform_vert_end
event:/game/03_resort/platform_vert_start
event:/game/03_resort/platform_vert_up_loop
event:/game/03_resort/sequence_oshiro_intro
event:/game/03_resort/sequence_oshirofluff_pt1
event:/game/03_resort/sequence_oshirofluff_pt2
event:/game/03_resort/suite_bad_ceilingbreak
event:/game/03_resort/suite_bad_exittop
event:/game/03_resort/suite_bad_intro
event:/game/03_resort/suite_bad_mirrorbreak
event:/game/03_resort/suite_bad_moveroof
event:/game/03_resort/suite_bad_movestageleft
event:/game/03_resort/trapdoor_frombottom
event:/game/03_resort/trapdoor_fromtop
event:/game/04_cliffside/arrowblock_activate
event:/game/04_cliffside/arrowblock_break
event:/game/04_cliffside/arrowblock_debris
   debris_velocity min:0 max:1 default:0 GAME_CONTROLLED
event:/game/04_cliffside/arrowblock_move
   arrow_stop min:0 max:1 default:0 GAME_CONTROLLED
   arrow_influence min:1 max:9 default:1 GAME_CONTROLLED
event:/game/04_cliffside/arrowblock_reappear
event:/game/04_cliffside/arrowblock_reform_begin
event:/game/04_cliffside/arrowblock_side_depress
event:/game/04_cliffside/arrowblock_side_release
event:/game/04_cliffside/cloud_blue_boost
event:/game/04_cliffside/cloud_pink_boost
event:/game/04_cliffside/cloud_pink_reappear
event:/game/04_cliffside/gondola_cliffmechanism_start
event:/game/04_cliffside/gondola_finish
event:/game/04_cliffside/gondola_halted_loop
event:/game/04_cliffside/gondola_movement_loop
event:/game/04_cliffside/gondola_restart
event:/game/04_cliffside/gondola_scaryhair_01
event:/game/04_cliffside/gondola_scaryhair_02
event:/game/04_cliffside/gondola_scaryhair_03
event:/game/04_cliffside/gondola_theo_fall
event:/game/04_cliffside/gondola_theo_lever_fail
event:/game/04_cliffside/gondola_theo_lever_start
event:/game/04_cliffside/gondola_theo_recover
event:/game/04_cliffside/gondola_theoselfie_halt
event:/game/04_cliffside/greenbooster_dash
event:/game/04_cliffside/greenbooster_end
event:/game/04_cliffside/greenbooster_enter
event:/game/04_cliffside/greenbooster_reappear
event:/game/04_cliffside/snowball_impact
event:/game/04_cliffside/snowball_spawn
event:/game/04_cliffside/stone_blockade
event:/game/05_mirror_temple/bladespinner_spin
event:/game/05_mirror_temple/button_activate
event:/game/05_mirror_temple/button_depress
event:/game/05_mirror_temple/button_return
event:/game/05_mirror_temple/crackedwall_vanish
event:/game/05_mirror_temple/crystaltheo_break_free
event:/game/05_mirror_temple/crystaltheo_hit_ground
   crystal_velocity min:0 max:1 default:0 GAME_CONTROLLED
event:/game/05_mirror_temple/crystaltheo_hit_side
event:/game/05_mirror_temple/eye_pulse
event:/game/05_mirror_temple/eyebro_eyemove
event:/game/05_mirror_temple/eyewall_bounce
event:/game/05_mirror_temple/eyewall_destroy
event:/game/05_mirror_temple/gate_main_close
event:/game/05_mirror_temple/gate_main_open
event:/game/05_mirror_temple/gate_theo_close
event:/game/05_mirror_temple/gate_theo_open
event:/game/05_mirror_temple/key_unlock_dark
event:/game/05_mirror_temple/key_unlock_light
event:/game/05_mirror_temple/mainmirror_reveal
event:/game/05_mirror_temple/mainmirror_torch_lit_1
event:/game/05_mirror_temple/mainmirror_torch_lit_2
event:/game/05_mirror_temple/mainmirror_torch_loop
event:/game/05_mirror_temple/redbooster_dash
event:/game/05_mirror_temple/redbooster_end
event:/game/05_mirror_temple/redbooster_enter
event:/game/05_mirror_temple/redbooster_move
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/game/05_mirror_temple/redbooster_reappear
event:/game/05_mirror_temple/room_lightlevel_down
event:/game/05_mirror_temple/room_lightlevel_up
event:/game/05_mirror_temple/seeker_aggro
event:/game/05_mirror_temple/seeker_booped
event:/game/05_mirror_temple/seeker_dash
event:/game/05_mirror_temple/seeker_dash_turn
event:/game/05_mirror_temple/seeker_death
event:/game/05_mirror_temple/seeker_hit_lightwall
event:/game/05_mirror_temple/seeker_hit_normal
event:/game/05_mirror_temple/seeker_playercontrolstart
event:/game/05_mirror_temple/seeker_revive
event:/game/05_mirror_temple/seeker_statue_break
event:/game/05_mirror_temple/swapblock_move
event:/game/05_mirror_temple/swapblock_move_end
event:/game/05_mirror_temple/swapblock_return
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/game/05_mirror_temple/swapblock_return_end
event:/game/05_mirror_temple/torch_activate
event:/game/06_reflection/badeline_feather_slice
event:/game/06_reflection/badeline_freakout_1
event:/game/06_reflection/badeline_freakout_2
event:/game/06_reflection/badeline_freakout_3
event:/game/06_reflection/badeline_freakout_4
event:/game/06_reflection/badeline_freakout_5
event:/game/06_reflection/badeline_pull_cliffbreak
event:/game/06_reflection/badeline_pull_impact
event:/game/06_reflection/badeline_pull_rumble_loop
event:/game/06_reflection/badeline_pull_whooshdown
event:/game/06_reflection/boss_spikes_burst
event:/game/06_reflection/crushblock_activate
event:/game/06_reflection/crushblock_impact
event:/game/06_reflection/crushblock_move_loop
   end min:0 max:1 default:0 GAME_CONTROLLED
   submerged min:0 max:1 default:0 GAME_CONTROLLED
event:/game/06_reflection/crushblock_rest
event:/game/06_reflection/crushblock_rest_waypoint
event:/game/06_reflection/crushblock_return_loop
   submerged min:0 max:1 default:0 GAME_CONTROLLED
event:/game/06_reflection/fall_spike_smash
event:/game/06_reflection/fallblock_boss_impact
event:/game/06_reflection/fallblock_boss_shake
event:/game/06_reflection/feather_bubble_bounce
event:/game/06_reflection/feather_bubble_get
event:/game/06_reflection/feather_bubble_renew
event:/game/06_reflection/feather_get
event:/game/06_reflection/feather_reappear
event:/game/06_reflection/feather_renew
event:/game/06_reflection/feather_state_bump
event:/game/06_reflection/feather_state_end
event:/game/06_reflection/feather_state_loop
   feather_speed min:0 max:1 default:0 GAME_CONTROLLED
event:/game/06_reflection/feather_state_warning
event:/game/06_reflection/hug_badeline_glow
event:/game/06_reflection/hug_image_1
event:/game/06_reflection/hug_image_2
event:/game/06_reflection/hug_image_3
event:/game/06_reflection/hug_levelup_text_in
event:/game/06_reflection/hug_levelup_text_out
event:/game/06_reflection/pinballbumper_hit
event:/game/06_reflection/pinballbumper_reset
event:/game/06_reflection/scaryhair_move
event:/game/06_reflection/scaryhair_whoosh
event:/game/06_reflection/supersecret_dashflavour
   dash_direction min:1 max:9 default:1 GAME_CONTROLLED
event:/game/06_reflection/supersecret_heartappear
event:/game/06_reflection/supersecret_torch_1
event:/game/06_reflection/supersecret_torch_2
event:/game/06_reflection/supersecret_torch_3
event:/game/06_reflection/supersecret_torch_4
event:/game/07_summit/altitude_count
event:/game/07_summit/checkpoint_confetti
event:/game/07_summit/gem_get
event:/game/07_summit/gem_unlock_1
   gem_distance min:0 max:700 default:0 AUTOMATIC_DISTANCE
event:/game/07_summit/gem_unlock_2
   gem_distance min:0 max:700 default:0 AUTOMATIC_DISTANCE
event:/game/07_summit/gem_unlock_3
   gem_distance min:0 max:700 default:0 AUTOMATIC_DISTANCE
event:/game/07_summit/gem_unlock_4
   gem_distance min:0 max:700 default:0 AUTOMATIC_DISTANCE
event:/game/07_summit/gem_unlock_5
   gem_distance min:0 max:700 default:0 AUTOMATIC_DISTANCE
event:/game/07_summit/gem_unlock_6
   gem_distance min:0 max:700 default:0 AUTOMATIC_DISTANCE
event:/game/07_summit/gem_unlock_complete
   gem_distance min:0 max:700 default:0 AUTOMATIC_DISTANCE
event:/game/09_core/bounceblock_break
event:/game/09_core/bounceblock_reappear
event:/game/09_core/bounceblock_touch
event:/game/09_core/conveyor_activate
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/game/09_core/final_heart_get
event:/game/09_core/frontdoor_heartfill
event:/game/09_core/frontdoor_unlock
event:/game/09_core/hotpinball_activate
event:/game/09_core/iceball_break
event:/game/09_core/iceblock_reappear
event:/game/09_core/iceblock_touch
event:/game/09_core/pinballbumper_hit
event:/game/09_core/rising_threat
   room_state min:0 max:1 default:0 GAME_CONTROLLED
   rising min:0 max:1 default:0 GAME_CONTROLLED
event:/game/09_core/switch_dies
event:/game/09_core/switch_to_cold
event:/game/09_core/switch_to_hot
event:/game/general/assist_dreamblockbounce
event:/game/general/assist_nonsolid_in
event:/game/general/assist_nonsolid_out
event:/game/general/assist_screenbottom
event:/game/general/bird_in
event:/game/general/bird_land_dirt
event:/game/general/bird_peck
event:/game/general/bird_squawk
event:/game/general/bird_startle
event:/game/general/birdbaby_flyaway
event:/game/general/birdbaby_hop
event:/game/general/birdbaby_tweet_loop
event:/game/general/cassette_block_switch_1
event:/game/general/cassette_block_switch_2
event:/game/general/cassette_bubblereturn
event:/game/general/cassette_get
event:/game/general/cassette_preview
   remix min:0 max:10 default:0 GAME_CONTROLLED
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/game/general/crystalheart_blue_get
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/game/general/crystalheart_bounce
event:/game/general/crystalheart_gold_get
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/game/general/crystalheart_pulse
event:/game/general/crystalheart_red_get
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/game/general/debris_dirt
   debris_velocity min:0 max:1 default:0 GAME_CONTROLLED
event:/game/general/debris_stone
   debris_velocity min:0 max:1 default:0 GAME_CONTROLLED
event:/game/general/debris_wood
   debris_velocity min:0 max:1 default:0 GAME_CONTROLLED
event:/game/general/diamond_return
event:/game/general/diamond_touch
event:/game/general/fallblock_impact
event:/game/general/fallblock_shake
event:/game/general/key_get
event:/game/general/lookout_move
event:/game/general/lookout_use
event:/game/general/passage_closed_behind
event:/game/general/platform_disintegrate
event:/game/general/platform_return
event:/game/general/secret_revealed
event:/game/general/seed_complete_berry
event:/game/general/seed_complete_main
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
event:/game/general/seed_poof
event:/game/general/seed_pulse
   count min:0 max:6 default:0 GAME_CONTROLLED
event:/game/general/seed_reappear
   count min:0 max:6 default:0 GAME_CONTROLLED
event:/game/general/seed_touch
   count min:0 max:6 default:0 GAME_CONTROLLED
event:/game/general/spotlight_intro
event:/game/general/spotlight_outro
event:/game/general/spring
event:/game/general/strawberry_blue_pulse
event:/game/general/strawberry_blue_touch
event:/game/general/strawberry_flyaway
event:/game/general/strawberry_get
   count min:0 max:6 default:0 GAME_CONTROLLED
   colour min:0 max:4 default:0 GAME_CONTROLLED
event:/game/general/strawberry_laugh
event:/game/general/strawberry_pulse
event:/game/general/strawberry_touch
event:/game/general/strawberry_wingflap
event:/game/general/thing_booped
event:/game/general/touchswitch_any
event:/game/general/touchswitch_gate_finish
event:/game/general/touchswitch_gate_open
event:/game/general/touchswitch_last
event:/game/general/touchswitch_last_cutoff
event:/game/general/touchswitch_last_oneshot
event:/game/general/wall_break_dirt
event:/game/general/wall_break_ice
event:/game/general/wall_break_stone
event:/game/general/wall_break_wood
event:/music/remix/01_forsaken_city
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/02_old_site
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/03_resort
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/04_cliffside
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/05_mirror_temple
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/06_reflection
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/music/remix/07_summit
   fade min:0 max:1 default:1 GAME_CONTROLLED
   escape min:0 max:1 default:0 GAME_CONTROLLED
event:/music/remix/09_core
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/game/10_farewell/bird_fly_uptonext
event:/state/underwater
   underwater min:0 max:1 default:0 GAME_CONTROLLED
event:/ui/game/general_text_loop
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/ui/game/increment_dashcount
event:/ui/game/increment_strawberry
event:/ui/main/assist_button_info
event:/ui/main/assist_button_no
event:/ui/main/assist_button_yes
event:/ui/main/assist_info_whistle
   assist_progress min:0 max:6 default:0 GAME_CONTROLLED
event:/ui/main/bside_intro_text
event:/ui/postgame/death_appear
event:/ui/postgame/goldberry_count
event:/ui/world_map/icon/assist_skip
snapshot:/berry_cooperation/1000s_down
snapshot:/berry_cooperation/2000s_down
snapshot:/berry_cooperation/3000s_down
snapshot:/berry_cooperation/4000s_down
snapshot:/berry_cooperation/5000s_down
snapshot:/char_granny_laughs_down
snapshot:/env_allamb_down
snapshot:/game_00_verb
snapshot:/game_01_birdbros_finish
snapshot:/game_03_clutterswitch_moment
snapshot:/game_03_oshirofreakout
snapshot:/game_03_pico8room
snapshot:/game_05_eyedeath
snapshot:/game_05_mus_pulse_controller
snapshot:/game_05_torch_arp
snapshot:/game_gen_crystalheart
snapshot:/game_gen_large_berry_get
snapshot:/music_all_mute
snapshot:/music_reflection_secret
snapshot:/music_secretrevealed
snapshot:/underwater
</pre>
</details>
<details>
<summary>UI</summary>
<pre>
event:/game/03_resort/clutterswitch_squish
event:/ui/game/chatoptions_appear
event:/ui/game/chatoptions_roll_down
event:/ui/game/chatoptions_roll_up
event:/ui/game/chatoptions_select
event:/ui/game/hotspot_main_in
event:/ui/game/hotspot_main_out
event:/ui/game/hotspot_note_in
event:/ui/game/hotspot_note_out
event:/ui/game/lookout_off
event:/ui/game/lookout_on
event:/ui/game/memorial_dream_loop
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/ui/game/memorial_dream_text_in
event:/ui/game/memorial_dream_text_loop
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/ui/game/memorial_dream_text_out
event:/ui/game/memorial_text_in
event:/ui/game/memorial_text_loop
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/ui/game/memorial_text_out
event:/ui/game/pause
event:/ui/game/textadvance_madeline
event:/ui/game/textadvance_other
event:/ui/game/textbox_madeline_in
event:/ui/game/textbox_madeline_out
event:/ui/game/textbox_other_in
event:/ui/game/textbox_other_out
event:/ui/game/tutorial_note_flip_back
event:/ui/game/tutorial_note_flip_front
event:/ui/game/unpause
event:/ui/main/button_back
event:/ui/main/button_climb
event:/ui/main/button_invalid
event:/ui/main/button_lowkey
event:/ui/main/button_select
event:/ui/main/button_toggle_off
event:/ui/main/button_toggle_on
event:/ui/main/message_confirm
event:/ui/main/postcard_ch1_in
event:/ui/main/postcard_ch1_out
event:/ui/main/postcard_ch2_in
event:/ui/main/postcard_ch2_out
event:/ui/main/postcard_ch3_out
event:/ui/main/postcard_ch4_in
event:/ui/main/postcard_ch4_out
event:/ui/main/postcard_ch5_in
event:/ui/main/postcard_ch5_out
event:/ui/main/postcard_ch6_in
event:/ui/main/postcard_ch6_out
event:/ui/main/postcard_csides_in
event:/ui/main/postcard_csides_out
event:/ui/main/rename_entry_accept
event:/ui/main/rename_entry_backspace
event:/ui/main/rename_entry_char
event:/ui/main/rename_entry_rollover
event:/ui/main/rename_entry_space
event:/ui/main/rollover_down
event:/ui/main/rollover_up
event:/ui/main/savefile_begin
event:/ui/main/savefile_delete
event:/ui/main/savefile_rename_start
event:/ui/main/savefile_rollover_down
event:/ui/main/savefile_rollover_first
event:/ui/main/savefile_rollover_up
event:/ui/main/title_firstinput
event:/ui/main/whoosh_large_in
event:/ui/main/whoosh_large_out
event:/ui/main/whoosh_list_in
event:/ui/main/whoosh_list_out
event:/ui/main/whoosh_savefile_in
event:/ui/main/whoosh_savefile_out
event:/ui/postgame/crystal_heart
event:/ui/postgame/death_count
event:/ui/postgame/death_final
event:/ui/postgame/strawberry_count
event:/ui/postgame/strawberry_total
event:/ui/postgame/strawberry_total_all
event:/ui/postgame/unlock_bside
event:/ui/postgame/unlock_newchapter
event:/ui/world_map/chapter/back
event:/ui/world_map/chapter/checkpoint_back
event:/ui/world_map/chapter/checkpoint_photo_add
event:/ui/world_map/chapter/checkpoint_photo_remove
event:/ui/world_map/chapter/checkpoint_start
event:/ui/world_map/chapter/level_select
event:/ui/world_map/chapter/pane_contract
event:/ui/world_map/chapter/pane_expand
event:/ui/world_map/chapter/tab_roll_left
event:/ui/world_map/chapter/tab_roll_right
event:/ui/world_map/icon/flip_left
event:/ui/world_map/icon/flip_right
event:/ui/world_map/icon/roll_left
event:/ui/world_map/icon/roll_right
event:/ui/world_map/icon/select
event:/ui/world_map/journal/back
event:/ui/world_map/journal/heart_grab
event:/ui/world_map/journal/heart_release
event:/ui/world_map/journal/heart_roll
event:/ui/world_map/journal/heart_shift_down
event:/ui/world_map/journal/heart_shift_up
event:/ui/world_map/journal/page_cover_back
event:/ui/world_map/journal/page_cover_forward
event:/ui/world_map/journal/page_main_back
event:/ui/world_map/journal/page_main_forward
event:/ui/world_map/journal/select
snapshot:/game_02_dreammemorial_fade
</pre>
</details>
<details>
<summary>DlcMusic</summary>
<pre>
event:/new_content/music/lvl10/cassette_rooms
   fade min:0 max:1 default:1 GAME_CONTROLLED
   sixteenth_note min:1 max:257 default:1 GAME_CONTROLLED
   ahdsr_controller min:0 max:1 default:0 GAME_CONTROLLED
   progress min:0 max:3 default:0 GAME_CONTROLLED
event:/new_content/music/lvl10/cinematic/bird_crash_first
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/music/lvl10/cinematic/bird_crash_second
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/music/lvl10/cinematic/end
   end min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/music/lvl10/final_run
   toodamnfast min:0 max:1 default:0 GAME_CONTROLLED
   progress min:0 max:3 default:0 GAME_CONTROLLED
event:/new_content/music/lvl10/golden_room
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/music/lvl10/granny_farewell
   end min:0 max:1 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/music/lvl10/intermission_heartgroove
   fade min:0 max:1 default:1 GAME_CONTROLLED
   escape min:0 max:1 default:0 GAME_CONTROLLED
   bird_grab min:0 max:1 default:0 GAME_CONTROLLED
event:/new_content/music/lvl10/intermission_powerpoint
   fade min:0 max:1 default:1 GAME_CONTROLLED
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/new_content/music/lvl10/part01
   progress min:0 max:3 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/music/lvl10/part02
   if_bubble min:0 max:1 default:0 GAME_CONTROLLED
   progress min:0 max:3 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/music/lvl10/part03
   in_space min:0 max:2 default:0 GAME_CONTROLLED
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/music/lvl10/reconciliation
   fade min:0 max:1 default:1 GAME_CONTROLLED
snapshot:/game_10_in_space
snapshot:/game_10_kevinpc_sendcontrol
snapshot:/game_10_kevinpc_verbtransition
</pre>
</details>
<details>
<summary>DlcSfxs</summary>
<pre>
event:/char/dialogue/theo
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
event:/char/dialogue/theo_webcam
   dialogue_end min:0 max:1 default:0 GAME_CONTROLLED
   dialogue_portrait min:0 max:12 default:0 GAME_CONTROLLED
event:/game/06_reflection/crushblock_move_loop_covert
   submerged min:0 max:1 default:0 GAME_CONTROLLED
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/new_content/char/badeline/birdcrash_scene_float
event:/new_content/char/badeline/booster_finalfinal_part1
event:/new_content/char/badeline/booster_finalfinal_part2
   final_boost_ahdsr min:0 max:1 default:0 GAME_CONTROLLED
event:/new_content/char/badeline/booster_first_appear
event:/new_content/char/badeline/booster_relocate_slow
event:/new_content/char/badeline/maddy_join_quick
event:/new_content/char/granny/cane_tap_ending
event:/new_content/char/granny/dissipate
event:/new_content/char/madeline/bounce_boost
event:/new_content/char/madeline/death_golden
event:/new_content/char/madeline/glider_drop
event:/new_content/char/madeline/hiccup_ducking
event:/new_content/char/madeline/hiccup_standing
event:/new_content/char/madeline/screenentry_golden
event:/new_content/char/madeline/screenentry_gran
event:/new_content/char/madeline/screenentry_gran_landing
event:/new_content/char/madeline/screenentry_lowgrav
event:/new_content/char/madeline/screenentry_stubborn
event:/new_content/char/tutorial_ghost/appear
event:/new_content/char/tutorial_ghost/dash_red_left
event:/new_content/char/tutorial_ghost/dash_red_right
event:/new_content/char/tutorial_ghost/disappear
event:/new_content/char/tutorial_ghost/dreamblock_sequence
event:/new_content/char/tutorial_ghost/footstep
event:/new_content/char/tutorial_ghost/grab
event:/new_content/char/tutorial_ghost/handhold
event:/new_content/char/tutorial_ghost/jump
event:/new_content/char/tutorial_ghost/jump_super
event:/new_content/char/tutorial_ghost/land
event:/new_content/env/10_electricity
event:/new_content/env/10_endscene
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/env/10_grannyclouds
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/env/10_rain
event:/new_content/env/10_rushingvoid
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/env/10_space_underwater
   fade min:0 max:1 default:1 GAME_CONTROLLED
event:/new_content/env/10_voidspiral
   strong_wind min:0 max:1 default:0 GAME_CONTROLLED
   wind_direction min:-1 max:1 default:0 GAME_CONTROLLED
event:/new_content/env/local/cafe_computer
event:/new_content/env/local/cafe_sign
event:/new_content/env/local/kevinpc
   kevinpc_distance min:0 max:600 default:0 AUTOMATIC_DISTANCE
event:/new_content/env/local/tutorial_static_left
event:/new_content/env/local/tutorial_static_right
event:/new_content/game/10_farewell/bird_camera_pan_up
event:/new_content/game/10_farewell/bird_crashscene_leave
event:/new_content/game/10_farewell/bird_crashscene_recover
event:/new_content/game/10_farewell/bird_crashscene_relocate
event:/new_content/game/10_farewell/bird_crashscene_start
event:/new_content/game/10_farewell/bird_crashscene_twitch_1
event:/new_content/game/10_farewell/bird_crashscene_twitch_2
event:/new_content/game/10_farewell/bird_crashscene_twitch_3
event:/new_content/game/10_farewell/bird_flappyscene
event:/new_content/game/10_farewell/bird_flappyscene_entry
event:/new_content/game/10_farewell/bird_flyuproll
event:/new_content/game/10_farewell/bird_relocate
event:/new_content/game/10_farewell/bird_startle
event:/new_content/game/10_farewell/bird_throw
event:/new_content/game/10_farewell/bird_wingflap
event:/new_content/game/10_farewell/cafe_computer_off
event:/new_content/game/10_farewell/cafe_computer_on
event:/new_content/game/10_farewell/cafe_computer_on_old
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/new_content/game/10_farewell/cafe_computer_startupsfx
event:/new_content/game/10_farewell/endscene_attachment_click
event:/new_content/game/10_farewell/endscene_attachment_notify
event:/new_content/game/10_farewell/endscene_dial_theo
event:/new_content/game/10_farewell/endscene_final_input
event:/new_content/game/10_farewell/endscene_photo_zoom
event:/new_content/game/10_farewell/fakeheart_bounce
event:/new_content/game/10_farewell/fakeheart_get
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/new_content/game/10_farewell/fakeheart_pulse
event:/new_content/game/10_farewell/fusebox_hit_1
event:/new_content/game/10_farewell/fusebox_hit_2
event:/new_content/game/10_farewell/glider_emancipate
event:/new_content/game/10_farewell/glider_engage
event:/new_content/game/10_farewell/glider_land
event:/new_content/game/10_farewell/glider_movement
   glider_speed min:0 max:1 default:0 GAME_CONTROLLED
event:/new_content/game/10_farewell/glider_platform_dissipate
event:/new_content/game/10_farewell/glider_wallbounce_left
event:/new_content/game/10_farewell/glider_wallbounce_right
event:/new_content/game/10_farewell/glitch_long
event:/new_content/game/10_farewell/glitch_medium
event:/new_content/game/10_farewell/glitch_short
event:/new_content/game/10_farewell/heart_door
event:/new_content/game/10_farewell/key_unlock_1
event:/new_content/game/10_farewell/key_unlock_2
event:/new_content/game/10_farewell/key_unlock_3
event:/new_content/game/10_farewell/key_unlock_4
event:/new_content/game/10_farewell/key_unlock_5
event:/new_content/game/10_farewell/lightning_strike
event:/new_content/game/10_farewell/locked_door_appear_1
event:/new_content/game/10_farewell/locked_door_appear_2
event:/new_content/game/10_farewell/locked_door_appear_3
event:/new_content/game/10_farewell/locked_door_appear_4
event:/new_content/game/10_farewell/locked_door_appear_5
event:/new_content/game/10_farewell/pico8_flag
event:/new_content/game/10_farewell/pinkdiamond_return
event:/new_content/game/10_farewell/pinkdiamond_touch
event:/new_content/game/10_farewell/ppt_cube_transition
event:/new_content/game/10_farewell/ppt_dissolve_transition
event:/new_content/game/10_farewell/ppt_doubleclick
event:/new_content/game/10_farewell/ppt_happy_wavedashing
event:/new_content/game/10_farewell/ppt_impossible
event:/new_content/game/10_farewell/ppt_its_easy
event:/new_content/game/10_farewell/ppt_mouseclick
event:/new_content/game/10_farewell/ppt_spinning_transition
event:/new_content/game/10_farewell/ppt_wavedash_whoosh
event:/new_content/game/10_farewell/puffer_boop
event:/new_content/game/10_farewell/puffer_expand
event:/new_content/game/10_farewell/puffer_reform
event:/new_content/game/10_farewell/puffer_return
event:/new_content/game/10_farewell/puffer_shrink
event:/new_content/game/10_farewell/puffer_splode
event:/new_content/game/10_farewell/quake_onset
event:/new_content/game/10_farewell/quake_rockbreak
event:/new_content/game/10_farewell/strawberry_gold_detach
event:/new_content/game/10_farewell/zip_mover
event:/new_content/timeline_bubble_to_remembered
event:/new_content/ui/postcard_variants_in
event:/new_content/ui/postcard_variants_out
event:/new_content/ui/rename_entry_accept_locked
event:/new_content/ui/skip_all
event:/state/cafe_computer_active
   quit min:0 max:1 default:0 GAME_CONTROLLED
   end min:0 max:1 default:0 GAME_CONTROLLED
event:/ui/postgame/unlock_newchapter_icon
snapshot:/game_10_BIR_music_part01
snapshot:/game_10_BIR_music_part02
snapshot:/game_10_BIR_sfx
snapshot:/game_10_amb_voidspiral_active
snapshot:/game_10_cafe_computer_active
snapshot:/game_10_final_boost
snapshot:/game_10_glitch_active
snapshot:/game_10_goldenroom_death_fix
snapshot:/game_gen_crystalheart
snapshot:/game_gen_large_berry_get
</pre>
</details>

Please note that this page was mostly computer generated, but people make mistakes. For questions or feedback, contact @coloursofnoise on the Celeste Discord.

Additionally, many of the sounds listed here require additional parameters to function properly, which are listed underneath the IDs