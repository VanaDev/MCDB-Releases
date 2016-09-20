Changelog
=========

This is a full series of changelogs since I've been keeping records. The code for the prefixes is as follows:
+ means addition
~ means change
- means removal
= means a note
Double indicators means that it's a significant operation
! as the first indicator means really important change
~+ may be combined to indicate a modification that's tied to an addition, for example, fusing two tables into a new one

4.3
===
~~Renamed skill_player_data to skill_player_level_data (this is actually fairly major, considering that a new table is skill_player_data)
~ Renamed item_equip_data.equipid, item_timeless_levels.equipid, item_timeless_skills.equipid, and item_pet_data.id to itemid for consistency
~ Renamed item_monster_card_map_ranges.startmap and endmap to start_map and end_map, respectively
~ Renamed maker_rewards.prob to chance
~ Renamed reactor_data.maxstates to max_states
~ Renamed reactor_events.nextstate to next_state
~ Renamed make_creation_data.req_mesos to req_money
~~Removed SQL reserved keywords from field names:
~ Renamed item_equip_data.int to intelligence and also updated the other 3 core stats to follow suit
~ Renamed item_data.exp to experience
~ Renamed item_consume_data.time to buff_time
~ Renamed character_forbidden_names.name to forbidden_name
~ Renamed item_pet_data.name to default_name
~ Renamed item_reward_data.count to quantity
~ Renamed item_timeless_levels.level and exp to item_level and experience
~ Renamed maker_recipes.count to quantity
~ Renamed map_footholds.prev and next to previousid and nextid
~ Renamed map_life.name, x, and y to life_name, x_pos, and y_pos
~ Renamed map_portals.name, x, y, and destination_portal to label, x_pos, y_pos, and destination_label
~ Renamed map_seats.x and y to x_pos and y_pos
~ Renamed mob_data.level and exp to mob_level and experience
~ Renamed mob_skills.level to skill_level
~ Renamed physical_defense_data.level to player_level
~ Renamed quest_requests.count to quantity
~ Renamed quest_rewards.count to quantity
~ Renamed reactor_events.type to event_type
~ Renamed scripts.modifier to helper
~ Renamed skill_family_data.time to buff_time
~ Renamed skill_mob_data.level, time, x, and y to skill_level, buff_time, x_property, and y_property
~ Renamed skill_monster_carnival.type and time to buff_type and buff_time
~ Renamed skill_player_level_data.level, time, x, and y to skill_level, buff_time, x_property, and y_property
~ Renamed strings.name to label
+ Added new set types for the Episode 2 jobs in quest rewards and the processing backend to support them
+ Added skill_player_data and skill_player_requirement_data tables
+ Added crc_info table of all .wz CRCs in both string and integral formats
+ Added maple_locale and test_server fields to mcdb_info
+ Added item_equip_bonus_exp table
+ Added recovery, knockback, and specialid fields to item_equip_data
+ Added drop_item_period field to mob_data
+ Added jumpable, magic, and knockback flags to mob_attacks.flags
+ Added element and attack_type fields to mob_attacks
+ Added quest_exclusive_medals table
+ Added inventory field to item_data
- Removed skill_mob_summons.index field

4.2
===
~ Modified mob_attacks.disease to mob_skillid (and level to mob_skill_level) to better convey purpose
~ Modified shop_data.rechargetier to recharge_tier (and the same to the user_ table)
~ Modified character_creation_data.object_id to objectid
~ Modified item_skills.required_skill_level to req_skill_level
~ Modified map_continent_data's fields: mapcluster -> map_cluster and continentcode -> continent
~ Modified map_portals fields: tomap -> destination and toname -> destination_portal
~ Modified map_time_mob fields: starthour -> start_hour and endhour -> end_hour
~ Modified ox_quiz_data.questionset to question_set
~ Modified scripts.quest_state to modifier
~ Removed the primary key of reactor_event_trigger_skills; it's useless to have all three fields as a primary key
~ Clarified one field limitation bit, modified a couple that actually are used from "unused"
~ Fixed a bug in quest reward job processing (thanks to Hendi48)
+ Added ship_kind field to map_data
+ Added is_guild_rank flag to npc_data
+ Added a number of comments to various fields
+ Added a couple quest drops (thanks to Diamondo25)
+ Added pet_skill reward type to quest rewards
+ Added flags field to quest_data, also added time_limit and selected_mob
+ Added an index processing of sorts to NPC scripts (they may have multiple scripts)

