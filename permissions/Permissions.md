To assign permissions to players you must install a permissions plugin, like [Luckperms](https://www.spigotmc.org/resources/28140). Below you find a list of permissions that you can assign to players or their permission groups. Please note that if a player has `/op`, they will have all permissions.

# Player Permissions
These permissions are safe to set for your players.

## Numbered Permissions
Important:
* **Replace `<number>` with an actual number.** Example: `fasterfurnaces.furnaces.<number>` -> fasterfurnaces.furnaces.5

`fasterfurnaces.furnaces.<number>`\
Allow players to place a specific amount of furnaces. Replace `number` with an actual number.

## Command Permissions
Commands wiki page: https://github.com/Angeschossen/FasterFurnaces/wiki/Commands

## Teleportation
The following permissions limit all teleportation initiated by FasterFurnaces. Players have them by default. However, in some cases
the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.

### Disabling Teleportation
If you want to disable a teleportation you
need to unset the permission in your permissions plugin.
Example for LuckPerms: ``/luckperms group default permission set fasterfurnaces.teleport.furnace false``
The value ``false`` is important here.

### Teleportation Permissions
`fasterfurnaces.teleport.furnace`\
Allow teleportation placed furnaces. This permission is set by default.

# Admin Permissions
These permissions should only be given to staff or server admins.

## Admin Commands
See here: [Link](../admins/Commands.md)