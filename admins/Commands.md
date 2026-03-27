# Lands Admin Commands

`/lands admin`\
Allows you do execute a variety of actions for lands and so on.\
*Permission: lands.admin.command*

`/lands wild <world> <player> <skip-cooldown>`\
Teleport to a random location. The parameters are only available to server admins and allow you to execute the command via the console for specific players.\
*Permission: lands.admin.command.wild*

## Permissions for Admin Commands
All subcommands of `/lands admin` will have this permission format: `lands.admin.command.<subcommand>`\
Examples:
* `/lands admin migratedb` = lands.admin.command.migratedb
* `/lands admin land <land> menu` = lands.admin.command.land.menu

# Wars Admin Commands
`/wars admin`\
Allows you do execute a variety of actions for lands and so on.\
*Permission: wars.admin.command*

## Permissions for Admin Commands
All subcommands of `/wars admin` will have this permission format: `lands.admin.command.<subcommand>`\
Example: `/wars admin start` - wars.admin.command.start