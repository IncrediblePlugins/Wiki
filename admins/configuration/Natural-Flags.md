# Natural Flags

Natural flags control land behavior that is not tied to a player role, such as mob spawning, fire spread, water flow, and special admin states.

Players can toggle visible natural flags in their land menu if they have the matching `lands.setting.<flag>` permission and a role that can edit land settings. Server admins can also edit them from `/lands admin menu` for wilderness settings.

# Configuration

Natural flags are configured in `config.yml` under `chunk.land-flags`.

`default_list` sets the natural flags that are enabled for newly created lands.

`display_list` controls which natural flags appear in the player menu. Hiding a flag from this list does not remove it from the plugin. You can still set its default value in config or change it with admin commands.

Changing flag defaults in config requires a reload or restart and only affects new lands, unless you reset existing lands.

# Admin Commands

`/lands admin land <land or *> setflag <flag> <true or false> <visitor>`

Sets a role flag or natural flag in one land, or all lands with `*`.

`/lands admin land <land or *> resetflag <flag or all>`

Resets one flag or all flags back to the values from config and `roles.yml`. Admin lands are skipped when resetting all lands.

Required permissions:

| Command | Permission |
| --- | --- |
| Set a flag | `lands.admin.command.land.setflag` |
| Reset flags | `lands.admin.command.land.resetflag` |
| Open admin menu for wilderness settings | `lands.admin.command.menu` |

# Available Natural Flags

| Flag | What it controls | Toggle permission |
| --- | --- | --- |
| `ENTITY_GRIEFING` | Whether entities such as creepers can grief blocks. | `lands.setting.entity_griefing` |
| `TNT_GRIEFING` | Whether TNT can destroy blocks. | `lands.setting.tnt_griefing` |
| `PISTON_GRIEFING` | Whether pistons can push blocks into the land from outside. | `lands.setting.piston_griefing` |
| `MONSTER_SPAWN` | Whether monsters can spawn. Spawner handling depends on config. | `lands.setting.monster_spawn` |
| `PHANTOM_SPAWN` | Whether phantoms can spawn. | `lands.setting.phantom_spawn` |
| `ANIMAL_SPAWN` | Whether animals can spawn. | `lands.setting.animal_spawn` |
| `WATERFLOW_ALLOW` | Whether water can flow into or inside the land. | `lands.setting.waterflow_allow` |
| `LAVAFLOW_ALLOW` | Whether lava can flow into or inside the land. | `lands.setting.lavaflow_allow` |
| `FIRE_SPREAD` | Whether fire can spread in the land. | `lands.setting.fire_spread` |
| `LEAF_DECAY` | Whether leaves decay naturally. | `lands.setting.leaf_decay` |
| `PLANT_GROWTH` | Whether plants and trees grow. | `lands.setting.plant_growth` |
| `SNOW_MELT` | Whether snow and ice can melt. | `lands.setting.snow_melt` |
| `WITHER_ATTACK_ANIMAL` | Whether withers can damage animals. | `lands.setting.wither_attack_animal` |
| `BLOCK_SPREADING` | Whether spreading blocks, such as amethyst, can spread in the land. | `lands.setting.block_spreading` |
| `COPPER_GOLEM` | Whether copper golems from other areas can sort chests in this area. | `lands.setting.copper_golem` |

# System and Admin Natural Flags

These flags exist in source too, but they are not normal player-facing natural flags. Use them only when you intentionally expose them or manage them as an admin.

| Flag | What it controls | Toggle permission |
| --- | --- | --- |
| `TITLE_HIDE` | Hides land enter and leave title messages for the land. | `lands.setting.title_hide` |
| `REQUEST_ACCEPT` | Automatically accepts land join requests. | `lands.setting.request_accept` |
| `EXPIRATION_SHIELD` | Prevents the land from being removed by expiration. | `lands.setting.expiration_shield` |
| `PEACEFUL` | Prevents the land from taking part in wars. | `lands.setting.peaceful` |

# War Interaction

`wars.yml` has `land-flags_list`. Flags in that list are enabled for lands during war. For example, if you want TNT damage during wars, add `TNT_GRIEFING` there. If you also want players to ignite TNT, configure the matching role flag in `invading.flags.role-flags_list`.
