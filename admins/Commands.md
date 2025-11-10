`/spawners admin`\
Allows you to execute a variety of actions.\
_Permission: uspawners.admin.command_

`/spawners admin give <player> <entity> <amount> <level: spawn_interval> <level: spawn_amount> <level: period_amount> <level: player_range> <level: nearby_entities> <set owner>`
The levels are the levels from the levels.yml file. The last argument "set owner" defines if you want to mark the player as the owner of the spawner item.
Depending on your config you can prevent other players from placing the spawner item, if they're not the owner.
_Permission: uspawners.admin.command.give_

## Permissions for Admin Commands
All subcommands of `/spawners admin` will have this permission format: `uspawners.admin.command.<subcommand>`\
Example: `/uspawners admin give -> `uspawners.admin.command.give`
