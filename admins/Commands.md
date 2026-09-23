# Admin Commands

Admin commands are for server staff.

The examples on this page use `/spawners`. Depending on your server configuration, the same
commands may also be available through aliases such as `/spawner`, `/uspawners`, or
`/upgradeablespawners`.

All `/spawners admin` subcommands use this permission format:

`uspawners.admin.command.<subcommand>`

Example: `/spawners admin give` uses `uspawners.admin.command.give`.

# Commands

| Command | What it does | Permission |
| --- | --- | --- |
| `/spawners admin` | Shows admin command help. | `uspawners.admin.command` |
| `/spawners admin give <player> <entity> [amount] [level] [set-owner]` | Gives upgradeable spawner items. `level` is a level id from `spawners.yml` (defaults to `1`). `set-owner` decides whether the item belongs to the target player (defaults to `true`). | `uspawners.admin.command.give` |
| `/spawners list <player>` | Opens another player's placed-spawner list. | `uspawners.admin.command.list` |
| `/spawners admin player <player>` | Shows how many spawners a player has placed and lists their spawner ids. | `uspawners.admin.command.player` |
| `/spawners admin teleport <spawner-id>` | Teleports to a spawner by id. | `uspawners.admin.command.teleport` |
| `/spawners admin reload` | Reloads configuration and locale files. | `uspawners.admin.command.reload` |
| `/spawners admin about` | Shows plugin and debug information. | `uspawners.admin.command.about` |
| `/spawners admin listperms <player> [page]` | Lists the UpgradeableSpawners permissions that apply to a player. | `uspawners.admin.command.listperms` |
| `/spawners admin migratedb <mysql or sqlite>` | Copies current data to the selected database type. Configure the target database first, then restart after migration. | `uspawners.admin.command.migratedb` |
| `/spawners admin killall [confirm]` | Removes entities spawned by UpgradeableSpawners. This command is not registered on Folia. | `uspawners.admin.command.killall` |

# Giving Spawners with Levels

`level` is a single combined level id from `spawners.yml`'s `types.spawner.levels` section, not a
raw stat value — a spawner has one combined level, not a separate level per stat. See
[Levels](../config/Levels.md).

To set `level`, also provide `amount` (it comes first). For example, to give one pig spawner at
level `3`: `/spawners admin give <player> PIG 1 3`.

If `set-owner` is `true`, the target player is stored as the owner of the item. If your server has
owner-locked spawner placement enabled, only that owner can place the item unless the player has a
bypass permission.
