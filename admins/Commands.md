# Admin Commands

Admin commands are for server staff. Do not give these permissions to regular players.

Most `/lands admin` subcommands use this permission format:

`lands.admin.command.<subcommand>`

Nested commands add the full path:

`/lands admin land <land> resetflag` uses `lands.admin.command.land.resetflag`.

`/lands admin player <player> delete` uses `lands.admin.command.player.delete`.

# Lands Admin Commands

| Command | What it does | Permission |
| --- | --- | --- |
| `/lands admin menu` | Opens the admin menu. | `lands.admin.command.menu` |
| `/lands admin reload` | Reloads Lands config, roles, levels, events, and player data cache. | `lands.admin.command.reload` |
| `/lands admin deleteinactive` | Runs the configured expiration actions for inactive players and lands. | `lands.admin.command.deleteinactive` |
| `/lands admin limits` | Opens limit pack tools. | `lands.admin.command.limits` |
| `/lands admin limits refresh` | Refreshes player limit packs. | `lands.admin.command.limits.refresh` |
| `/lands admin limits migrate confirm` | Migrates old numbered limit permissions to `player-limits.yml`. | `lands.admin.command.limits.migrate` |
| `/lands admin player <player> limits` | Shows all limits that apply to a player. | `lands.admin.command.player.limits` |
| `/lands admin player <player> menu` | Opens the menu view of a player. | `lands.admin.command.player.menu` |
| `/lands admin player <player> delete confirm` | Deletes stored Lands data for a player. | `lands.admin.command.player.delete` |
| `/lands admin migratedb <database> confirm` | Migrates Lands data to another database type. | `lands.admin.command.migratedb` |
| `/lands admin land <land or *> limits` | Shows limits for a land. | `lands.admin.command.land.limits` |
| `/lands admin land <land> menu` | Opens the menu of a land. | `lands.admin.command.land.menu` |
| `/lands admin land <land or *> addrole <role> confirm` | Adds a custom role from `roles.yml` to one land or all lands. | `lands.admin.command.land.addrole` |
| `/lands admin land <land or *> setflag <flag> <state> <visitor>` | Sets a role flag or natural flag in one land or all lands. | `lands.admin.command.land.setflag` |
| `/lands admin land <land or *> resetflag <flag or all>` | Resets one flag or all flags to config defaults. | `lands.admin.command.land.resetflag` |
| `/lands admin land <land or *> removespawn` | Removes the spawn of one land or all lands. | `lands.admin.command.land.removespawn` |
| `/lands admin land <land or *> shield set <time>` | Sets the war shield time. | `lands.admin.command.land.shield.set` |
| `/lands admin land <land or *> shield modify <time>` | Adds or removes war shield time. | `lands.admin.command.land.shield.modify` |
| `/lands admin land <land or *> bank set <amount>` | Sets the land bank balance. | `lands.admin.command.land.bank.set` |
| `/lands admin land <land or *> bank modify <amount>` | Adds or removes land bank balance. | `lands.admin.command.land.bank.modify` |
| `/lands admin resetworld <world> confirm` | Deletes all claims and land spawns in a world. | `lands.admin.command.resetworld` |
| `/lands admin dismiss` | Dismisses new-flag notices. | `lands.admin.command.dismiss` |
| `/lands admin chatspy [land or nation or *]` | Toggles chat spy for one land, one nation, all lands and nations, or disables it with no argument. | `lands.admin.command.chatspy` |
| `/lands admin debug` | Prints debug information. | `lands.admin.command.debug` |
| `/lands admin debug tasks` | Prints task debug information. | `lands.admin.command.debug.tasks` |
| `/lands admin import <plugin>` | Imports claims from a supported claim plugin. | `lands.admin.command.import` |
| `/lands admin hologram create <context> <sorting>` | Creates a leaderboard hologram at your location. | `lands.admin.command.hologram.create` |
| `/lands admin hologram list` | Lists leaderboard holograms. | `lands.admin.command.hologram.list` |
| `/lands admin hologram delete` | Deletes a nearby leaderboard hologram. | `lands.admin.command.hologram.delete` |
| `/lands admin player <player> give claimblock <radius> <amount> [silent]` | Gives claim block items. | `lands.admin.command.give.claimblock` |
| `/lands admin player <player> give camp <radius> <amount> [silent]` | Gives camp items. | `lands.admin.command.give.camp` |
| `/lands admin player <player> give captureflag <amount> [silent]` | Gives war capture flag items. | `lands.admin.command.give.captureflag` |
| `/lands admin player <player> give first-join-items` | Gives all enabled first-join items. | `lands.admin.command.give.first-join-items` |
| `/lands admin koth create` | Creates a KoTH arena in the sub area you are standing in. Only exists when KoTH support is enabled. | `lands.admin.command.koth.create` |
| `/lands admin listperms <player>` | Lists permissions detected for a player. | `lands.admin.command.listperms` |

`<land or *>` means that `*` applies the command to all lands where the command supports it.

# Other Staff Commands

| Command | What it does | Permission |
| --- | --- | --- |
| `/lands edit <land>` | Selects another land for admin editing. | `lands.admin.command.edit` |
| `/lands menu <player>` | Opens another player's Lands menu. | `lands.admin.command.menu` |
| `/lands wild <world> <player> [skip-cooldown]` | Random-teleports another player. | `lands.admin.command.wild` |
| `/lands spawn <land or none> <area or none> <player> <wait>` | Teleports another player to a land or area spawn. | `lands.admin.command.edit` |

# Wars Admin Commands

`/wars admin` uses this permission format:

`wars.admin.command.<subcommand>`

| Command | What it does | Permission |
| --- | --- | --- |
| `/wars admin start <attacker> <defender> <tribute> <preparation_time>` | Forcefully declares or starts a war. | `wars.admin.command.start` |
| `/wars admin end <land or nation>` | Ends an upcoming or active war without winner rewards. | `wars.admin.command.end` |

# Related Permissions

Admin commands are only one part of staff access. See [Permissions](permissions/Permissions.md) for bypass permissions, flag permissions, teleport permissions, and non-command admin permissions.
