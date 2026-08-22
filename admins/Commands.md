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

`/upgradeablehoppers admin migratedb <mysql | sqlite>`\
Copy data to another database type. Configure the target database first, run the command, then enable the new database type in `config.yml` and restart the server.\
*Permission: uhoppers.admin.command.migratedb*

`/upgradeablehoppers admin about`\
Display debug information about the plugin.\
*Permission: uhoppers.admin.command.about*

`/upgradeablehoppers admin listperms <player> [page]`\
List active permissions that the plugin detects for a player.\
*Permission: uhoppers.admin.command.listperms*

## Permission Pattern
All subcommands of `/upgradeablehoppers admin` use this permission format: `uhoppers.admin.command.<subcommand>`\
Example: `/upgradeablehoppers admin give` = `uhoppers.admin.command.give`

## Import Command
Older plugin files may still contain references to `/upgradeablehoppers admin import` or `uhoppers.admin.command.import`.

This subcommand is not active in the current plugin code.
