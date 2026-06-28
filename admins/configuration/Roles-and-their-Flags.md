# Roles and Role Flags

Roles decide what players can do in lands, areas, and nations. Land owners edit these in the land menu. Server admins configure the default roles in `roles.yml`.

Role flags are split into action flags and management flags.

Action flags control gameplay actions, such as breaking blocks or opening containers.

Management flags control land management, such as trusting players, setting roles, changing taxes, or declaring war.

# Configuration

Default roles are configured in `roles.yml`.

`display` controls which role flags appear in the role menu.

Each default role has a `default` list. These flags are enabled when a new land is created. Existing lands are not changed until you reset or edit them.

Changing `roles.yml` requires a reload or restart.

# Admin Commands

| Command | What it does | Permission |
| --- | --- | --- |
| `/lands admin land <land or *> setflag <flag> <true or false> <visitor>` | Sets a role flag or natural flag in one land, or all lands with `*`. | `lands.admin.command.land.setflag` |
| `/lands admin land <land or *> resetflag <flag or all>` | Resets one flag or all flags to config defaults. | `lands.admin.command.land.resetflag` |
| `/lands admin land <land or *> addrole <role>` | Adds a custom role from `roles.yml` to one land or all lands. | `lands.admin.command.land.addrole` |

Be careful with `addrole`: player-created lands can rename roles, so running it multiple times can add duplicate roles.

# Permission Format

| Type | Format |
| --- | --- |
| Allow players to toggle a land role flag | `lands.role.setting.<flag>` |
| Bypass a land role flag in claimed land | `lands.bypass.<flag>` |
| Bypass a land role flag in protected wilderness | `lands.bypass.wilderness.<flag>` |
| Allow players to toggle a nation role flag | `nations.setting.<flag>` |
| Bypass a nation role flag | `nations.bypass.<flag>` |

`lands.bypass.priority` lets staff ignore role priority checks. Without it, a player can only manage members with a lower role priority when the action uses role priority.

# Action Flags

| Flag | What it allows | Toggle permission | Bypass permission | Wilderness bypass |
| --- | --- | --- | --- | --- |
| `BLOCK_BREAK` | Break blocks. | `lands.role.setting.block_break` | `lands.bypass.block_break` | `lands.bypass.wilderness.block_break` |
| `BLOCK_PLACE` | Place blocks. | `lands.role.setting.block_place` | `lands.bypass.block_place` | `lands.bypass.wilderness.block_place` |
| `ATTACK_PLAYER` | Attack players. | `lands.role.setting.attack_player` | `lands.bypass.attack_player` | `lands.bypass.wilderness.attack_player` |
| `ATTACK_ANIMAL` | Attack animals. | `lands.role.setting.attack_animal` | `lands.bypass.attack_animal` | `lands.bypass.wilderness.attack_animal` |
| `ATTACK_MONSTER` | Attack monsters. If disabled, monsters also cannot damage players of that role. | `lands.role.setting.attack_monster` | `lands.bypass.attack_monster` | `lands.bypass.wilderness.attack_monster` |
| `BLOCK_IGNITE` | Ignite blocks and place fire. | `lands.role.setting.block_ignite` | `lands.bypass.block_ignite` | `lands.bypass.wilderness.block_ignite` |
| `INTERACT_GENERAL` | Use interactions not covered by a more specific interaction flag. | `lands.role.setting.interact_general` | `lands.bypass.interact_general` | `lands.bypass.wilderness.interact_general` |
| `INTERACT_MECHANISM` | Use redstone, levers, pressure plates, and similar blocks. | `lands.role.setting.interact_mechanism` | `lands.bypass.interact_mechanism` | `lands.bypass.wilderness.interact_mechanism` |
| `INTERACT_CONTAINER` | Open containers such as chests. | `lands.role.setting.interact_container` | `lands.bypass.interact_container` | `lands.bypass.wilderness.interact_container` |
| `INTERACT_DOOR` | Open and close doors. | `lands.role.setting.interact_door` | `lands.bypass.interact_door` | `lands.bypass.wilderness.interact_door` |
| `INTERACT_TRAPDOOR` | Open and close trapdoors. | `lands.role.setting.interact_trapdoor` | `lands.bypass.interact_trapdoor` | `lands.bypass.wilderness.interact_trapdoor` |
| `INTERACT_VILLAGER` | Trade with villagers. | `lands.role.setting.interact_villager` | `lands.bypass.interact_villager` | `lands.bypass.wilderness.interact_villager` |
| `FLY` | Fly in the area if flight control is enabled in config. | `lands.role.setting.fly` | `lands.bypass.fly` | `lands.bypass.wilderness.fly` |
| `ELYTRA` | Use elytras in the area. | `lands.role.setting.elytra` | `lands.bypass.elytra` | `lands.bypass.wilderness.elytra` |
| `SPAWN_TELEPORT` | Teleport to the land spawn. | `lands.role.setting.spawn_teleport` | `lands.bypass.spawn_teleport` | `lands.bypass.wilderness.spawn_teleport` |
| `LAND_ENTER` | Enter the land area. | `lands.role.setting.land_enter` | `lands.bypass.land_enter` | `lands.bypass.wilderness.land_enter` |
| `VEHICLE_USE` | Place and use vehicles. | `lands.role.setting.vehicle_use` | `lands.bypass.vehicle_use` | `lands.bypass.wilderness.vehicle_use` |
| `ITEM_PICKUP` | Pick up dropped items. | `lands.role.setting.item_pickup` | `lands.bypass.item_pickup` | `lands.bypass.wilderness.item_pickup` |
| `ENDER_PEARL` | Use ender pearls. | `lands.role.setting.ender_pearl` | `lands.bypass.ender_pearl` | `lands.bypass.wilderness.ender_pearl` |
| `TRAMPLE_FARMLAND` | Trample farmland. | `lands.role.setting.trample_farmland` | `lands.bypass.trample_farmland` | `lands.bypass.wilderness.trample_farmland` |
| `HARVEST` | Harvest crops. | `lands.role.setting.harvest` | `lands.bypass.harvest` | `lands.bypass.wilderness.harvest` |
| `SHEAR` | Shear animals. | `lands.role.setting.shear` | `lands.bypass.shear` | `lands.bypass.wilderness.shear` |
| `PLANT` | Plant crops and saplings. | `lands.role.setting.plant` | `lands.bypass.plant` | `lands.bypass.wilderness.plant` |
| `WIND_BURST` | Use wind charges and maces with Wind Burst. | `lands.role.setting.wind_burst` | `lands.bypass.wind_burst` | `lands.bypass.wilderness.wind_burst` |
| `NO_DAMAGE` | Makes players with the role immune to damage. This flag targets admin use and is hidden by default. | `lands.role.setting.no_damage` | `lands.bypass.no_damage` | `lands.bypass.wilderness.no_damage` |

