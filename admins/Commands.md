# Admin Commands

`/upgradeablehoppers list [player]`\
View placed hoppers. Without `[player]`, this opens your own hopper list and uses the normal player permission. Providing another player requires the admin permission.\
*Permission for other players: uhoppers.admin.command.list*

`/upgradeablehoppers admin`\
View available admin subcommands.\
*Permission: uhoppers.admin.command*

`/upgradeablehoppers admin give <player> <type> <amount> [set-owner]`\
Give hopper items to a player. If `[set-owner]` is omitted or `true`, only that player can place the item while `hopper.only-owner` is enabled. If it is `false`, the item is unbound and the player who places it becomes the owner.\
*Permission: uhoppers.admin.command.give*

`/upgradeablehoppers admin reload`\
Reload reloadable configuration files. `hoppers.yml` can't be reloaded and requires a full server restart.\
*Permission: uhoppers.admin.command.reload*

`/upgradeablehoppers admin database`\
View available database admin subcommands.\
*Permission: uhoppers.admin.command.database*

`/upgradeablehoppers admin database backup`\
Create a database backup immediately, in addition to the schedule configured under `database.backup` in `config.yml`. Runs in the background and does not affect server performance. Backups are stored in `Data/Backups/` and old ones are pruned automatically down to the configured retention count.\
*Permission: uhoppers.admin.command.database.backup*

`/upgradeablehoppers admin database restore <file>`\
Restore the database from a backup created by `/upgradeablehoppers admin database backup` (or the scheduled backup task). Requires confirmation, since this overwrites the current database - the server restarts automatically once the restore finishes, since the plugin can't safely keep running against a swapped-out database. `<file>` tab-completes existing backups.\
*Permission: uhoppers.admin.command.database.restore*

`/upgradeablehoppers admin database migrate <mysql | sqlite>`\
Copy data to another database type. Configure the target database first, run the command, then enable the new database type in `config.yml` and restart the server.\
*Permission: uhoppers.admin.command.database.migrate*

`/upgradeablehoppers admin about`\
Display debug information about the plugin.\
*Permission: uhoppers.admin.command.about*

`/upgradeablehoppers admin listperms <player> [page]`\
List active permissions that the plugin detects for a player.\
*Permission: uhoppers.admin.command.listperms*

## Permission Pattern
All subcommands of `/upgradeablehoppers admin` use this permission format: `uhoppers.admin.command.<subcommand>`\
Example: `/upgradeablehoppers admin give` = `uhoppers.admin.command.give`

Subcommands nested under `/upgradeablehoppers admin database` extend the pattern one level deeper: `uhoppers.admin.command.database.<subcommand>`\
Example: `/upgradeablehoppers admin database backup` = `uhoppers.admin.command.database.backup`

## Import Command
Older plugin files may still contain references to `/upgradeablehoppers admin import` or `uhoppers.admin.command.import`.

This subcommand is not active in the current plugin code.
