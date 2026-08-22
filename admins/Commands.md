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
| `/farm admin give <player> <type> <amount> [set-owner] [interval-level] [storage-level] [radius-level]` | Gives farm items to a player. `set-owner` defaults to `true`; level numbers are 1-based. | `betterfarming.admin.command.give` |
| `/farm admin reload` | Reloads config, language, GUI, player limits, and farm configuration where reloads are supported. Restart for settings marked restart-only. | `betterfarming.admin.command.reload` |
| `/farm admin about` | Shows version, update, wiki, marketplace, license, and placeholder-parser information. | `betterfarming.admin.command.about` |
| `/farm admin listperms <player> [page]` | Lists BetterFarming permissions active for a player. Op players have every permission. | `betterfarming.admin.command.listperms` |
| `/farm admin migratedb <mysql|sqlite>` | Copies data to the selected database type. After it completes, enable the target database type in `config.yml` and restart. | `betterfarming.admin.command.migratedb` |
| `/farm admin player <player> limits` | Shows a player's effective limits. | `betterfarming.admin.command.player` and `betterfarming.admin.command.player.limits` |
| `/farm admin player <player> give limit <limit> <amount>` | Adds or removes a command-given limit modifier for an online player. Negative amounts remove from command-given modifiers. | `betterfarming.admin.command.player`, `betterfarming.admin.command.player.give`, and `betterfarming.admin.command.player.give.limit` |

# Notes

The optional farm-item level arguments for `/farm admin give` are ordered as interval, storage, and radius.

`set-owner` defaults to `true`. If you set it to `false`, the farm item has no stored owner and can be placed by another player even when `farm.creation.only-owner` is enabled.

Use `/farm admin migratedb` only after making a database backup.
