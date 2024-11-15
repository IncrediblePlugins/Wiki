To assign permissions to players you must install a permissions plugin, like [Luckperms](https://www.spigotmc.org/resources/28140). Below you find a list of permissions that you can assign to players or their permission groups. Please note that if a player has `/op`, they will have all permissions.

# Numbered Permissions
Important: 
* **Replace `<number>` with an actual number.** Example: `chestprotect.blocks.<number>` -> chestprotect.blocks.5

`chestprotect.blocks.<number>`\
How many blocks can a player protect? Replace `number` with an actual number.

`chestprotect.entities.<number>`\
How many entities can a player protect? Replace `number` with an actual number.

`chestprotect.members.<number>`\
How many trusted players can a player have per protection. Replace `number` with an actual number.

`chestprotect.groups.<number>`\
How many groups can a player create? Replace `number` with an actual number.

`chestprotect.free.blocks.<number>`\
Set the amount of free block protections. Replace `number` with an actual number.

`chestprotect.free.entities.<number>`\
Set the amount of free entity protections. Replace `number` with an actual number.

# Player Commands
See here: [Link](../players/Commands.md)

# Admin Commands
See here: [Link](../admins/Commands.md)

# Teleportation
The following permissions limit all teleportation initiated by ChestProtect. Players have them by default. However, in some cases
the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.

## Disabling Teleportation
If you want to disable a teleportation you need to unset the permission in your permissions plugin.
Example for LuckPerms: ``/luckperms group default permission set chestprotect.teleport.protection false``
The value ``false`` is important here.

## Teleportation Permissions
`chestprotect.teleport.protection`\
Allow teleportation to protections. This permission is set by default.

## Settings Permissions

      chestprotect.setting.*:
        description: Access to all protection and player settings
        default: op
        children:
          chestprotect.setting.player.*:
            description: Access to all player settings
            default: op
            children:
              chestprotect.setting.player.lock_persistent:
                description: Access to toggle lock persistent setting
                default: op
              chestprotect.setting.player.unlock_persistent:
                description: Access to toggle unlock persistent setting
                default: op
              chestprotect.setting.player.trust_persistent:
                description: Access to toggle trust persistent setting
                default: op
              chestprotect.setting.player.untrust_persistent:
                description: Access to toggle untrust persistent setting
                default: op
              chestprotect.setting.player.setrole_persistent:
                description: Access to toggle setrole persistent setting
                default: op
          chestprotect.setting.protection.*:
            description: Access to all protection settings
            default: op
            children:
              chestprotect.setting.protection.player_trust:
                description: Access to toggle role player trust setting
                default: op
              chestprotect.setting.protection.player_untrust:
                description: Access to toggle role player untrust setting
                default: op
              chestprotect.setting.protection.player_setrole:
                description: Access to toggle role player setrole setting
                default: op


# Bypass Permissions
`chestprotect.bypass.edit`\
Edit protections of other players.

`chestprotect.bypass.open`\
Open protection of other players.

`chestprotect.bypass.unlock`\
Unlock protections of other players.