4.1
===
~ Made "id" fields consistent with one another (removed _ from all)
~ Made most SQL set fields non-nullable and default to no flags
~ Fixed an issue in item processing
~ Renamed string_data to strings
~ Reordered mob data columns to put stats before resistances
~ Modified unused bits in field_type to reflect this (as opposed to no_clue)
+ Added skill_family_data, item_maker_data, item_reward_data, quest_area_data, and item_scroll_targets tables
+ Added party_quest flag to item_data
+ Added money and state_change_item to item_data
+ Added a bunch of pet equip flags to item_equip_data
+ Added area, pet_closeness, and taming_mob_level fields to quest_data
+ Added create_item field to item_consume_data
+ Added pet closeness and pet speed quest rewards

4.0
===
++Added tons of tables
++Added countless properties to many existing tables, notably map/mob/items
--Removed the mapreactor table (fused with maplife)
--Removed reactor event repeat property; it only matters for the animation
~~Changed equip data to only have data relevant to equips
~~Changed item data to only have data relevant to all items
~~Changed drop global data to accept continent information
~~Changed ban fields to banish data
~~Renamed countless fields to be more clear about their purpose
~~Renamed every table
~~Separated dechp into two fields, as they functioned differently; value-based
~~Separated quest reward data's job field into two fields
~~Consolidated a large number of fields into the SQL enum and set types
~~Fixed up numerous bugs in processing

3.0
===
!~Increased maximum drop integer to 100% drop = 1 million (1,000,000)
~ Modified drop rates of most items
~ Modified meso drops (all credit to Bri)
~ Fixed mob data parsing
~ Fixed mob skill data parsing
~ Fixed quest reward data parsing
~ Fixed up numerous tables and reordered some
+ Added monster card buff stuff to itemdata
+ Added flying and "friendly" mob info to mobdata
+ Added buffs and proper skill rewards to quest reward data
+ Added timemob processing to mapdata
+ Added proper banish support
+ Added reactor repeat/timeout data
+ Added real script name data for reactors, NPCs, and quests
+ Added mpp/mobcount to skilldata

2.8
===
++Added facedata, hairdata, and skindata tables
++Added dropglobaldata table
+ Added quest strings to stringdata

2.7
===
~ Modified mob skill x/y to int(11)
~ Updated shop data
++Added mapseatdata, monstercarddata, continentdata tables
+ Added itemdata.hasmapeffect
+ Added shopitemdata.quantity
+ Added mapreactordata.link
+ Added mobdata.link, mobdata.buff, mobdata.publicreward, mobdata.explosivereward
+ Added skilldata.damage

2.6
===
- Removed action column from mobskilldata, it indicates an animation, which we don't care about
- Removed elemAttr column from mobskills, it was only used for one skill
+ Added summoneffect column to mobskills
+ Added selfdestruction column to mobdata
~ Redid numerous mobskill table columns to better suit their data
~ Fixed rb/lt to ltx/lty and rbx/rby.

2.5.2
=====
+ Added maple_version column to mcdb_info

2.5.1
=====
~ Ran SQL file to fix scroll drop rates and restored horntail and NX Slime drops.

2.5
===
+ Added columns top, left, right, and bottom to mapdata. These are map boundries.
+ Added column town to mapdata, to tell whether or not a map is a town.
+ Added columns randstat and recover to itemdata. These determine whether or not a scroll gives random stats or recovers slots.
+ Added column ailment to itemdata. This determines which ailments an item cures. [curse: 1, weakness: 2, darkness: 4, seal: 8, poison: 16 - Items which cure multiples of each ailment are derived from the sum of each ailment's numbers. All cures have an ailment value of 31 since they cure them all, and holy water has an ailment value of 9 since it cures curse and seal.]
++Added tables mobskills, mobskillsummons tables.
- Removed deprecated deathdelay column from mobdata, and added undead boolean.
~ Now using .68 WZ information.

2.4
===
+ Added rechargedata and other tables/columns by Bui
+ Now using .66 WZ info

2.3
===
+ Added deathdelay to mobdata, containing the overall delay for a mob's death.
+ Added autoconsume column to itemdata after morph.
~ Adjusted some columns in mobdata to unsigned due to them never being below 0.

2.2
===
~+Golden Slime NX drops now based on auto-generated list of non Pet Equip cash items
~ Drop chances altered to better fit with GMS drop rates
~ Cleaned up a few meso drop entries
~ Renamed `dropdata.mobid` to `dropdata.dropperid`

2.1
===
!~Fixed improper portal IDs caused by some odd reordering
+ New shop data for Singapore and other areas by Bui.
+ Improved GM shop contents

2.0
===
~+Merged reactordropdata and mobdropdata tables into dropdata, and did a reorganisation of the table for clarity.
!~Drop chances are now based on 100000 as the max value for chance, rather than 10000.
++New drop database based on Monster Book information by Doyos with Golden Slime NX drops by Bri.
~~Renamed toid in mapportaldata to tomap to better reflect meanings of acryonyms and better describe the variable

1.0
===
= Initial Release of MCDB
