To assign permissions to players you must install a permissions plugin, like [Luckperms](https://www.spigotmc.org/resources/28140). Below you find a list of permissions that you can assign to players or their permission groups. Please note that if a player has `/op`, they will have all permissions.

# Player Permissions
These permissions are safe to set for your players.

## Numbered Permissions
**Replace `<number>` with a number and `<farmtype>` with the configuration key of a farm type (`farms.yml` file).**\
Example:
````yaml
crop:
  enabled: true
````
Results in `betterfarming.crop.10`. Whereas `10` represents the maximum farms of this farm type.

`betterfarming.total.<number>`\
How many farms should the player be able to create in total? Below, you can control individual farm type limits. Both permissions need to be set in order to create any farm. Replace `number` with an actual number.

`betterfarming.<farmtype>.<number>`\
How many crop farms should the player be able to create? Replace `number` with an actual number.\
Example: `betterfarming.crop.5`, `betterfarming.tree.5`, `betterfarming.ore.5`

`betterfarming.roles.<number>`\
How many player roles should the player be able to create per farm? Replace `number` with an actual number.

`betterfarming.members.<number>`\
How many players should the farm owner be able to trust at the farm? Replace `number` with an actual number.

## General Permissions
`betterfarming.upgrade`\
Only allow players with this permission to upgrade any farm, if config option `upgrade-perm` enabled.

## Command Permissions
See here: [Link](../players/Commands.md)

## Teleportation
The following permissions limit all teleportation initiated by BetterFarming. Players have them by default. However, in some cases
the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.

### Disabling Teleportation
If you want to disable a teleportation you
need to unset the permission in your permissions plugin.
Example for LuckPerms: ``/luckperms group default permission set betterfarming.teleport.farm false``
The value ``false`` is important here.

### Teleportation Permissions
`betterfarming.teleport.farm`\
Allow teleportation to placed farms. This permission is set by default.

# Admin Permissions
These permissions should only be given to staff or server admins.

## Commands
See here: [Link](../admins/Commands.md)

## Flag Toggle & Bypass Permissions
Bypass protections and do stuff for other farms: [Link](../config/Role-Flags.md)

## Admin Flags
See here: [Link](../admins/Flags.md)

