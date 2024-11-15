To assign permissions to players you must install a permissions plugin, like [Luckperms](https://www.spigotmc.org/resources/28140). Below you find a list of permissions that you can assign to players or their permission groups. Please note that if a player has `/op`, they will have all permissions.

# Player Permissions
These permissions are safe to set for players.

## Numbered Permissions
Important: 
* **Replace `<number>` with an actual number.** Example: `uspawners.spawners.<number>` -> uspawners.spawners.5

`uspawners.spawners.<number>`\
Set amount of placeable spawners. Replace `number` with an actual number.

## Other
`uspawners.upgrade`\
Allow players with this permission to upgrade their spawners.

`uspawners.drop-item`\
Drop the spawner item when players break the spawner.

`uspawners.silktouch`\
Allow to mine spawners with the silktouch enchantement. The option `silktouch` needs to be enabled in config.

`uspawners.mob.<mob>`\
Allow players to purchase mob types. Replace `<mob>` with a mob type from `entities.yml`.

## Command Permissions
See here: [Link](../players/Commands.md)

## Teleportation
The following permissions limit all teleportation initiated by UpgradeableSpawners. Players have them by default. However, in some cases
the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.

### Disabling Teleportation
If you want to disable a teleportation you
need to unset the permission in your permissions plugin.
Example for LuckPerms: ``/luckperms group default permission set uspawners.teleport.spawner false``
The value ``false`` is important here.

### Teleportation Permissions
`uspawners.teleport.spawner`\
Allow teleportation to placed spawners via ``/uspawners list``. This permission is set by default.

# Admin Permissions
These permissions should only be given to staff.

## Command Permissions
See here: [Link](../admins/Commands.md)

## Bypass Permissions
`uspawners.bypass.delete`\
Delete other players spawners.

`uspawners.bypass.edit`\
Upgrade spawners that belong to other players.
