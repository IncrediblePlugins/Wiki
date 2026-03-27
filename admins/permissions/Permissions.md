To assign permissions to players you must install a permissions plugin, like [Luckperms](https://www.spigotmc.org/resources/28140). Below you find a list of permissions that you can assign to players or their permission groups. Please note that if a player has `/op`, they will have all permissions.

# Recommended Permission Setup
You can find a recommended permission setup for players here: [Recommended Permission Setup](https://wiki.incredibleplugins.com/lands/permissions/recommended-permission-setup)

# Looking for max Chunks etc.?
Limits such as max lands, chunks etc. are now edited in the ``player-limits.yml`` file. Read more [here](https://wiki.incredibleplugins.com/general/locale-and-config/limits).

# Player Permissions
These permissions are safe to set for your players.

## Command Permissions
[Commands wiki page](players/Commands.md)

## Teleportation
The following permissions limit all teleportation initiated by Lands. Players have them by default. However, in some cases the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.

### Disabling Teleportation
If you want to disable a teleportation you need to unset the permission in your permissions plugin.
Example for LuckPerms: `/luckperms group default permission set lands.teleport.sub_area false`\
The value `false` is important here.

### Teleportation Permissions
`lands.teleport.chunk`\
Allow teleportation to claimed chunks via `/lands claimlist`. This permission is set by default.

`lands.teleport.rentables`\
Allow teleportation to rentable areas or lands setup for purchase. This permission is set by default.

`lands.teleport.land_spawn`\
Allow to teleport to a land spawn. This permission is set by default.

`lands.teleport.random_teleport`\
Allow to random teleport via `/lands wild`. This permission is set by default.

`lands.teleport.war`\
Allow to teleport to war spawn via `/wars spawn`. This permission is set by default.

`lands.teleport.sub_area`\
Allow to teleport to a sub area. This permission is set by default.

`lands.teleport.unstuck`\
Allow to teleport via `/lands unstuck`. This permission is set by default.

## Toggle Natural Flags
Permissions for toggleing natural flags can be found [here](../configuration/Natural-Flags.md).

## Toggle Role Flags
Permissions for toggleing role flags can be found [here](../configuration/Roles-and-their-Flags.md).

## Toggle Personal Flags
Permissions for toggleing personal flags can be found [here](../configuration/Player-Personal-Settings.md).

# Staff Permissions
These permissions should only be set for your staff.

## Admin Commands
See [here](../Commands.md).

## Bypass Permissions
These permissions allow you to edit other players lands etc.

### Action Bypass
Bypass land protections such as block break, entering etc.: [here](../configuration/Roles-and-their-Flags.md#action-flags)

### Selection
`lands.bypass.selection`\
Bypass other plugins, such as WorldGuard, cancelling a selection creation.

### Teleport Cooldowns
`lands.bypass.cooldown.wild`\
Bypass the `/lands wild` cooldown.

`lands.bypass.cooldown.rename`\
Bypass the `/lands rename` cooldown.

`lands.bypass.cooldown.teleport`\
Bypass the chunk teleport cooldown via `/lands claimlist`.

`lands.bypass.cooldown.spawn`\
Bypass the `/lands spawn` cooldown.

`lands.bypass.cooldown.unstuck`\
Bypass the `/lands unstuck` cooldown.

### War
`lands.bypass.war.trust`\
Allow trusting other players during war.

`lands.bypass.war.claim`\
Allow claiming during war.

### Options
`lands.bypass.option.force-near`\
Bypass the `force-near` option from `config.yml`.

### Command Blacklist
`lands.bypass.cmd.untrusted.*`\
Bypass blacklisted commands for untrusted players from `config.yml`. Use `lands.bypass.cmd.untrusted.<command>` while replacing `<command>` with a command to bypass the restriction for a specific command.

`lands.bypass.cmd.general.*`\
Bypass blacklisted commands for untrusted **and trusted** players from `config.yml`. Use `lands.bypass.cmd.general.<command>` while replacing `<command>` with a command to bypass the restriction for a specific command.

### Expiration
`lands.bypass.expiration`\
Bypass land expiration. This only works, if you use LuckPerms for your permission management.

### Teleportation
`lands.bypass.teleport.delay`\
Bypass the wait time before teleportation.

`lands.bypass.teleport.cmd`\
Execute commands while waiting for the teleportation to start.

## Admin & Moderator Utilities
See [here](../Tools.md).
