## Numbered Permissions
IMPORTANT: **Replace `<number>` with an actual number.** Example: `uspawners.spawners.<number>` -> uspawners.spawners.5

`uspawners.spawners.<number>`\
Description: Set amount of placeable spawners.\
Example: uspawners.spawners.5\
Unlimited: uspawners.spawners.*

## Other
`uspawners.upgrade`\
Description: Allow players with this permission to upgrade their spawners.

`uspawners.drop-item`\
Description: Drop the spawner item when players break the spawner.

`uspawners.silktouch`\
Description: Allow to mine spawners with the silktouch enchantement.\
Option `silktouch` needs to be enabled in config.

`uspawners.mob.<mob>`\
Description: Allow players to purchase mob types.
Replace `<mob>` with a mob type from entities.yml.

## Command Permissions
````
      uspawners.command.*:
        description: Permission for all player commands.
        default: op
        children:
          uspawners.command.get:
            description: /Spawners get
            default: op
          uspawners.command.list:
            description: /Spawners list
            default: op

      uspawners.admin.*:
        description: Permission for all admin commands. This does not include bypass.
        default: op
        children:
          uspawners.admin.command.give:
            description: /Spawners give
            default: op
          uspawners.admin.command.reload:
            description: /Spawners reload
            default: op
          uspawners.admin.command.admin:
            description: /Spawners admin
            default: op
          uspawners.admin.command.list:
            description: /Spawners list <player>
            default: op
````

## Teleportation
The following permissions limit all teleportation initiated by UpgradeableSpawners. Players have them by default. However, in some cases
the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.
You don't need to explicitly set them.

### Disabling Teleportation
If you want to disable a teleportation you
need to unset the permission in your permissions plugin.
Example for LuckPerms: ``/luckperms group default permission set uspawners.teleport.spawner false``
The value ``false`` is important here.

### Teleportation Permissions
`uspawners.teleport.spawner`\
Description: Allow teleportation to placed spawners via ``/uspawners list``.\
Note: This permission is set by default.



## Admin Permissions

## Bypass Permissions

      uspawners.bypass.*:
        description: Permission for all bypasses.
        default: op
        children:
          uspawners.bypass.delete:
            description: Delete other players spawners.
            default: op
          uspawners.bypass.edit:
            description: Upgrade other players spawners.
            default: op