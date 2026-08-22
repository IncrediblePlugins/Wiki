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
| `/spawners admin give <player> <entity> [amount] [spawn_interval] [spawn_amount] [period_amount] [player_range] [nearby_entities] [set-owner]` | Gives upgradeable spawner items. Level arguments are level ids from `levels.yml`. `set-owner` decides whether the item belongs to the target player. | `uspawners.admin.command.give` |
| `/spawners list <player>` | Opens another player's placed-spawner list. | `uspawners.admin.command.list` |
| `/spawners admin player <player>` | Shows how many spawners a player has placed and lists their spawner ids. | `uspawners.admin.command.player` |
| `/spawners admin teleport <spawner-id>` | Teleports to a spawner by id. | `uspawners.admin.command.teleport` |
| `/spawners admin reload` | Reloads configuration and locale files. | `uspawners.admin.command.reload` |
| `/spawners admin about` | Shows plugin and debug information. | `uspawners.admin.command.about` |
| `/spawners admin listperms <player> [page]` | Lists the UpgradeableSpawners permissions that apply to a player. | `uspawners.admin.command.listperms` |
| `/spawners admin migratedb <mysql or sqlite>` | Copies current data to the selected database type. Configure the target database first, then restart after migration. | `uspawners.admin.command.migratedb` |
| `/spawners admin killall [confirm]` | Removes entities spawned by UpgradeableSpawners. This command is not registered on Folia. | `uspawners.admin.command.killall` |

# Giving Spawners with Levels

The level arguments use level ids from `levels.yml`, not raw values.

If you set a later level argument, also provide the previous arguments. For example, to give a pig
spawner with custom upgrade levels, include the amount first and then the upgrade level ids in this
order:

1. Spawn Interval
2. Spawn Amount
3. Spawns During Period
4. Player Distance
5. Nearby Entities

If `set-owner` is `true`, the target player is stored as the owner of the item. If your server has
owner-locked spawner placement enabled, only that owner can place the item unless the player has a
bypass permission.
