# Permissions

Use a permissions plugin such as [LuckPerms](https://www.spigotmc.org/resources/28140) to assign permissions. Op players have all permissions.

# Player Permissions

These permissions are usually safe for normal players.

| Permission | What it does |
| --- | --- |
| `betterfarming.command.get` | Allows `/farm get`. |
| `betterfarming.command.list` | Allows `/farm list` for the player's own farms. |
| `betterfarming.command.help` | Allows `/farm help`. |
| `betterfarming.command.confirmtp` | Allows `/farm confirmtp` after an unsafe teleport warning. |
| `betterfarming.teleport.farm` | Allows teleporting to placed farms from the farm list. This permission is set by default. |
| `betterfarming.upgrade` | Allows farm upgrades if `farm.upgrade-perm` is enabled in `config.yml`. |

If you want to disable farm teleports, explicitly set the teleport permission to `false`.

Example:

`/luckperms group default permission set betterfarming.teleport.farm false`

# Admin Command Permissions

Admin commands use `betterfarming.admin.command` plus the subcommand path.

Examples:

| Permission | What it does |
| --- | --- |
| `betterfarming.admin.command` | Allows access to the `/farm admin` command tree. |
| `betterfarming.admin.command.give` | Allows `/farm admin give`. |
| `betterfarming.admin.command.reload` | Allows `/farm admin reload`. |
| `betterfarming.admin.command.about` | Allows `/farm admin about`. |
| `betterfarming.admin.command.listperms` | Allows `/farm admin listperms`. |
| `betterfarming.admin.command.migratedb` | Allows `/farm admin migratedb`. |
| `betterfarming.admin.command.player` | Allows the `/farm admin player <player> ...` command branch. |
| `betterfarming.admin.command.player.limits` | Allows viewing a player's BetterFarming limits. Also requires `betterfarming.admin.command.player`. |
| `betterfarming.admin.command.player.give` | Allows the `/farm admin player <player> give ...` command branch. |
| `betterfarming.admin.command.player.give.limit` | Allows modifying a player's command-given limits. Also requires the parent `player` and `player.give` permissions. |
| `betterfarming.admin.command.list` | Allows viewing another player's farms with `/farm list <player>`. |

Use `betterfarming.admin.command.*` for all admin subcommands.

# Role Setting Permissions

These permissions allow changing role-flag defaults where the role settings UI or framework exposes them.

| Permission | Flag |
| --- | --- |
| `betterfarming.role.setting.block_break` | `BLOCK_BREAK` |
| `betterfarming.role.setting.block_place` | `BLOCK_PLACE` |
| `betterfarming.role.setting.harvest` | `HARVEST` |
| `betterfarming.role.setting.plant` | `PLANT` |
| `betterfarming.role.setting.interact` | `INTERACT` |
| `betterfarming.role.setting.upgrade` | `UPGRADE` |
| `betterfarming.role.setting.player_trust` | `PLAYER_TRUST` |
| `betterfarming.role.setting.player_untrust` | `PLAYER_UNTRUST` |
| `betterfarming.role.setting.player_setrole` | `PLAYER_SETROLE` |
| `betterfarming.role.setting.delete` | `DELETE` |
| `betterfarming.role.setting.configure` | `CONFIGURE` |

See [Roles and Role Flags](../config/Role-Flags.md) for what each flag controls.

# Bypass Permissions

Bypass permissions should only be given to trusted staff.

| Permission | What it bypasses |
| --- | --- |
| `betterfarming.bypass.block_break` | Block break protection inside farms. Current non-harvestable block placement checks use this flag too. |
| `betterfarming.bypass.block_place` | Registered block placement bypass. Current placement checks use `plant` for harvestable blocks and `block_break` for other blocks. |
| `betterfarming.bypass.harvest` | Harvest protection. |
| `betterfarming.bypass.plant` | Planting protection. |
| `betterfarming.bypass.interact` | Interaction protection. |
| `betterfarming.bypass.upgrade` | Farm upgrade role checks. |
| `betterfarming.bypass.player_trust` | Trust-player role checks. |
| `betterfarming.bypass.player_untrust` | Untrust-player role checks. |
| `betterfarming.bypass.player_setrole` | Set-role checks. |
| `betterfarming.bypass.delete` | Farm deletion checks. |
| `betterfarming.bypass.configure` | Farm configuration checks. |
| `betterfarming.bypass.manage_players` | Managing farm players even when not trusted. |
| `betterfarming.bypass.edit` | Opening other players' farm menus and bypassing role priority. |
| `betterfarming.bypass.only-land` | The Lands-only placement requirement. |

# Admin Flags

| Permission | What it does |
| --- | --- |
| `betterfarming.admin.flag.auto_replant` | Shows and allows toggling the admin-only `AUTO_REPLANT` farm flag. |

Use `betterfarming.admin.*` for all admin command and admin flag permissions.
