# Admin Commands

`/farm` is the short alias used on this page. `/betterfarming` is the full command.

Use `/farm admin help` in game to see the admin commands available to your account.

# Farm List

| Command | What it does | Permission |
| --- | --- | --- |
| `/farm list <player>` | Opens the placed farms list for another player. | `betterfarming.command.list` and `betterfarming.admin.command.list` |

# Admin Command Tree

All `/farm admin ...` commands require `betterfarming.admin.command` and then the subcommand permission shown below. Nested commands also require their parent command permissions, unless you grant a wildcard.

| Command | What it does | Permission |
| --- | --- | --- |
| `/farm admin help [page]` | Shows admin command help. | `betterfarming.admin.command.help` |
| `/farm admin give <player> <type> <amount> [level] [stack]` | Gives farm items to a player. `level` is the combined level index (0-based; omit it to use the type's configured entry level). `stack` optionally bundles that many farms into each item, up to the type's stacking cap. | `betterfarming.admin.command.give` |
| `/farm admin reload` | Reloads config, language, GUI, player limits, and farm configuration where reloads are supported. Restart for settings marked restart-only. | `betterfarming.admin.command.reload` |
| `/farm admin about` | Shows version, update, wiki, marketplace, license, and placeholder-parser information. | `betterfarming.admin.command.about` |
| `/farm admin listperms <player> [page]` | Lists BetterFarming permissions active for a player. Op players have every permission. | `betterfarming.admin.command.listperms` |
| `/farm admin database backup` | Creates a database backup immediately, in addition to any configured backup schedule (see [Configuration](Configuration.md)). | `betterfarming.admin.command.database` and `betterfarming.admin.command.database.backup` |
| `/farm admin database restore <backup> confirm` | Restores the database from a backup file and restarts the server. Destructive - requires confirmation. | `betterfarming.admin.command.database` and `betterfarming.admin.command.database.restore` |
| `/farm admin player <player> limits` | Shows a player's effective limits. | `betterfarming.admin.command.player` and `betterfarming.admin.command.player.limits` |
| `/farm admin player <player> give limit <limit> <amount>` | Adds or removes a command-given limit modifier for an online player. Negative amounts remove from command-given modifiers. | `betterfarming.admin.command.player`, `betterfarming.admin.command.player.give`, and `betterfarming.admin.command.player.give.limit` |

# Notes

Farms have one combined level (radius, growth interval, and storage capacity together) - see [Farm Types](../config/Farm-Types.md#levels). `/farm admin give`'s optional `[level]` argument picks that single combined level, not a per-attribute value.

There is no separate "set owner" option - `/farm admin give` always gives an item with the target player stored as its owner.
