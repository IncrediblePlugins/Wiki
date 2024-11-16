You can configure these flags inside your `config.yml` file.\
Options: 
* default_list
* display_list

Wilderness flags can be edited in the `/lands admin menu` menu.

# Reset flag(s) to their defined state from config.yml:
`/lands admin land <land | *> resetflag <flag | all>`\
Keep in mind that changing flags in the configuration files requires a server reload / restart.\
*Permission: lands.admin.command.land.resetflag*

# Flags
Each flag has a toggle permission, which is required for players to be able to toggle the flag.

* **ENTITY_GRIEFING**\
Allow entities to grief blocks?\
*Toggle permission: lands.setting.entity_griefing*

* **TNT_GRIEFING**\
Allow tnt to destroy blocks?\
*Toggle permission: lands.setting.tnt_griefing*

* **PISTON_GRIEFING**\
Allow pistons from a wilderness to push into the area?
This should be set to false, since it protects against griefing from other players.\
*Toggle permission: lands.setting.piston_griefing*

* **MONSTER_SPAWN**\
Should monsters spawn? This does not include spawners by default.
To include spawners, you need to enable the include-spawners option.\
*Toggle permission: lands.setting.monster_spawn*

* **PHANTOM_SPAWN**\
Should phantoms spawn? This does not include spawners by default.
* To include spawners, you need to enable the include-spawners option.\
*Toggle permission: lands.setting.phantom_spawn*

* **WITHER_ATTACK_ANIMAL**\
Should withers be able to damage animals? This flags gives you more control over mob farms.\
*Toggle permission: lands.setting.wither_attack_animal*

* **ANIMAL_SPAWN**\
Should animals spawn? This does not include spawners.\
*Toggle permission: lands.setting.animal_spawn*

* **WATERFLOW_ALLOW**\
Allow water to flow?
This should be set to false, since it protects against griefing from other players.\
*Toggle permission: lands.setting.waterflow_allow*

* **FIRE_SPREAD**\
Should fire spread? Fire can not spread from wilderness into lands, even without this flag being set.\
*Toggle permission: lands.setting.fire_spread*

* **LEAF_DECAY**\
Should leaves decay?\
*Toggle permission: lands.setting.leaf_decay*

* **PLANT_GROWTH**\
Should plants (including trees) grow?\
*Toggle permission: lands.setting.plant_growth*

* **SNOW_MELT**\
Should snow and ice be able to melt?\
*Toggle permission: lands.setting.snow_melt*

* **BLOCK_SPREADING**\
Should blocks, such as amethyst blocks be able to spread into an area? 
This only affects blocks that are spreading from an area that is part of the same land.
Blocks from the wilderness can never spread into claims, regardless of whether this flag is set or not.\
*Toggle permission: lands.setting.block_spreading*

# Other Land Flags
These flags might not appear in the natural flag's menu. Instead, they usually have their own menu, where they can be toggled directly.

* **TITLE_HIDE**\
Hide the land enter title?\
*Toggle permission: None*

* **REQUEST_ACCEPT**\
Automatically accept new membership requests?\
*Toggle permission: None*

# Config
Here you configure the default flags and decide which flags should be displayed in the GUI menu to players.
```yaml
  # Natural flags configuration. Role flags can be configured in the roles.yml file.
  # List of available landFlags: https://wiki.incredibleplugins.com/lands/configuration/natural-flags
  # NOTE: This option requires server reload / restart.
  land-flags:
    # Configure DEFAULT natural flags which will apply to new land creations.
    default_list:
      - monster_spawn
      - phantom_spawn
      - animal_spawn
      - leaf_decay
      - plant_growth
      - snow_melt

    # Natural flags which should be visible in the flags menu.
    display_list:
      - entity_griefing
      - tnt_griefing
      - piston_griefing
      - monster_spawn
      - phantom_spawn
      - animal_spawn
      - waterflow_allow
      - fire_spread
      - leaf_decay
      - plant_growth
      - snow_melt
```
