# Admin Commands

All admin commands start with `/chestprotect admin`.

The root permission is `chestprotect.admin.command`. Subcommands use the same pattern:
`chestprotect.admin.command.<subcommand>`.

Only give these permissions to trusted staff.

# Commands

| Command | What it does | Permission |
| --- | --- | --- |
| `/chestprotect admin` | Shows admin command help. | `chestprotect.admin.command` |
| `/chestprotect admin about` | Shows plugin information. | `chestprotect.admin.command.about` |
| `/chestprotect admin reload` | Reloads configuration and reloads `protectables.yml`. | `chestprotect.admin.command.reload` |
| `/chestprotect admin listperms <player>` | Lists ChestProtect permissions detected for a player. | `chestprotect.admin.command.listperms` |
| `/chestprotect admin import` | Imports protections from LWC. LWC must be installed and enabled. | `chestprotect.admin.command.import` |
| `/chestprotect admin player <player> menu` | Opens the ChestProtect menu for another player's data. | `chestprotect.admin.command.player.menu` |
| `/chestprotect admin player <player> delete confirm` | Deletes all ChestProtect data and protections for a player. | `chestprotect.admin.command.player.delete` |
| `/chestprotect admin player <player> give limit <limit> <amount>` | Modifies a player's stored limit value. | `chestprotect.admin.command.player.give.limit` |

# Admin Locking

`/chestprotect lock [player]` has an optional admin argument.

| Command | What it does | Permission |
| --- | --- | --- |
| `/chestprotect lock <player>` | Enters lock mode and creates the next clicked protection for another player. | `chestprotect.admin.lock` |
| `/chestprotect lock Server` | Enters lock mode and creates the next clicked protection for the server owner ID. | `chestprotect.admin.lock` |

Normal players use `/chestprotect lock` without an argument.

# Player Administration

Use `/chestprotect admin player <player> menu` when staff need to inspect or edit a player's
protections through the GUI.

Use `/chestprotect admin player <player> delete confirm` carefully. It deletes the player's
ChestProtect data and protections.

# Limit Administration

The limit command uses the same limit IDs as `player-limits.yml`:

| Limit ID | What it controls |
| --- | --- |
| `player_blocks` | Maximum block protections. |
| `player_blocks_free` | Free block protections before costs apply. |
| `player_entities` | Maximum entity protections. |
| `player_entities_free` | Free entity protections before costs apply. |
| `player_groups` | Maximum groups. |
| `protection_members` | Maximum trusted players per protection or group. |

For normal rank-based limits, prefer [Limits](../config/Limits.md). Use admin limit commands for
manual adjustments.

# Importing from LWC

`/chestprotect admin import` imports protections from LWC. Make a backup first and run the import
while LWC is installed and enabled.
