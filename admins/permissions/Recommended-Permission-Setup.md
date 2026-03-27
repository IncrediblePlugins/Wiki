This page is a list of recommended permissions for players on your server. Please note that this is a general recommendation and might not reflect your server's needs. Also, most features of Lands can be disabled. Therefore, this recommendation might include permissions that are not required for your setup. For managing permissions, you can use a permission plugin like [LuckPerms](https://www.spigotmc.org/resources/luckperms.28140/).

# Looking for max Chunks etc.?
Limits such as max lands, chunks etc. are now edited in the ``player-limits.yml`` file. Read more [here](https://wiki.incredibleplugins.com/general/locale-and-config/limits).

# Command Permissions

* `lands.command.*`\
Description: That gives players access to all player related commands.
If you want to remove some commands, you either need to negate the specific command permission or you need to set each command permission specifically.\
_View all permissions: [Link](../../players/basics/Commands.md)_

* `nations.command.*`\
Description: Use all player related `/nations <cmd>` commands.\
_View all permissions: [Link](https://wiki.incredibleplugins.com/lands/players/basics/commands#nations)_

* `wars.command.*`\
Description: Allow players to use all player related `/wars <cmd>` commands.\
_View all permissions: [Link](https://wiki.incredibleplugins.com/lands/players/basics/commands#wars)_

# Teleportation
`lands.teleport.*`\
Description: This allows players to teleport to individual claimed chunks of their land etc. This does not include spawn teleportation, as this is covered by `lands.command.spawn`. If you want to limit teleportation, you'll need to set permissions accordingly.

_View all permissions: [Link](https://wiki.incredibleplugins.com/lands/permissions/permissions#teleportation)_

# Toggle Role Flags
`lands.role.setting.*`\
Description: This allows players to toggle all role flags for their land.

_View all permissions: [Link](https://wiki.incredibleplugins.com/lands/configuration/roles-and-their-flags#flags)_

# Toggle Natural Flags
`lands.setting.*`\
Description: This allows players to toggle all natural flags (like monster spawning etc.) for their land.

_View all permissions: [Link](https://wiki.incredibleplugins.com/lands/configuration/natural-flags#flags)_


# Toggle Personal Flags
`lands.player.setting.*`\
Description: Allow players to toggle all their personal flags.

_View all permissions: [Link](https://wiki.incredibleplugins.com/lands/configuration/player-personal-settings#available-personal-flags)_


# List of recommended Permissions for regular Players
This list isn't meant to be a standard. Each server is different. This is just an example. 

## Command Permissions
* lands.command.*
* wars.command.*
* nations.command.*
## Teleportation
* lands.teleport.*
## Toggle Flags
* lands.setting.*
* lands.role.setting.*
* lands.player.setting.*