# Management Flags

| Flag | What it allows | Toggle permission | Bypass permission |
| --- | --- | --- | --- |
| `PLAYER_TRUST` | Trust players to the land. | `lands.role.setting.player_trust` | `lands.bypass.player_trust` |
| `PLAYER_UNTRUST` | Untrust players with a lower role priority. | `lands.role.setting.player_untrust` | `lands.bypass.player_untrust` |
| `PLAYER_SETROLE` | Change roles of players with a lower role priority. | `lands.role.setting.player_setrole` | `lands.bypass.player_setrole` |
| `LAND_CLAIM` | Claim chunks for the land. | `lands.role.setting.land_claim` | `lands.bypass.land_claim` |
| `LAND_CLAIM_BORDER` | Claim directly next to another land, ignoring the configured claim distance. | `lands.role.setting.land_claim_border` | `lands.bypass.land_claim_border` |
| `SPAWN_SET` | Set the land spawn. | `lands.role.setting.spawn_set` | `lands.bypass.spawn_set` |
| `SETTING_EDIT_LAND` | Edit natural land flags. | `lands.role.setting.setting_edit_land` | `lands.bypass.setting_edit_land` |
| `SETTING_EDIT_ROLE` | Edit role settings for roles with a lower priority. | `lands.role.setting.setting_edit_role` | `lands.bypass.setting_edit_role` |
| `SETTING_EDIT_TAXES` | Edit tax settings. Roles with this flag do not pay taxes. | `lands.role.setting.setting_edit_taxes` | `lands.bypass.setting_edit_taxes` |
| `SETTING_EDIT_VARIOUS` | Rename the land and change its title. | `lands.role.setting.setting_edit_various` | `lands.bypass.setting_edit_various` |
| `BALANCE_WITHDRAW` | Withdraw money from the land bank. | `lands.role.setting.balance_withdraw` | `lands.bypass.balance_withdraw` |
| `AREA_ASSIGN` | Create sub areas and assign selections to areas. | `lands.role.setting.area_assign` | `lands.bypass.area_assign` |
| `PLAYER_BAN` | Ban players from the land. | `lands.role.setting.player_ban` | `lands.bypass.player_ban` |
| `WAR_MANAGE` | Declare wars, manage wars, and surrender for the land. | `lands.role.setting.war_manage` | `lands.bypass.war_manage` |

# Nation Role Flag

| Flag | What it allows | Toggle permission | Bypass permission |
| --- | --- | --- | --- |
| `NATION_EDIT` | Edit nation settings. | `nations.setting.nation_edit` | `nations.bypass.nation_edit` |

The nation flag uses `nations.*` permissions because it belongs to the nation module, not normal land role settings.

# War Interaction

`wars.yml` uses role flags in `invading.flags.role-flags_list`. These flags are granted to invaders while they are fighting in enemy land.

Adding `BLOCK_BREAK` or `BLOCK_PLACE` allows all block breaking or placing during war. To allow only specific blocks, keep those flags out of the list and use `block-break_list` or `block-place_list` instead.
